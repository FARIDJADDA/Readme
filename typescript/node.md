# Méthodes de requête HTTP

_HTTP définit un ensemble de méthodes de requête qui indiquent l'action que l'on souhaite réaliser sur la ressource indiquée. Bien qu'on rencontre également des noms (en anglais), ces méthodes sont souvent appelées verbes HTTP. Chacun d'eux implémente une sémantique différente mais certaines fonctionnalités courantes peuvent être partagées par différentes méthodes (e.g. une méthode de requête peut être sûre (safe), idempotente ou être mise en cache (cacheable))._

### GET
La méthode GET demande une représentation de la ressource spécifiée. Les requêtes GET doivent uniquement être utilisées afin de récupérer des données.

````js
app.get('/api/hostels/:id/rooms',
    (req, res) => {
    }
````

### POST
La méthode POST est utilisée pour envoyer une entité vers la ressource indiquée. Cela  entraîne généralement un changement d'état ou des effets de bord sur le serveur.

````js
app.post('/api/hostels/:id/rooms',
    (req, res) => {
    }
````

### PUT
La méthode PUT remplace toutes les représentations actuelles de la ressource visée par le contenu de la requête.

````js
app.put('/api/hostels/:id/rooms',
    (req, res) => {
    }
````

### DELETE
La méthode DELETE supprime la ressource indiquée.

````js
app.delete('/api/hostels/:id/rooms',
    (req, res) => {
    }
````

### PATCH
La méthode PATCH est utilisée pour appliquer des modifications partielles à une ressource.

````js
app.patch('/api/hostels/:id/rooms',
    (req, res) => {
    }
````
