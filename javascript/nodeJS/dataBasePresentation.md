# Connecter l'appli Node à une base de données

1) S'assurer que firebase est bien installé (firebase --version)
2) Aller sur le site de Firebase et créer un nouveau projet
3) Désactiver google analytics
4) Aller sur Database
5) Cliquer sur "Créer une base de données"
6) Choisir "démarrer en mode de production"
7) Choisir europe3
8) Aller dans le terminal, s'assurer d'être dans server et saisir firebase init.
9) Choisir firestore
10) Use an existing project
11) Choisir le projet
12) Appuyer sur entrer lors de la question sur les rules
13) Saisir entrer encore une fois
14) De nouveaux fichiers sont apparus dans server (à ajouter sur git)
15) Sur firebase, créer une collection
16) Chemin : /hotels
17) l'Id doit être généré automatiquement
18) Remplir les champs : champs : name, type : string, valeur: hotel rose;
19) Créer une nouvelle collection rooms et faire pareil en ajoutant deux rooms

## Initialiser la base de données dans le projet

1) Aller sur firebase et accéder à la console
2) Accéder à la documentation
3) Aller dans get started for admin
4) Aller dans cloud firestore, puis get started
5) Copier npm install firebase-admin --save
6) Coller en s'assurant d'être dans server sinon saisir cd server dans le terminal
7) S'assurer que tout a été installé dans package.json

## Se connecter à firebase admin

1) Aller sur server.ts
2) Faire un import `import admin from 'firebase-admin'`;
3) Copier et coller le code pour initialiser en google cloud :
````
admin.initializeApp({
    credential: admin.credential.applicationDefault()
});
````
4) Créer la base de donnée et la référence pour avoir accès à la BDD (la BDD étant sur firebase)
````
const db = admin.firestore();

const ref = db.collection('hotels');
````
5) Maintenant qu'on a accès à la référence on va rajouter le mot clef `async` (quand on doit récuperer des données sur le server firebase) :
````
app.get('/api/hostels', async (req, res) => {
    try {
        const hotels = await ref.get();
        return res.send(hotels);
    } catch (e) {
return res.status(500).send({error: 'erreur serveur :' + e.message});
    }
});
````
On met await pour dire qu'on attends le résultat (pas partout) et async quand on a des choses à chercher dans une BDD externe
En cliquant sur ctrl + get on aura une documentation.

## Fournir les credential pour que cela fonctionne

1) Sur firebase, cliquer sur la roue en haut à gauche, puis sur paramètres du projet
2) Aller dans compte de service
3) Selectionner SDK admin firebase
4) Générer une nouvelle clé privée
5) Récupérer le fichier téléchargé, le copier et le coller dans un nouveau dossier appelé cred qu'on va créer dans server
6) Créer un nouveau fichier dans cred qu'on va appelé cert.ts
7) Dans ce fichier on va saisir :
````
export const cert = {
//Copier ici ce qu'il y a dans le fichier télécharger
````
Enlever toutes les quotes pour en faire un objet classique javascript.
On a maintenant récupérer la clé.

## Lier le certificat créee avec l'admin initializeApp

1) Retourner sur firebase dans compte de service, sdk admin firebase
2) Copier le code Node js et le mettre à la place de la fonction admin.initializeApp sur server.ts
````
admin.initializeApp({
  credential: admin.credential.cert(serviceAccount),
  databaseURL: 'https://wr-node-promo3.firebaseio.com'
});
````
3) le serviceAccount ne fonctionne pas, cliquer sur ctrl + cert
4) On remarque qu'il faut saisir un string dans cert ou un objet
5) Cliquer sur ctrl + service account, on constate qu'il y a un objet avec 3 éléments dans l'interface
6) Retourner sur le cert qu'on a créee, et on le transforme pour ne garder que ce qu'il y a dans l'objet(on oublie pas de dire que cert est de type service account)
7) Importer service account from firebase-admin
8) Retirer tout ce qu'il n'y a pas dans l'objet pour qu'il corresponde à l'objet serviceAccount
9) Remplacer serviceAccount dans server.ts par cert
10) Faire l'import de cert from cred pour qu'il soit reconnu
11) Aller dans la collection hotels, et copier l'uID et on le colle dans la ref :
`const ref = db.collection('hotels').doc('FWJT67Dh8DHfzdj')`

