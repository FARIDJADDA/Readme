# Organiser son code Javascript

Pour organiser proprement son code il vaut mieux le séparer en deux fichiers :
* Un fichier avec le code javascript
* Un fichier pour manipuler le code appelé users.data par exemple

Pour se faire, il faut saisir dans le fichier contenant le code un `export`.
````
export const tab = [me, user, user2, user3, user4, user5];
````

Et dans le fichier pour manipuler le code :
````
import {tab} from './users.data';
````
