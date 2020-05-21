# Node Js

## Architecture client/server

Le serveur envoie les données aux clients.

## Les ports

Un port est une ligne de connexion que le serveur va établir avec le client pour lui renvoyer des données.
Sur un serveur il y a 65 535 ports. Certains sont innaccessibles pour les developpeurs.
On ne peut avoir qu'un seul serveur node Js par port. `En cas d'utilisation de deux servers, il faut changer les ports utilisés ou arrêter le premier serveur.`

Avoir deux fois le serveur "tryHard" :

Le serveur node lit le code Js et dès qu'il voit un changement il reéxecute le code à l'aide de Webpack.
Pour ouvrir un second fichier tryHard, il faut aller dans le fichier webpack.config, et changer le numéro du port.

## Mettre en place Node Js

1) Cloner le repos promo3-node
2) Installer node dans le dossier serveur et saisir dans la console : cd server puis npm i,
ou Aller dans package json et cliquer sur npm install.
3) Saisir npm install -g concurrently
4) Aller dans package.json, show npm script et cliquer sur watch (à faire une fois, on aura plus qu'à ouvrir le serve la prochaine fois)
5) Cliquer sur Serve (ca va lancer le watcheur et le serveur)

On a donc le serveur (serveur.ts), le fichier node Js sera dans le dossier lib

## Méthodes de requete HTTP

*Protocole* : Façon d'envoyer des 0 et des 1 (de stocker des données).
Git est un protocole, Http également.
On peut réaliser des actions dans ces protocoles : afficher, supprimer etc

Les navigateurs ne savent faire que des get (afficher), pour remédier à ce problème on va utiliser Postman.
Postman va nous aider à utiliser toutes les méthodes en plus de Get.

### GET 

Il permet de demander au navigateur d'afficher quelque chose.

> exemples :

````javascript
app.get('/api/users', (req, res) => {
    return res.send(users);
});
````

*PS* : Pour afficher un nombre il faut le mettre dans un objet.

### POST

Il permet de créer quelque chose de nouveau

> exemples :

````javascript
app.post('/api/users',
    (req, res) => {
        const newUser = req.body;
        const id = users.length + 1;
        users.push({...newUser, id});
        return res.send(users);
    });
````
Sur postman il faut aller dans body/row et ajouter du json pour envoyer des objets.
Ps : Il faut mettre des double quotes au éléments sur json.
Ne pas oublier d'importer le bodyparser dans le tableau pour utiliser req.body.

````javascript
import bodyParser from 'body-parser';

app.use(bodyParser({}));
````

### PUT

Il permet de remplacer tous les éléments d'une chose par une autre

> exemples :

````javascript
app.put('/api/users/:id',
    (req, res) => {
        const newUser = req.body;
        const id = parseInt(req.params.id);
        const index = users
            .findIndex((user) => user.id === id);
        users[index] = {...newUser, id};
        return res.send(users);
    });
````

Comme pour post on créer l'objet qu'on veut remplacer dans le body sur postman.

### PATCH

Il permet de remplacer une partie d'un objet

> exemples :

````javascript
app.patch('/api/users/:id',
    (req, res) => {
        const newUser = req.body;
        const id = parseInt(req.params.id);
        const index = users
            .findIndex((user) => user.id === id);
        users[index] = {...users[index], ...newUser};
        return res.send(users);
    });
````

### DELETE

Il permet de supprimer un ou plusieurs éléments

> exemples :

````javascript
app.delete('/api/users/:id',
    (req, res) => {
        const id = parseInt(req.params.id);
        users = users.filter((user) => user.id !== id);
        return res.send(users);
    });
````


API : une API est un lien entre deux machines. Il s'agit des règles de communication entre deux machines.
