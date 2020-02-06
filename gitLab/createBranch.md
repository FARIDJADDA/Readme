# Qu'est-ce qu'une Master :

document principale avec tout les fichiers qui ont été accepté par le chef de projet 
version de reference qu'on va garder ... Si nous sommes bcp à travailler sur un projet
on utilisera donc des branches 

# Qu'est-ce qu'une branch :

une copie du repo a une date T pour faire nos propre modification sans toucher à la master dans un premier temps.

 
### Comment créer une branch :

en bas a droite git:master -> new branch
faire des modification dans sa branche commit puis chekout dans la master pour voir le resultat final <br/>
( <strong><em>really important! interdit de chekout entre 2 branches sans avoir commit avant</em></strong> )

### Comment envoyer sa branch vers la master:

:one: aller sur gitlab

:two: rafraichir la page principale et appuyer sur create merge request<br/>
( <strong><em>really important! bien faire attention qu'on va bien de from testBranch into master </em></strong> )

:three: assigner le chef de projet 

:four: submit merge request

:five: decocher delete source branch

