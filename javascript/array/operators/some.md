# .some() :

_some() teste si au moins un élément du tableau passe le test implémenté par la fonction fournie. Elle renvoie un booléen indiquant le résultat du test._

#### Demo: Array.some() : :speech_balloon:

````js
const array = [1, 2, 3, 4, 5];

const even = (element) => element % 2 === 0;

console.log(array.some(even));
// expected output: true
````

##### Syntaxe :

      arr.some(callback[, objetThis])
      
callback :leftwards_arrow_with_hook:
_La fonction à tester pour chaque élément du tableau._