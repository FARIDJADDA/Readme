# Présentation de bash et commandes Linux

## Les shells

Un shell est un interpréteur de commandes destinés à accéder à des fonctionnalités du système d'exploitation.

Un shell est accessible depuis une console ou un terminal.

Il existe deux grandes catégories de shell : les shell Unix (présents sur MacOS, les systèmes GNU/Linux et de nombreux autres) et les shells Windows (comme par exemple Windows PowerShell sur les versions récentes).

Le terminal par défaut sur la plupart des systèmes Unix est bash.

Vous pouvez vérifier le shell courant en tapant dans votre terminal :

`echo $0`

Si vous avez Bash, vous aurez --bash.

Sur Windows, vous avez installé Git Bash qui est un ensemble de logiciels permettant d'émuler un 
environnement bash et les principales commandes POSIX.

## Les commandes systèmes

Voir les versions des commandes systèmes et d'où elles proviennents.

Sur un système GNU/Linux, par exemple Ubuntu, tapez :

`mkdir --version`

Le shell va exécuter des commandes en appelant les librairies systèmes nécessaires.

## La commande ls
ls est une commande signifiant list directory contents.

Autrement dit, cette commande permet de lister les contenus d'un dossier.

Comme vu précédemment cette commande, et donc ses options, ne dépendent pas du tout du shell utilisé mais si 
votre système est de type Unix ou non.

D'ailleurs les options varieront légèrement entre les systèmes, sur un système GNU vous pourrez faire :

`ls --all`

Mais sur MacOS cela ne fonctionnera pas.

Heureusement, il y a un standard, appelé POSIX (pour Portable Operating System Interface et le X pour Unix) 
qui standardise un grand nombre d'options sur les commandes systèmes pour les systèmes Unix.

Un ensemble d'options fonctionnera donc sur tous les systèmes respectants POSIX

Par exemple, l'option -a permet d'afficher les fichiers et les dossiers cachés (précédés par un .) sur tous les systèmes respectant POSIX.

Vous pouvez donc faire sur Ubuntu, Debian, MacOS etc :

`ls -a`

Une autre option POSIX utile est -t qui permet de trier les dossiers et fichiers du plus récent au plus ancien.

-l permet d'afficher en plus du nom, le type de fichier, les permissions, les noms du propriétaire et du groupe, la taille en octets et l'horodatage de la dernière modification.

Le type de fichier est le premier caractère : - pour un fichier ordinaire, d pour un dossier, ou encore l pour un lien symbolique.

## La commande echo
echo permet d'afficher sur la sortie standard ce qui lui est passé en argument suivi par une nouvelle ligne.

Par exemple :

`echo 1`
Affichera dans le terminal 1 suivi d'une nouvelle ligne.

## La commande rm
La commande rm pour remove permet d'effacer un ou plusieurs fichiers ou dossiers.

Les options POSIX sont les suivantes :

-r permet de supprimer récursivement les sous-répertoires. Cela signifie qu'elle va supprimer le dossier et tout son contenu :

`rm -r dossier`
-f pour force permet de ne pas demander de confirmation et de ne pas afficher de message d'erreur.

-i permet de demander à l'utilisateur de confirmer l'effacement pour chaque fichier. Il faudra taper y ou Y puis entrée pour confirmer la suppression fichier par fichier.

## La commande mkdir
La commande mkdir pour make directories permet de créer des dossiers, également appelés répertoires.

L'option -p permet de créer les répertoires parents s'ils n'existent pas.

Par exemple :

`mkdir -p a/b/c`
Va créer les répertoires parents du dossier c : a et b s'ils n'existent pas

## La commande cd
La commande cd pour change directory permet de naviguer dans un terminal entre les dossiers.

. signifie dossier courant et ../ remonter d'un cran.

Par exemple :

cd ../dossier2
Signifie remonte dans le dossier parent puis va dans le dossier2 situé dans celui-ci.

## La commande cat
La commande cat permet d'afficher le contenu d'un fichier.

`cat config`
