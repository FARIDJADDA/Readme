# reduce() :

_reduce() applique une fonction qui est un « accumulateur » et qui traite chaque valeur d'une liste (de la gauche vers la droite) afin de la réduire à une seule valeur._

#### Demo: Array.reduce() :

````js
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;

// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));

// 5 + 1 + 2 + 3 + 4
console.log(array1.reduce(reducer, 5));
````

##### Syntaxe :

      arr.reduce(callback)
      arr.reduce(callback, valeurInitiale)
      
_C'est une fonction callback_

  
