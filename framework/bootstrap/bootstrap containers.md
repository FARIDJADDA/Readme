

# Container classique & Container fluid

## Partie 1: Qu'est-ce que le container classique 

un site internet d'un container classique et centré le contenu du site sera seulement au millieu de la page 

## Partie 2: Quest-ce qu'un container fluid 
 
 le site internet d'un container fluid prendra tout l'espace de la page .
 
 
### `code:` :speech_balloon:
 
### container classique :thumbsup:

 `html:`
 
```

  <div class="container main">
     <div class="row content">
         <div class="col"> coucou </div>
     </div>
 
 </div>
```

`css:`

```
.main {
    background: ;
}

.content {
    height: ...px;
}
``` 

### container fluid  :thumbsup:
 
`html:`
 
 ```
 <div class="container-fluid main">
     <div class="row content">
         <div class="col"> coucou </div>
     </div>
 </div>

```