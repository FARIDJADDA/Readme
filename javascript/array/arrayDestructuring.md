# Destructuration : 

_La destructuration permet de reccuperer des variables dans un tableau pour leur donner un nom directement et d'y avoir accés facilement._

#### Demonstration :

````js
const tab = ['tata', 'toto', 'tutu'];

tab[1] = 'coucou';

const [var1, var2, var3, var4] = tab;

console.log(var3);

````
##### Resultat :

![Screenshot](/img/console.png)
