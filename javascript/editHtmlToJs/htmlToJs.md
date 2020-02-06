# Comment Modifier le html d'une page avec js:

_Mettre  la balise `<script src="texte.html.js"></script>` a la fin de la balise `<body>` pour prendre en compte tout le contenue ._

## Dans l'index JS

chercher la fonction  `queryselector` (selectionner la requete) `'h1'`


__Code JS :__


```
const title = document.querySelector('h1');

title.textContent = me.FirstName +' '+ me.LastName +' '+ me.Age ;
```

>textContent _c'est le text affiché à l'interieur de la balise `h1`

>+' '+  =  espace 

>organisation : `<h2 id= " studies">`  les id permettent de repérer plus facilement la portion de texte qu'on veut modifier.