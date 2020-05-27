# Composants de fonction et de classe

La façon la plus simple de définir un composant est d'écrire une fonction JavaScript:

````jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
````

Cette fonction est un composant React valide car elle accepte un seul argument d'objet «props» (qui signifie propriétés) avec des données et renvoie un élément React. Nous appelons ces composants des «composants fonctionnels» car ce sont littéralement des fonctions JavaScript.
