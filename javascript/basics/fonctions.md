## Les fonctions

Une fonction est une boite dans laquelle on va stocker des variables. Ci-dessous un exemple avec des valeurs de retour `return`.

````
const number1 = 5;
const number2 = 3;

function addition (param1, param2) {
  return param1 + param2;
}

function soustraction (param1, param2) {
  return param1 - param2;
}

const result = addition(number1, number2);
const result2 = soustraction(number1, number2);

console.log(result);
console.log(result2);
````
Il y a deux façons de définir une fonction :

### Fonction classique

````
function testFunction(a, b) {
return a + b;
}
console.log(testFunction(2, 3));
````

### Arrow functions

````
const testFunction2 = (a, b) => {
return a + b
};
console.log(testFunction2(2, 3));
````

On peut également l'écrire comme ceci :

````
const testFunctions2 = (a, b) => a + b;
````

### Rest parameters

Si on veut utilier une fonction avec de nombreux arguments :

````
function add(...args) {
    console.log(args);
    return args;
}
add(2, 3, 4, 5);
````

La fonction renvoie un tableau `[2, 3, 4, 5]`

Si on veut une fonction qui aditionne plusieurs paramètres :

````
function add(...args) {
    console.log(args);
    return args.reduce((acc, value) => acc + value, 0);
}
add(2, 3, 4, 5);
````

La fonction renvoie 14.

Autres exemples : 

````
function maFonction(a, b, ...plusDArguments) {
  console.log("a", a);
  console.log("b", b);
  console.log("plusDArguments", plusDArguments);
}

maFonction("un", "deux", "trois", "quatre", "cinq");
// affichera ceci dans la console :
// a, "un"
// b, "deux"
// plusDArguments, ["trois", "quatre", "cinq"]
````

Si le dernier paramètre nommé fourni à la fonction est préfixé de ... (trois points), il devient un tableau.
