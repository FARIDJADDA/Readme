# includes() 

`includes()` permet de déterminer si un tableau contient une valeur et renvoie true si c'est le cas, false sinon.


#### Demo: Array.includes() : :speech_balloon:

````js
const array1 = [1, 2, 3];

console.log(array1.includes(2));
// expected output: true

const pets = ['cat', 'dog', 'bat'];

console.log(pets.includes('cat'));
// expected output: true

console.log(pets.includes('at'));
// expected output: false
````

##### Synthaxe :

_élément recherché_