## Sur hostels.service 

Il faut saisir ce code tout en haut de la page pour faire le crud :

````
import admin from "firebase-admin";
import {cert} from "../cred/cert";
import DocumentReference = FirebaseFirestore.DocumentReference;
import DocumentData = FirebaseFirestore.DocumentData;

admin.initializeApp({
    credential: admin.credential.cert(cert),
    databaseURL: 'https://wr-node-promo3.firebaseio.com'
});

const db = admin.firestore();

const refHotels = db.collection('hotels');
````

### GET

````
export async function getAllHostels(): Promise<HotelModel[]> {
    const hotelsQuerySnap: QuerySnapshot = await refHotels.get();
    const hotels: HotelModel[] = [];
    hotelsQuerySnap.forEach(hotelSnap => hotels.push(hotelSnap.data() as HotelModel));
    return hotels;
}

app.get('/api/hostels', async (req, res) => {
    try {
        const hostels = await getAllHostels();
        return res.send(hostels);
    } catch (e) {
        return res.status(500).send({error: 'erreur serveur :' + e.message});
    }
});
````

On ne peut faire qu'un forEach lorsqu'il s'agit d'un querySnapshot.

### POST

````
export async function postNewHostel(newHostel: HotelModel): Promise<HotelModel> {
    if (!newHostel) {
        throw new Error(`new hostel must be filled`);
    }
    const addResult: DocumentReference<DocumentData> = await refHotels.add(newHostel);
    return {...newHostel, id: addResult.id};
}

app.post('/api/hostels', async (req, res) => {
    try {
        const newHostel = req.body;
        const addResult = await postNewHostel(newHostel);
        return res.send(addResult);
    } catch (e) {
        return res.status(500).send({error: 'erreur serveur :' + e.message});
    }
});
````

### DELETE

````
export async function deleteHotelById(hostelId: string) {
    if (!hostelId) {
        throw new Error('hotel id is missing');
    }
    const hotelref: DocumentReference = refHotels.doc(hostelId);
    const snapHostelToDelete: DocumentSnapshot = await hotelref.get();
    const hostelToDelete: HotelModel | undefined = snapHostelToDelete.data() as HotelModel;
    if (!hostelToDelete) {
     throw  new Error(`${hostelId} does not exists`);
    }
    await refHotels.doc(hostelId).delete();
    return `${hostelId} => delete ok`
}

app.delete('/api/hostels/:id', async (req, res) => {
    try {
        const id = req.params.id;
        const writeResult: WriteResult = await deleteHotelById(id);
        return res.send(writeResult);
    } catch (e) {
        return res.status(500).send({error: 'erreur serveur :' + e.message});
    }
});
````

### PUT

````
export async function putHostel(hostelId: string, newHostel: HotelModel): Promise<HotelModel> {
    if (!newHostel || !hostelId) {
        throw new Error(`hostel data and hostel id must be filled`);
    }
    const hostelToPutRef: DocumentReference = await testIfHostelExistsById(hostelId);
    await hostelToPutRef.set(newHostel);
    return newHostel;
}

app.put('/api/hostels/:id', async (req, res) => {
    try {
        const id = req.params.id;
        const hotel = await putHostel(id, req.body);
        return res.send(hotel);
    } catch (e) {
        return res.status(500).send({error: 'erreur serveur :' + e.message});
    }
});
````

### PATCH

````
export async function updateHostel(hostelId: string, newHostel: HotelModel): Promise<HotelModel> {
    if (!newHostel || !hostelId) {
        throw new Error(`hostel data and hostel id must be filled`);
    }
    const hostelToPutRef: DocumentReference = await testIfHostelExistsById(hostelId);
    await hostelToPutRef.update(newHostel);
    return newHostel;
}

app.patch('/api/hostels/:id', async (req, res) => {
    try {
        const id = req.params.id;
        const hotel = await updateHostel(id, req.body);
        return res.send(hotel);
    } catch (e) {
        return res.status(500).send({error: 'erreur serveur :' + e.message});
    }
});
````

Pour la fonction test : doc => get => data

## Les sous collections

Créer une sous collection à l'interieur de hotels, puis mettre une reference de la room (ref et UID) de la table rooms.

## Créer une chambre dans un hôtel

