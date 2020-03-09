# Rest parameters :
_Cette syntaxe permet de représenter un nombre indéfini d'arguments sous forme d'un tableau._

# Demo: Functions Rest Parameters :

````js
function sum(...theArgs) {
  return theArgs.reduce((previous, current) => {
    return previous + current;
  });
}

console.log(sum(1, 2, 3));
// expected output: 6

console.log(sum(1, 2, 3, 4));
// expected output: 10
````

### Syntaxe :

````js
function f(a, b, ...lesArguments) {
  // ...
}
````

### Description :

Si le dernier paramètre nommé fourni à la fonction est préfixé de ... (trois points), il devient un tableau dont les éléments entre 0 (inclus) et lesArguments.length (exclus) sont fournis comme autres arguments à la fonction.

````js
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
