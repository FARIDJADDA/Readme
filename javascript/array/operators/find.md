# find() : 

find() renvoie la valeur du premier élément trouvé dans le tableau qui respecte la condition donnée par la fonction de test passée en argument. Sinon, la valeur undefined est renvoyée.

#### Demo: Array.find() : :speech_balloon:

````js
const array1 = [5, 12, 8, 130, 44];

const found = array1.find(element => element > 10);

console.log(found);
// expected output: 12
````

##### Syntaxe : :leftwards_arrow_with_hook:

      arr.find(callback(element[, index[, tableau]])[, thisArg])
  
