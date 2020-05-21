# Truthy et Falsy

## Truthy

Il s'agit de toutes les valeurs qui sont true. On peut s'en assurer à l'aide d'un prédicat.

`if() {console.log('ok')}` renvoie true.
`if(10) {console.log('ok')}` renvoie true car 10 existe.
`if([2, 3]) {console.log('ok')}` renvoie true aussi.

## Falsy

Il s'agit de toutes les valeurs qui sont false.

`if(false) {console.log('ok')}` renvoie rien (donc false)
`if(null) {console.log('ok')}` renvoie rien (donc false)
`if(undefined) {console.log('ok')}` renvoie rien (donc false)
`if(NaN) {console.log('ok')}` renvoie rien (donc false)
`if(0) {console.log('ok')}` renvoie rien (donc false)
`if('') {console.log('ok')}` renvoie rien (donc false)
`if() {console.log('ok')}` renvoie rien (donc false)

## Inverse 

`if(!true) {console.log('ok')}` renvoie rien (false)
`if(!false) {console.log('ok')}` renvoie true
`if(!1) {console.log('ok')}` renvoie false car l'inverse d'une chose qui existe n'existe pas.

Pour transformer quelque chose en boolean on peut mettre 2 '!!'.

`console.log(!!1) : true car 1 existe`
`console.log(!!null) : false car il n'existe pas`




