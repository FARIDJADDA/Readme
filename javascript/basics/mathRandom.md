# Math Random

Il renvoit un nombre aléatoire compris entre 0 et 1 (le 1 n'est pas compris).

````javascript
console.log(Math.random());
````

La console va renvoyer 0.06123456743.  À partir de ce nombre on va pouvoir fabriquer des nombres aléatoires.

````
console.log(Math.random() * 1000 + 1);
````

La console va renvoyer 859.196424784. Il envoit un nombre compris entre 1 et 1000 (1000 non compris).
Pour retirer les chiffres après la virgule :

````
console.log(Math.floor(Math.random() * 1000 + 1));
````
La console va renvoyer un nombre aléatoire entre 1 et 1000.

`Math.random` va donc nous permettre d'utiliser des générateurs aléatoires'

## Créer un nombre aléatoire entre 2 nombres

````
function createRandomNumber(min, max) {
    return Math.floor(min + Math.random() * (max - min) + 1);
}
console.log(createRandomNumber(10,15);
````
La console va renvoyer un nombre aléatoire entre 10 et 15.
