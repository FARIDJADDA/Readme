# React router

Récupérer les paramètres qu'il y a dans router

La page2 affiche les données d'un utilisateur :

````
export default function page2() {
    let {id} = useParams();
    return <h1>Page 2: {id}</h1>
}
````

use params va aller dans user et recuperer les paramètres
Pour que ca marche il faut aller dans app.js, et ajouter :id à la route en question.
