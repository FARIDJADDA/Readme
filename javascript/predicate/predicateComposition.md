
>_Camel Case = IsMajor ( le fait de mettre une majuscule au début de chaque mot )_
&& = And (informatique)
||  = Or (informatique)

nous pouvons combiner les deux .
exemple:
const IsMaleOrIsFemaleAndIsMajorAndIsMinor = (IsFemale || IsMale) && (IsMajor && IsMinor) ;
console.log ( IsMaleOrIsFemaleAndIsMajor);

l'ordinateur va d'abord examiner la première parenthèse puis la comparer à la deuxième pour donner une reponse .
