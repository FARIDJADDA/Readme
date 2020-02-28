# Affecter par décomposition :

_L'affectation par décomposition (destructuring en anglais) est une expression JavaScript qui permet d'extraire (unpack en anglais) des données d'un tableau ou d'un objet grâce à une syntaxe dont la forme ressemble à la structure du tableau ou de l'objet._

# Demo: Expressions - Destructuring assignment : :pencil2:

````js
let a, b, rest;
[a, b] = [10, 20];

console.log(a);
// expected output: 10

console.log(b);
// expected output: 20

[a, b, ...rest] = [10, 20, 30, 40, 50];

console.log(rest);
// expected output: Array [30,40,50]
````

# Syntaxe :

````js
var a, b, rest;
[a, b] = [10, 20];
console.log(a); // 10
console.log(b); // 20

[a, b, ...rest] = [10, 20, 30, 40, 50];
console.log(a); // 10
console.log(b); // 20
console.log(rest); // [30, 40, 50]

({a, b} = {a: 10, b: 20});
console.log(a); // 10
console.log(b); // 20

// Proposition de syntaxe (niveau 4)
({a, b, ...rest} = {a: 10, b: 20, c: 30, d: 40});
console.log(a); // 10
console.log(b); // 20
console.log(rest); // {c: 30, d: 40}
````

:pencil2: **Note** : {a, b} = {a:1, b:2} n'est pas syntaxiquement valide en tant que tel, en effet {a, b} est ici considéré comme un bloc et non comme un objet littéral.

Cependant, ({a, b} = {a:1, b:2}) sera valide comme pour la forme var {a, b} = {a:1, b:2}.




