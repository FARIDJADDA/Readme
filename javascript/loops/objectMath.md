- [Math.round()](#mathround-)

# Bibliothéque Math :

_les outils mathématiques s'utilise à partir d'une bibliothéque que l'on appel Math._

### Math.round() :

La fonction Math.round() retourne la valeur d'un nombre arrondi à l'entier le plus proche.

### Demo: Math.round() :

````js
console.log(Math.round(0.9));
// expected output: 1

console.log(Math.round(5.95), Math.round(5.5), Math.round(5.05));
// expected output: 6 6 5

console.log(Math.round(-5.05), Math.round(-5.5), Math.round(-5.95));
// expected output: -5 -5 -6
````

### Syntaxe :

    Math.round(x)
    
# Math.floor(x) :

_La fonction Math.floor(x) renvoie le plus grand entier qui est inférieur ou égal à un nombre x._

### Demo: Math.floor() :

````js
console.log(Math.floor(5.95));
// expected output: 5

console.log(Math.floor(5.05));
// expected output: 5

console.log(Math.floor(5));
// expected output: 5

console.log(Math.floor(-5.05));
// expected output: -6
````
    
### Syntaxe

    Math.floor(x)

# toFixed :

_La méthode toFixed() permet de formater un nombre en notation à point-fixe._

### Demo: Number.toFixed() :

````js
function financial(x) {
  return Number.parseFloat(x).toFixed(2);
}

console.log(financial(123.456));
// expected output: "123.46"

console.log(financial(0.004));
// expected output: "0.00"

console.log(financial('1.23e+5'));
// expected output: "123000.00"
````


### Syntaxe

    numObj.toFixed([nbChiffres])

:bangbang: <strong><em> Attention ! En raison du standard IEEE 754 qui est utilisé par JavaScript pour représenter les nombres, tous les nombres décimaux ne sont pas représentés exactement en JavaScript, ce qui peut mener à des résultats inattendus (comme 0.1 + 0.2 === 0.3 qui renvoie false).</strong></em>

# parseFloat() :

_La fonction parseFloat() permet de transformer une chaîne de caractères en un nombre flottant après avoir analysée celle-ci (parsing)._
 
### Demo: Standard built-in objects - parseFloat() :

````js
function circumference(r) {
  return parseFloat(r) * 2.0 * Math.PI;
}

console.log(circumference(4.567));
// expected output: 28.695307297889173

console.log(circumference('4.567abcdefgh'));
// expected output: 28.695307297889173

console.log(circumference('abcdefgh'));
// expected output: NaN
````

### Syntaxe

    parseFloat(string)
    
### Paramètres

#### string

_Une chaîne de caractères la valeur qu'on souhaite analyser et transformer en un nombre flottant._

### Valeur de retour

Un nombre flottant obtenu à partir de l'analyse de la chaîne de caractères. Si le premier caractère ne permet pas d'obtenir un nombre, ce sera la valeur NaN qui sera renvoyée.

# Math.random() :

_La fonction Math.random() renvoie un nombre flottant pseudo-aléatoire compris dans l'intervalle [0, 1[ (ce qui signifie que 0 est compris dans l'intervalle mais que 1 en est exclu) selon une distribution approximativement uniforme sur cet intervalle. Ce nombre peut ensuite être multiplié afin de couvrir un autre intervalle. La graine (seed) du générateur est choisie par l'algorithme et ne peut pas être choisie ou réinitialisée par l'utilisateur._

### Demo: Math.random() :

````js
function getRandomInt(max) {
  return Math.floor(Math.random() * Math.floor(max));
}

console.log(getRandomInt(3));
// expected output: 0, 1 or 2

console.log(getRandomInt(1));
// expected output: 0

console.log(Math.random());
// expected output: a number between 0 and 1
````

# Valeur de retour

_Un nombre flottant pseudo-aléatoire, généré entre 0 (inclus) et 1 (exclu)_


  
