# Les enums

Pour gérer des cas incompatibles (une chambre louer et libre en meme temps).

Une enum est une interface qui permet de changer l'état d'un élément.

````
export enum RoomState {
    isAvailable = 'est libre',
    isCleaning = 'en nettoyage',
    isOccupied = 'occupé',
    isClosed = 'en travaux',
}

const room = RoomModel = {
    id: 1,
    roomName: 'toto',
    size: 12,
    roomState: RoomState.isAvailable,
};

console.log(room);
````

## Set et Get

Modifier (set) un joueur :

````
function checkPlayersState(state: any) {
    return Object.keys(PlayerState).some((playerState) => playerState === state);
}
export async function setPlayerState(id: string, state: PlayerState): Promise<string> {
    if (!id) {
        throw new Error('id is missing');
    }
    if (!checkPlayersState(state)) {
        throw new Error('state is invalid');
    }
    const refPlayer: DocumentReference = await refPlayers.doc(id);
    const snapPlayer: DocumentSnapshot = await refPlayer.get();
    if (!snapPlayer.exists) {
        throw new Error('player does not exists');
    }
    await refPlayer.update({playerState: state});
    return 'ok';
}

// On modifie uniquement l'état de la room :

app.patch('/api/players/:id/state', async (req, res) => {
    try {
        const id: string = req.params.id;
        const state: PlayerState = req.body.playerState;
        const result: string = await setPlayerState(id, state);
        return res.send(result);
    } catch (e) {
        return res.status(500).send(e.message);
    }
});

````

Faire un get d'un joueur :

````
export async function getPlayerState(id: string): Promise<PlayerState> {
    const player: PlayerModel = await getPlayerById(id);
    return player.playerState;
}


app.get('/api/players/:id/state', async (req, res) => {
    try {
        const id: string = req.params.id;
        const state: PlayerState = await getPlayerState(id);
        return res.send({state});
    } catch (e) {
        return res.status(500).send(e.message);
    }
});
````

