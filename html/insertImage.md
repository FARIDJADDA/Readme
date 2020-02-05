# Syntaxe des images HTML

_En HTML, les images sont définies avec la `<img>` balise.
La `<img>` balise est vide,
elle contient uniquement des attributs et n'a pas de balise de fermeture._

L' `src` attribut spécifie l'URL (adresse Web) de l'image:

```
<img src="url">
```

# L'attribut alt

L' `alt` attribut fournit un texte alternatif pour une image, <br/>
si l'utilisateur pour une raison quelconque ne peut pas la visualiser (en raison d'une connexion lente, <br/>
d'une erreur dans l'attribut src ou si l'utilisateur utilise un lecteur d'écran).

La valeur de l' `alt` attribut doit décrire l'image:

### Exemple
```
<img src="img_chania.jpg" alt="Flowers in Chania">
```

Si un navigateur ne trouve pas d'image, il affichera la valeur de l' alt attribut:

### Exemple

```
<img src="wrongname.gif" alt="Flowers in Chania">
```

<strong><em>Remarque</strong></em> _: l' altattribut est obligatoire. Une page Web ne sera pas validée correctement sans elle._