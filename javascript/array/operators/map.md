:arrow_forward: [linkOperators](../link/linkOperators.md)


# Map :

map() crée un nouveau tableau avec les résultats de l'appel d'une fonction fournie sur chaque élément du tableau appelant.
:anger: il y a toujours un `return` dans map() . 

#### Syntaxe : :leftwards_arrow_with_hook:

`var nouveauTableau = arr.map(callback [, thisArg])` c'est une fonction callback.

##### Demo: Array.map() : :speech_balloon:

````js
const array1 = [1, 4, 9, 16];

const map1 = array1.map(x => x * 2);

console.log(map1);
````
