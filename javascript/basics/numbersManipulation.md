# Manipulation des nombres

Manipuler des chiffres à virgule est complexe en Javascript.
Les outils mathématiques s'utilisent avec la librairie math.

## Math.round

La fonction Math.round() retourne la valeur d'un nombre arrondi à l'entier le plus proche.

````
console.log(Math.round(10.9));
````

La console va renvoyer 11. A partir de 10.5, la fonction renvoie le nombre au dessus.

## Math.floor

La fonction Math.floor(x) renvoie le plus grand entier qui est inférieur ou égal à un nombre.

````
console.log(Math.floor(10.5);
````

La console va renvoyer 10. Il va garder que ce qu'il y a avant la virgule.

## toFixed

La méthode toFixed() permet de formater un nombre en notation à point-fixe.

````
console.log(10.66668787878.toFixed(2));
````

La console va renvoyer 10.67. Le 2 après toFixed indique le nombre de virgule voulue.
`Le problème c'est qu'il renvoit un string et non un nombre.`

## parseInt et parseFloat

`La fonction parseFloat()` permet de transformer une chaîne de caractères en un nombre flottant après avoir analysée celle-ci (parsing).

````
console.log(parseFloat('10.67') + 10);
````
La console va renvoyer 20.67.

On peut l'utiliser avec la méthode toFixed : 

````
console.log(parseFloat(10.6777.toFixed(2)) + 10);
````

La console va renvoyer 20.68.

`La fonction parseInt()` analyse une chaîne de caractère fournie en argument et renvoie un entier exprimé dans une base donnée.

