+ [Object.keys()](#mathround-)

# Object.values() :

_La méthode Object.values() renvoie un tableau contenant les valeurs des propriétés propres énumérables d'un objet dont l'ordre est le même que celui obtenu avec une boucle for...in (la boucle for-in est différente car elle parcourt également les propriétés héritées)._

# Demo: Object.values() :

````js
const object1 = {
  a: 'somestring',
  b: 42,
  c: false
};

console.log(Object.values(object1));
// expected output: Array ["somestring", 42, false]
````

# Syntaxe

     Object.values(obj)
     
### Paramètres

**obj**
_L'objet dont on souhaite connaître les valeurs des propriétés propres énumérables._
### Valeur de retour
_Un tableau dont les éléments sont les valeurs des propriétés énumérables de l'objet passé en argument._

# Description:

_Object.values() renvoie un tableau dont les éléments sont les valeurs des propriétés énumérables directement rattachées à l'objet passé en argument. L'ordre du tableau est le même que celui obtenu lorsqu'on parcourt les propriétés manuellement._

# Object.keys() 

_La méthode Object.keys() renvoie un tableau contenant les noms des propriétés propres à un objet (qui ne sont pas héritées via la chaîne de prototypes) et qui sont énumérables. L'ordre de ce tableau est le même que celui obtenu par une boucle for...in (à la différence qu'une boucle for-in liste également les propriétés héritées)._

# Demo: Object.keys() :

````js
const object1 = {
  a: 'somestring',
  b: 42,
  c: false
};

console.log(Object.keys(object1));
// expected output: Array ["a", "b", "c"]
````

# Syntaxe :

Object.keys(obj)

### Paramètres :

##### obj
_L'objet dont on souhaite lister les propriétés propres et énumérables._

### Valeur de retour:

_Un tableau de chaînes de caractères qui sont les noms des propriétés énumérables de l'objet passé en argument._

### Description :

_Object.keys() renvoie un tableau dont les éléments sont les chaînes de caractères des noms des propriétés propres et énumérables d'obj. L'ordre des propriétés obtenu est le même que celui obtenu lorsqu'on boucle manuellement sur les propriétés de l'objet._

