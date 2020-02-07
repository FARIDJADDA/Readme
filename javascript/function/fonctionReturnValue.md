# Les fonctions la valeur de retour :

_Quand il y a une valeure de return la fonction s'arrête_<br>
_Une fonction renvoie toujours quelque chose_

`mot clef:` return

### Exemple : :speech_balloon:

````js
const number1 = 50
const number2 = 30

function addition (x , y){
    return x+y;
}
function soustraction (x , y){
    return x-y;
}
const result = addition (x,y);
const result2 = soustraction (x,y);

console.log(result);
console.log(result2);
````