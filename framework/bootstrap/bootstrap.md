
> architecture de site internet pour html et css avec logiciel bootstrap
(framework = cadre de travail)

## telechargement bootstrap 

+ appuyer sur terminal (en bas à gauche de l'écran)
taper npm init
puis npm install bootstrap




+ crée file html (index) 
mettre la balise <link rel="stylesheet" href="../node_modules/bootstrap/dist/css/bootstrap.css">
(    ../  remonter d'un cran dans les dossiers et ctrl+esp pour la recherche de fichier apres le /   )

:anger: <stron> tres important crée une div "container" avec bootstrap </strong> _( elle stock toutes les info du site )_

+ crée une grille ( unité principale :ligne et a linterieur: colone )
ligne = row    <div classe="row"
identifié les colones avec des div

### Exemple: :speech_balloon:

```
<div classe="col">1</div>
<div classe="col">2</div>
etc..
```

add un style au col pour qu'elles soient bien centrées
* crée un stylesheets.css dans le dossier assets
puis add un style

### Exemple: :speech_balloon:

````css
.numbers {
    text-align: center ;
}
````

:anger: important !!<strong> ne pas oublier de mettre la ref :</strong>

````html
<link rel="stylesheet" href="../assets/style.css">
````