Nous allons créee une chambre dans la table rooms qui sera lié à un hôtel en particulier.

````
app.post('/api/hostels/:hotelId/rooms/', async (req, res) => {
    try {
        const hotelId: string = req.params.hotelId;
        const newRoom: RoomModel = req.body;
        const result: string = await createRoom(hotelId, newRoom);
        return res.send(result);
    } catch (e) {
        return res.status(500).send(e.message);
    }
});

// Dans le fichier rooms.services :

const db = admin.firestore();
const hotelsRef: CollectionReference = db.collection('hotels');
const roomsRef: CollectionReference = db.collection('rooms');

export async function createRoom(hotelId: string, newRoom: RoomModel): Promise<string> {
  if (!hotelId || !newRoom) {
      throw new Error('hotelId or newRoom are missing');
  }
    const hotelRef: DocumentReference = hotelsRef.doc(hotelId);
    const hotelSnap: DocumentSnapshot = await hotelRef.get();
    if (!hotelSnap.exists) {
        throw new Error(('hotel does not exists'));
    }
    const createdRoomRef: DocumentReference = await roomsRef.add(newRoom);
    const createdRoomInHostelRef: DocumentReference = hotelRef
        .collection('rooms')
        .doc(createdRoomRef.id);
    await createdRoomInHostelRef.set({ref: createdRoomRef, uid: createdRoomRef.id});
    return 'ok';
}
````

## Promise.all

La méthode Promise.all() renvoie une promesse (Promise) qui est résolue lorsque l'ensemble des promesses contenues dans l'itérable passé en argument ont été résolues ou qui échoue avec la raison de la première promesse qui échoue au sein de l'itérable.

````
const db = admin.firestore();
const hotelsRef: CollectionReference = db.collection('hotels');
const roomsRef: CollectionReference = db.collection('rooms');

export async function getRoomById(roomId: string): Promise<RoomModel> {
    if (!roomId) {
        throw  new Error('roomId is missing');
    }
    const roomRef: DocumentReference = roomsRef.doc(roomId);
    const roomSnap: DocumentSnapshot = await roomRef.get();
    if (!roomSnap.exists) {
        throw new Error(`room ${roomId} does not exists`);
    }
    return roomSnap.data() as RoomModel;
}

export async function getAllRoomsBiUids(roomsUids: string[]) {
    const promisesToResolve: Promise<RoomModel>[] = roomsUids
        .map(uid => getRoomById(uid));
    return await Promise.all(promisesToResolve);
}

