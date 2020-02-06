# Qu'est-ce qu'un predicat :

_les prédicats = true or false_
 
### Exemple 


`fiche identité:`_créer un objet_
 
``` 
const firstName = 'farid';
const lastName = 'djadda';
const age = 28;
const adress = '6 rue huntziger';
```

`Savoir si quelqu'un est majeur`

```
const IsMajor =  me.age >=18 ; 
console.log (IsMajor);
```

# Comment mixer les predicats :


```
const IsMajor =  me.age >=18 ; 
const (isFarid) = me.firstName === 'Farid'

console.log (IsMajor);
console.log (isFarid);
```