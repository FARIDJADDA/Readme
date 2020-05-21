# Créer des paramètres query à une route qu'on a créer

Il s'agit de renvoyer quelque chose avec des conditions. On ne fait des query que pour les GET.

````
app.get('/api/testquery', async (req, res) => {
   try {
       const limit = req.query.limit;
       const toto = req.query.toto;
       return res.send({limit, toto});
   } catch (e) {
       return res.status(500).send(e.message);
   }
});

// Sur le navigateur on saisit : localhost:3015/api/testquery?limit=44&toto=45
// le navigateur renvoie {'limit': '44', 'toto': '45'}
````
On utilise : 
* `?` pour spécifier des paramètres supplémentaires
* `&` pour 'et'

## Query database 

Utiliser les query dans la database

````
app.get('/api/testquery', async (req, res) => {
   try {
       const roomNumbers = parseInt(req.query.roomNumbers);
const result = await getHostelByRoomNumbers(roomNumbers);
       return res.send({result});
   } catch (e) {
       return res.status(500).send(e.message);
   }
});

// Sur le navigateur on saisit : localhost:3015/api/testquery?roomNumbers=5

export async function getHostelByRoomNumbers(roomNumbers: number): Promise<HotelModel[]> {
    if (!roomNumbers) {
        throw new Error('roomNumbers required');
    }
    const data = await refHotels.where('roomNumbers', '==', roomNumbers).get();
    const result: HotelModel[] = [];
    data.forEach(doc => result.push(doc.data() as HotelModel));
    return result;
}
````
where : Permet de chercher dans roomNumbers toutes les rooms qui ont la valeur roomNumbers égal à roomNumbers
