# Map :

map() crée un nouveau tableau avec les résultats de l'appel d'une fonction fournie sur chaque élément du tableau appelant.

#### Syntaxe :

`var nouveauTableau = arr.map(callback [, thisArg])` c'est une fonction callback.

##### Demo: Array.map() :

````js

const array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map(x => x * 2);

console.log(map1);

````