# Qu'est'ce qu'une composition de predicat :

_c'est quand on combine +sieur predicat ensemble_

### Exemple: :speech_balloon:
 
 _pour savoir si la personne est une femme ou un homme et si elle est mineur ou majeur_


````js
const IsMaleOrIsFemaleAndIsMajorAndIsMinor = (IsFemale || IsMale) && (IsMajor && IsMinor) ;
console.log ( IsMaleOrIsFemaleAndIsMajor);
````

_l'ordinateur va d'abord examiner la première parenthèse puis la comparer à la deuxième pour donner une réponse ._

##### NaB :

>_Camel Case = IsMajor ( le fait de mettre une majuscule au début de chaque mot )_<br>
&& = And (informatique)<br>
||  = Or (informatique)
