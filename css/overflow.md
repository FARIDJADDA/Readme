# Overflow CSS


La `overflow` propriété spécifie s'il faut découper le contenu ou ajouter des barres de défilement lorsque le contenu d'un élément est trop grand pour tenir dans la zone spécifiée.

La `overflow` propriété a les valeurs suivantes:

+ `visible` - Défaut. Le débordement n'est pas écrêté. Le contenu s'affiche en dehors de la zone de l'élément
+ `hidden` - Le débordement est écrêté et le reste du contenu sera invisible
+ `scroll` - Le débordement est coupé, et une barre de défilement est ajoutée pour voir le reste du contenu
+ `auto`- Similaire à `scroll`, mais il ajoute des barres de défilement uniquement lorsque cela est nécessaire


> <strong><em>Remarque:</strong></em> La `overflow` propriété ne fonctionne que pour les éléments de bloc avec une hauteur spécifiée.<br/>
> <strong><em>Remarque:</strong></em> Sous OS X Lion (sur Mac), les barres de défilement sont masquées par défaut et ne s'affichent que lorsqu'elles sont utilisées (même si "overflow: scroll" est défini).
 
# Overflow: défilement


En définissant la valeur sur `scroll`, le débordement est coupé et une barre de défilement est ajoutée pour faire défiler l'intérieur de la boîte. Notez que cela ajoutera une barre de défilement horizontalement et verticalement (même si vous n'en avez pas besoin):

Vous pouvez utiliser la propriété de débordement lorsque vous souhaitez avoir un meilleur contrôle de la mise en page. La propriété overflow spécifie ce qui se passe si le contenu déborde de la boîte d'un élément.

### Exemple :speech_balloon:

```
div {
  overflow: scroll;
}
```

# Overflow-x et Overflow-y

Les propriétés `overflow-x` et `overflow-y`spécifient s'il faut modifier le débordement de contenu horizontalement ou verticalement (ou les deux):

`overflow-x` spécifie quoi faire avec les bords gauche / droit du contenu.
`overflow-y` spécifie ce qu'il faut faire avec les bords supérieur / inférieur du contenu.

### Exemple :speech_balloon:

````css
div {
  overflow-x: hidden; /* Hide horizontal scrollbar */
  overflow-y: scroll; /* Add vertical scrollbar */
}
````