app.get('/api/test', async (req, res) => {
    try {
        const rooms = await getAllRoomsBiUids([
            'Ocvwf178CZytPRihjlZg',
            'SlbXNOc5q7zFGmUmY4KK',
            'XOr3fUQVOm07qGPArwCl'
        ]);
        return res.send(rooms);
    } catch (e) {
        return res.status(500).send(e.message);
    }
````
Cela nous renvoie un tableau avec les trois chambres :
````
[
    {
        "size": 5,
        "roomName": "chambre de hamza"
    },
    {
        "size": 4,
        "roomName": "suite pacifique"
    },
    {
        "roomName": "suite mer du nord",
        "size": 4
    }
]
````

### GET

````
export async function getPlayerById(playerId: string): Promise<PlayerModel> {
    if (!playerId) {
        throw new Error('player Id is required');
    }
    const playerRef: DocumentReference = refPlayers.doc(playerId);
    const playerSnap: DocumentSnapshot = await playerRef.get();
    if (!playerSnap.exists) {
        throw new Error('player does not exists')
    }
    return playerSnap.data() as PlayerModel;
}

export async function getAllPlayersByUids(playerUids: string[]) {
    const promisesToResolve: Promise<PlayerModel>[] = playerUids
        .map(uid => getPlayerById(uid));
    return await Promise.all(promisesToResolve);
}

export async function getTeamById(id: string): Promise<TeamModel> {
    if (!id) {
        throw new Error('id is missing');
    }
    const teamRef = await refteams.doc(id);
    const snapTeam = await teamRef.get();
    if (!snapTeam) {
        throw new Error('team does not exists');
    }
    return snapTeam.data() as TeamModel;
}
export async function getTeamWidthPlayers(id: string): Promise<TeamModel> {
    const teamToFind: TeamModel = await getTeamById(id);
    const players: CollectionReference = refteams
        .doc(id)
        .collection('players');
    const playersSnap: QuerySnapshot = await players.get();
    const teamsWidthPlayers: string[] = [];
    playersSnap.forEach(player => teamsWidthPlayers.push(player.data().uid));
    teamToFind.playersData = await getAllPlayersByUids(teamsWidthPlayers);
    return teamToFind;
}
````

### POST

````
app.post('/api/teams/:id', async (req, res) => {
    try {
        const id = req.params.id;
        const newPlayer = req.body;
        const playerToPost = await postNewPlayer(id, newPlayer);
        return res.send(playerToPost);
    } catch (e) {
        return res.status(500).send(e.message);
    }
});

export async function postNewPlayer(id: string, newPlayer: PlayerModel): Promise<PlayerModel> {
    if (!id || !newPlayer) {
        throw new Error('id or player are missing');
    }
    const teamRef = await refTeams.doc(id);
    const teamSnap = await teamRef.get();
    if (!teamSnap.exists) {
    throw new Error('team does not exists');
    }
    const createdPlayerRef = await refPlayers.add(newPlayer);
    const createdPlayerInTeamRef = teamRef
        .collection('players')
        .doc(createdPlayerRef.id);
    await createdPlayerInTeamRef.set({ref: createdPlayerRef, uid: createdPlayerRef.id});
    return newPlayer;
}
````

### DElETE

````
app.delete('/api/teams/:id/players/:playerId', async (req, res) => {
   try {
       const id = req.params.id;
       const playerId = req.params.playerId;
       const playerToDelete = await deletePlayer(id, playerId);
       return res.send(playerToDelete);
   } catch (e) {
       return res.status(500).send(e.message);
   }
});


export async function deletePlayer(id: string, playerId: string): Promise<string> {
    if (!id || playerId) {
        throw new Error('team id and player id are required');
    }
    const teamRef = await refTeams.doc(id);
    const snapTeam = await teamRef.get();
    if (!snapTeam.exists) {
        throw new Error('team does not exists');
    }
    const playerInTeamRef: DocumentReference = teamRef.collection('players').doc(playerId);
    const playerSnap: DocumentSnapshot = await playerInTeamRef.get();
    if (!playerSnap.exists) {
        throw new Error('player does not exists')
    }
    await refPlayers.doc(playerId).delete();
    await refTeams
        .doc(id)
        .collection('players').doc(playerId).delete();
    return 'player deleted';
}
````

### PUT

````
app.put('/api/players/:id', async (req, res) => {
   try {
    const id = req.params.id;
    const newPlayer = req.body;
    const playerToPut = await putPlayer(id, newPlayer);
    return res.send(playerToPut);
   } catch (e) {
       return res.status(500).send(e.message);
   }
});

async function testIfPlayerExistById(playerId: string): Promise<DocumentReference> {
    const playerRef = refPlayers.doc(playerId);
    const snapPlayerToCheck: DocumentSnapshot = await playerRef.get();
    const playerToCheck: DocumentData | undefined = snapPlayerToCheck.data() as PlayerModel | undefined;
    if (!playerToCheck) {
        throw new Error(`player: ${playerId} does not exist`)
    }
    return playerRef;
}
export async function putPlayer(id: string, newPlayer: PlayerModel): Promise<PlayerModel> {
    if (!newPlayer || !id) {
        throw new Error(`team data and team id must be filled`);
    }
    const teamToPutRef: DocumentReference = await testIfPlayerExistById(id);
    await teamToPutRef.set(newPlayer);
    return newPlayer;
}
````

### PATCH

````
app.patch('/api/players/:id', async (req, res) => {
    try {
        const id = req.params.id;
        const newPlayer = req.body;
        const playerToPatch = await patchPlayer(id, newPlayer);
        return res.send(playerToPatch);
    } catch (e) {
        return res.status(500).send(e.message);
    }
});

export async function patchPlayer(id: string, newPlayer: PlayerModel): Promise<PlayerModel> {
    if (!newPlayer || !id) {
        throw new Error(`team data and team id must be filled`);
    }
    const teamToPutRef: DocumentReference = await testIfPlayerExistById(id);
    await teamToPutRef.update(newPlayer);
    return newPlayer;
}
````
