:arrow_forward: [linkOperators](../link/linkOperators.md)

# Every :

 every() _permet de tester si tous les éléments d'un tableau vérifient une condition donnée par une fonction en argument. Cette méthode renvoie un booléen pour le résultat du test._
 
#### Demo: every() :

````js
const isBelowThreshold = (currentValue) => currentValue < 40;

const array1 = [1, 30, 39, 29, 10, 13];

console.log(array1.every(isBelowThreshold));
````

#### Syntaxe :

    arr.every(callback[, thisArg])
    
## Valeur de retour :

true si la fonction de rappel obtient une valeur équivalente à vrai (truthy) pour chaque élément du tableau et false sinon.


