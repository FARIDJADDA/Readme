# splice() :

splice() modifie le contenu d'un tableau en retirant des éléments et/ou </br>
en ajoutant de nouveaux éléments à même le tableau. </br>
On peut ainsi vider ou remplacer une partie d'un tableau. 

#### Demo: Array.splice() : :speech_balloon:

````js
const months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');

console.log(months);

months.splice(4, 1, 'May');

console.log(months);
````