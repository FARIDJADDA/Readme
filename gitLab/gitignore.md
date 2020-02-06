# Ce qui ne faut pas mettre dans un repo gitlab :

`les nodemodules`

+ package.json
+ package.log
(log trace des operations qui ont étaient faites)

# Qu'est-ce qu'un gitignore :

C'est un fichier que nous allons crée afin d'enlever les fichiers dans gitlab qui nous serve pas .

# Comment faire un gitignore 

:one: : créer un fichier .gitignore à la racine

:two: :  entrer le dossier ou fichier qu'on ne veut pas dans .gitignore

## Comment faire si un fichier s'ajoute quand meme :

:one: : on fait un git rm dans le terminal
(!! dossier est supprimé definitivement )

:two: : -> dans le terminal -> git rm -rf .idea

:three: : une fois tout supprimé -> Commit and push

