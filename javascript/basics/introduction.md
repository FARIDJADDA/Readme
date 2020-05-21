# Introduction à Javascript

## Lier un fichier javascript à notre fichier html ?

Comme pour le css on relie le fichier dans la partie head de notre page html avec la balise `script`.

`<script src="index.js"></script>`

PS : On peut aussi mettre le script à la fin du code html.

## Afficher un élement dans la console

Pour afficher un élément dans la console on utilise `console.log`.

`console.log('coucou');`

`console.log(23);`

## Les valeurs primitifs

Il s'agit des valeurs principales qu'il est possible d'utiliser avec javascript.

### Strings

Il s'agit de valeurs de type texte. Les strings sont toujours entre guillemet.
``'Je suis Hamza';``

En cas de mot avec une apostrophe, et pour ne pas avoir de soucis avec le ' on écrit de cette façon : `'je m/'appelle Hamza';`

### Numbers

Il s'agit de valeurs de type nombre.
`42;`

### Booleans

Il s'agit d'une valeur qui est soit vraie soit fausse. 

`true;`
`false;`

### Undefined

C'est une valeur qui n'éxiste pas

### Null

C'est une valeur qui est vide

### NaN

C'est une valeur qui resulte d'une operation mathématique mais avec autre choses que des nombres.

## Les variables

Une variable est comme une boite dans laquelle on va stocker une donée.
Pour déclarer une variable on écrit `let name = 'hamza';` ou `const age = 26;`.

* la variable var n'est plus utilisé
* la variable let peut être modifié
* la variable const ne change plus

## Les objets

Plutôt que de créer plusieurs variables, on peut les regrouper dans un objet.

````
const me = {
nom : 'nayyer',
prenom: 'hamza',
age : 26,
};
````

Pour afficher le prénom par exemple on écrit `console.log(me.prenom);`

## Les prédicats

Il est possible de vérifier si une valeur est vraie ou fausse.
````
const isMajor = me.age >= 18;
````
La console devrait renvoyer `true` parce que hamza a plus de 18 ans.

### Composer des prédicats

Il est possible de vérifier si plusieurs conditions sont vraies ou fausses avec les symboles `&&` (pour ET) et `||` (pour OU).

````
const isMajorAndIsName = (me.prenom === 'hamza') && (me.age >= 18);

console.log(isMajorAndIsName);
````

La console devrait renvoyer `true`.

## Modifier le html avec du JS

Si on veut modifier le titre h1 d'une page html par exemple. On va devoir le selectionner avec `queryselector`.

````
const person = {
    firstname : 'Hamza',
    lastname : 'Nayyer',
    age : 26,
    gender : 'M',
    adresse : 'rue de la paix',
    etudes : 'Mes etudes',
};

const title = document.querySelector("h1");
title.textContent = person.firstname + " " + person.lastname;
````

Le h1 de la page html devrait maintenant être remplacé par Hamza Nayyer.

## La structure conditionnelle if  else

Il est possible de renvoyer un résultat en fonction des conditions que l'on va fixer.

````
const person = {
    firstname : 'Hamza',
    lastname : 'Nayyer',
    age : 26,
    gender : 'M',
    adresse : 'rue de la paix',
    etudes : 'Mes etudes',
};

if (person.gender === 'F') {
  console.log("coucou je suis une femme");
} else if (person.gender === 'M') {
  console.log("coucou je suis un homme");
} else {
  console.log("inconnu");
}
````

Il est aussi possible de mettre cette structure conditionnelle dans une fonction.

````
const hamzaNayyer = {
    firstname : 'Hamza',
    lastname : 'Nayyer',
    age : 26,
    gender : 'M',
    adresse : 'rue de la paix',
    etudes : 'Mes etudes',
};

function sayGender(person) {
    if (person.gender === 'F') {
      console.log("coucou je suis une femme");
    } else if (person.gender === 'M') {
      console.log("coucou je suis un homme");
    } else {
      console.log("inconnu");
    }
}

sayGender(hamzaNayyer);
````

La fonction devrait renvoyer `"coucou je suis un homme"`.
