# slice() :
 
_slice() renvoie un objet tableau, </br>
contenant une copie superficielle (shallow copy) d'une portion du tableau d'origine, </br> 
la portion est définie par un indice de début et un indice de fin (exclus). </br>
Le tableau original ne sera pas modifié._

#### Demo: Array.slice() :

````js
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2));

console.log(animals.slice(2, 4));

console.log(animals.slice(1, 5));
````

###### Syntaxe :

        arr.slice()
        arr.slice(début)
        arr.slice(début, fin)

