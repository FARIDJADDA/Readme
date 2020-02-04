# Ce qui ne faut pas mettre dans un repo gitlab :

`les nodemodules`

+ package.json
+ package.log
(log trace des operations qui ont etaient fait)

# Qu'est-ce qu'un gitignore :

C'est un fichier que nous allons crée afin de d'enlever les fichiers dans gitlab qui nous sert pas .

# Comment faire un gitignore 

`1.`: créer un fichier .gitignore à la racine

`2`:  entrer le dossier ou fichier qu'on ne veut pas dans .gitignore

## Comment faire si un fichier s'ajoute quand meme :

`1` : on fait un git rm dans le terminal
(!! dossier est supprimé definitivement )

`2` : -> dans le terminal -> git rm -rf .idea

`3` : une fois tout supprimé -> Commit
