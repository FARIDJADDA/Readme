:monkey: :monkey: :monkey: :monkey: :monkey: :monkey: :monkey: :monkey: :monkey: :monkey: :monkey: :monkey: :monkey: :monkey: :monkey: :monkey: :monkey: :monkey: :monkey: :monkey: :monkey: :monkey: :monkey: :monkey:


# Style de bordure CSS

<strong>la border-stylepropriété spécifie le type de bordure à afficher.</strong>

 _Les valeurs suivantes sont autorisées:_

+ `dotted` - Définit une bordure en pointillé
+ `dashed` - Définit une bordure en pointillés
+ `solid` - Définit une bordure solide
+ `double` - Définit une double bordure
+ `groove`- Définit une bordure rainurée 3D. L'effet dépend de la valeur de la couleur de la bordure
+ `ridge`- Définit une bordure striée 3D. L'effet dépend de la valeur de la couleur de la bordure
+ `inset`- Définit une bordure d'encart 3D. L'effet dépend de la valeur de la couleur de la bordure
+ `outset`- Définit une bordure de départ 3D. L'effet dépend de la valeur de la couleur de la bordure
+ `none` - Ne définit aucune frontière
+ `hidden` - Définit une bordure cachée
+ `La border` -stylepropriété peut avoir de une à quatre valeurs (pour la bordure supérieure, la bordure droite, la bordure inférieure et la bordure gauche).

### Exemple
_Démonstration des différents styles de bordure:_

Exemple
Démonstration des différents styles de bordure:

```
p.dotted {
    border-style: dotted;
}
p.dashed {
    border-style: dashed;
}
p.solid {
    border-style: solid;
}
p.double {
    border-style: double;
}
p.groove {
    border-style: groove;
}
p.ridge {
    border-style: ridge;
}
p.inset {
    border-style: inset;
}
p.outset {
    border-style: outset;
}
p.none {
    border-style: none;
}
p.hidden {
    border-style: hidden;
}
p.mix {
    border-style: dotted dashed solid double;
}
p.dotted {
    border-style: dotted;
}
p.dashed {
    border-style: dashed;
}
p.solid {
    border-style: solid;
}
p.double {
    border-style: double;
}
p.groove {
    border-style: groove;
}
p.ridge {
    border-style: ridge;
}
p.inset {
    border-style: inset;
}
p.outset {
    border-style: outset;
}
p.none {
    border-style: none;
}
p.hidden {
    border-style: hidden;
}
p.mix {
    border-style: dotted dashed solid double;
}
```
>
>

# Bordures arrondies CSS

<strong>La border-radiuspropriété est utilisée pour ajouter des bordures arrondies à un élément:</strong>


### Exemple

```
p {
  border: 2px solid red;
  border-radius: 5px;
}
```