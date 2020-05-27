# Composants et props

Les composants vous permettent de découper l’interface utilisateur en éléments indépendants et réutilisables, vous permettant ainsi de considérer chaque élément de manière isolée. Cette page fournit une introduction au concept de composants. Vous trouverez une référence détaillée de l’API des composants ici.

Conceptuellement, les composants sont comme des fonctions JavaScript. Ils acceptent des entrées quelconques (appelées « props ») et renvoient des éléments React décrivant ce qui doit apparaître à l’écran.


# Fonctions composants et composants à base de classes

Le moyen le plus simple de définir un composant consiste à écrire une fonction JavaScript :

````html
function Welcome(props) {
  return <h1>Bonjour, {props.name}</h1>;
}
````
_Cette fonction est un composant React valide car elle accepte un seul argument « props » (qui signifie « propriétés ») contenant des données, et renvoie un élément React. Nous appelons de tels composants des « fonctions composants », car ce sont littéralement des fonctions JavaScript._

