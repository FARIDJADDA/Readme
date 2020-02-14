:paperclip: [linkOperators](../link/linkOperators.md)


# filter :

`filter()` crée et retourne un nouveau tableau contenant tous les éléments du tableau d'origine qui remplissent une condition déterminée par la fonction callback.

#### Demo: Array.filter() : :speech_balloon:

````js
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(word => word.length > 6);

console.log(result);
````

## Valeur de retour :leftwards_arrow_with_hook:

_Un nouveau tableau contenant les éléments qui respectent la condition du filtre. </br>
Si aucun élément ne respecte la condition, </br>
c'est un tableau vide qui est renvoyé._