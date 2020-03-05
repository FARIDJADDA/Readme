# Méthodes de requête HTTP

_HTTP définit un ensemble de méthodes de requête qui indiquent l'action que l'on souhaite réaliser sur la ressource indiquée. Bien qu'on rencontre également des noms (en anglais), ces méthodes sont souvent appelées verbes HTTP. Chacun d'eux implémente une sémantique différente mais certaines fonctionnalités courantes peuvent être partagées par différentes méthodes (e.g. une méthode de requête peut être sûre (safe), idempotente ou être mise en cache (cacheable))._

# Le CRUD :

_CRUD est un sigle informatique qui se définit en anglais par Create Read Update et Delete qui respectivement signifie en français Créer, Lire, Mettre à jour et Supprimer. Les CRUD nous permettent une manipulation basique des données d’une base de données, ainsi donc nous pourrons enregistrer des données, lire des données,
modifier des données et supprimer des données à partir d’une base de données._

# Les verbes utilisés pour le CRUDE :

### GET
La méthode GET demande une représentation de la ressource spécifiée. Les requêtes GET doivent uniquement être utilisées afin de récupérer des données.

````js
app.get('/api/hostels/:id/rooms',
    (req, res) => {
 const x = parseInt(req.params);
    return res.send();
    }
````

### POST
La méthode POST est utilisée pour envoyer une entité vers la ressource indiquée. Cela  entraîne généralement un changement d'état ou des effets de bord sur le serveur.

````js
app.post('/api/hostels/:id/rooms',
    (req, res) => {
  const x = req.body;
        return res.send();
    }
````

### PUT
La méthode PUT remplace toutes les représentations actuelles de la ressource visée par le contenu de la requête.

````js
app.put('/api/hostels/:id/rooms',
    (req, res) => {
  const x = req.body;
        return res.send(hostels);
    }
````

### DELETE
La méthode DELETE supprime la ressource indiquée.

````js
app.delete('/api/hostels/:id/rooms',
    (req, res) => {
 const x = parseInt(req.params);
    return res.send();
    }
````

### PATCH
La méthode PATCH est utilisée pour appliquer des modifications partielles à une ressource.

````js
app.patch('/api/hostels/:id/rooms',
    (req, res) => {
  const x = req.body;
        return res.send();
    }
````
