# Sort() :

sort() trie les éléments d'un tableau, </br>
dans ce même tableau, </br>
et renvoie le tableau. </br>
Par défaut, le tri s'effectue sur les éléments du tableau convertis en chaînes de caractères et triées selon les valeurs des unités de code UTF-16 des caractères. </br>

La complexité en espace mémoire et en temps utilisée pour le tri ne peut pas être garantie car elle dépend de l'implémentation.

#### Syntaxe

       arr.sort()
       arr.sort(fonctionComparaison)
       
_C'est une fonction de comparaison_

##### Demo: Array.sort()

````js
const months = ['March', 'Jan', 'Feb', 'Dec'];

months.sort();

console.log(months);

const array1 = [1, 30, 4, 21, 100000];

array1.sort();

console.log(array1);
````

      ​
