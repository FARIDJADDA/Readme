**SOMMAIRE :**

* [Introduction REACT](#introduction-react)
* [Racine de l'application](#racine-de-lapplication)
* [Creer un element](#creer-un-element)
* [utiliser JSX pour faire du react](#utiliser-jsx-pour-faire-du-react)
* [Interpolation](#interpolation)
* [Les composants](#les-composants)
* [Fonction composants et composants à base de classes](#fonctions-composants-et-composants--base-de-classes)
* [Produire le rendu d'un composant](#produire-le-rendu-dun-composant)
* [Composition de composants](#composition-de-composants)
* [Les props (proprietes)](#les-props-proprits)
* [Décomposition des props](#dcomposition-des-props)
* [Element enfant en JSX](#element-enfant-en-jxs)
* [Les fragments](#les-fragments)
* [Créer un composant](#crer-un-composant)
* [Passer les bons types](#passer-les-bons-types)
* [Spécifier les types des props](#spcifier-les-types-des-props)
* [Mettre du CSS](#mettre-du-css)
* [Passer des classes CSS dans un component](#passer-des-classes-css-dans-un-component)
* [Choisir une classe grâce à une props](#choisir-une-classe-grce--une-props)
* [La prop style](#la-prop-style)
* [Gérer les événements](#grer-les-vnements)
* [Gérer les clics](#grer-les-clics)
* [Gérer tous types d'évenements](#grer-tous-types-dvenements)
* [Gérer les états proprement](#grer-les-tats-proprement)
* [Structure d'un formulaire](#structure-dun-formulaire)
* [l'affichage conditionnel](#laffichage-conditionnel)
* [Rendre une liste](#rendre-une-liste)
* [Passer des functions en props](#passer-des-functions-en-props)
* [Gérer le monde extérieur](#grer-le-monde-extrieur--react)
* [React useEffect](#react-useeffect)


# Introduction REACT

React.Js, est une techno Javascript, mais il ne s’agit pas d’un framework à proprement parler. 
En fait, il s’agit plus d’une librairie open source qui permet de construire des interfaces utilisateur dynamique à l'aide du virtual DOM.

# Racine de l'application 

Dans notre fichier HTML, on va ajouter une balise « div » avec un identifiant (id). Par convention on l'appelera « root », ce sera la racine de notre application :
`<div id="root"></div>`

## Créer un élément

````
// SE LIER A NOTRE ROOT GRACE A SON ID

const root = document.getElementById('root');

// CREER UN ELEMENT (DIV) 

const exampleDiv = React.createElement('div', {
    className: 'main',
    children: `Bienvenue dans l'initiation à ${value} (version ${version})`,
  });
  ReactDOM.render(exampleDiv, root);
````

* children : Contenu de cette DIV qui est créer à l'interieur de root.
* className : C'est une classe en react.
* reactDom.render : on prend le Dom virtuel et on affiche (render) exampleDiv et root. C'est l'équivalent de return.

## Utiliser JSX pour faire du react

Pour faciliter l'utilisation de react on va mixer le html et le js à l'aide d'un nouveau langage : le JSX. 
Pour faire cela, on utilisera l'outil BABEL qui va transformer le JSX en javascript.

````
// CREER LE MEME ELEMENT EN JSX

const exampleDiv = <div className="main">
    Bienvenue dans l'initiation à ${value} (version ${version})
  </div>;
  
ReactDOM.render(exampleDiv,  document.getElementById('root'));
````

document.getElementById nous permettra de récupérer notre élément root que nous avons créé en HTML.

## Interpolation

Une interpolation s'écrit entre accolades.

````
const name = 'Hamza Nayyer';
const element = <h1>Bonjour, {name}</h1>;

ReactDOM.render(element, document.getElementById('root'));
````

On peut également utiliser un calcul `{1 + 1}` ou encore une fonction : 

````
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Kylian',
  lastName: 'Mbappé'
};

const element = (
  <h1>
    Bonjour, {formatName(user)} !
  </h1>
);

ReactDOM.render(element, document.getElementById('root'));
````

## Les composants 

Les composants vous permettent de découper l’interface utilisateur en éléments indépendants et réutilisables, vous permettant ainsi de considérer chaque élément de manière isolée.
Conceptuellement, les composants sont comme des fonctions JavaScript. 
Ils acceptent des entrées quelconques (appelées « props ») et renvoient des éléments React décrivant ce qui doit apparaître à l’écran.

## Fonctions composants et composants à base de classes

Le moyen le plus simple de définir un composant consiste à écrire une fonction JavaScript :

````
function Welcome(props) {
  return <h1>Bonjour, {props.name}</h1>;
}
````

Cette fonction est un composant React valide car elle accepte un seul argument « props » (qui signifie « propriétés ») contenant des données, et renvoie un élément React. Nous appelons de tels composants des « fonctions composants », car ce sont littéralement des fonctions JavaScript.
Vous pouvez également utiliser une classe ES6 pour définir un composant :

````
class Welcome extends React.Component {
  render() {
    return <h1>Bonjour, {this.props.name}</h1>;
  }
}
````

Les deux composants ci-dessus sont équivalents du point de vue de React.
Les composants (aussi bien fonctions que classes) possèdent quelques fonctionnalités supplémentaires dont nous discuterons

## Produire le rendu d'un composant

Jusqu’ici, nous n’avons rencontré que des éléments React représentant des balises DOM :

````
const element = <div />;
````

Mais ces éléments peuvent également représenter des composants définis par l’utilisateur :

````
const element = <Welcome name="Sara"/>;
````

Lorsque React rencontre un élément représentant un composant défini par l’utilisateur, il transmet les attributs JSX et les enfants à ce composant sous la forme d’un objet unique. Nous appelons cet objet « props ».
Par exemple, ce code affiche « Bonjour, Sara » sur la page :

````
function Welcome(props) {
  return <h1>Bonjour, {props.name}</h1>;
}

const element = <Welcome name="Sara" />;
ReactDOM.render(element, document.getElementById('root'));
````

Récapitulons ce qui se passe dans cet exemple :

1. On appelle ReactDOM.render() avec l’élément <Welcome name="Sara" />.
2. React appelle le composant Welcome avec comme props {name: 'Sara'}.
3. Notre composant Welcome retourne un élément <h1>Bonjour, Sara</h1> pour résultat.
4. React DOM met à jour efficacement le DOM pour correspondre à <h1>Bonjour, Sara</h1>.

> **Remarque**
> React considère les composants commençant par des lettres minuscules comme des balises DOM. 
> Par exemple, <div /> représente une balise HTML div, mais <Welcome /> représente un composant, et exige que l’identifiant Welcome existe dans la portée courante.

### Composition de composants

Composition de composants
Les composants peuvent faire référence à d’autres composants dans leur sortie. Ça nous permet d’utiliser la même abstraction de composants pour n’importe quel niveau de détail. Un bouton, un formulaire, une boîte de dialogue, un écran : dans React, ils sont généralement tous exprimés par des composants.

Par exemple, nous pouvons créer un composant App qui utilise plusieurs fois Welcome :

````
function Welcome(props) {
  return <h1>Bonjour, {props.name}</h1>;
}

function App() {
  return (
    <div>
      <Welcome name="Sara" />
      <Welcome name="Cahal" />
      <Welcome name="Edite" />
    </div>
  );
}

ReactDOM.render(
  <App />,
  document.getElementById('root')
);
````

## Les props (propriétés)

React nous permet de passer des props(abréviation de propriétés) aux composants. 
Vous pouvez passer n’importe quelle expression JavaScript comme prop, en l’entourant avec des accolades {}. Par exemple, dans ce code JSX :

````
<script type="text/babel">

<MyComponent foo={1 + 2 + 3 + 4} />

  ReactDOM.render(exampleDiv, document.getElementById('root'));
</script>
````

Pour MyComponent, la valeur de props.foo sera 10 parce que l’expression 1 + 2 + 3 + 4 est calculée.
Les props ressemblent à des attributs HTML. Si vous passez une chaîne de caractères via des props, 
vous n'avez pas besoin des accolades, mais tout autre type de données ou variable doit être entre accolades.

````
<MyComponent message="hello world" />

<MyComponent message={'hello world'} />
````

### Décomposition des props

Si vous avez déjà un objet props et souhaitez l’utiliser en JSX, vous pouvez utiliser l’opérateur de décomposition (spread operator, NdT) ... 
pour passer l’ensemble de l’objet props. Ces deux composants sont équivalents :
````
function App1() {
  return <Greeting firstName="Ben" lastName="Hector" />;
}

function App2() {
  const props = {firstName: 'Ben', lastName: 'Hector'};
  return <Greeting {...props} />;
}
````

## Element enfant en JXS

Vous pouvez mettre une chaîne de caractères entre une balise ouvrante et une fermante et props.children sera juste cette chaîne de caractères. 
C’est utile pour la plupart des éléments HTML natifs. Par exemple :

````
<MyComponent>Bonjour monde !</MyComponent>
````

> C’est du JSX valide, et props.children dans MyComponent sera simplement la chaîne de caractères "Bonjour monde !"

## Les fragments

````
<script type="text/babel">

  const className1 = 'main';
  const children1 = 'ma div1';

  const className2 = 'secondary';
  const children2 = 'ma div2';

  const props1 = {
    className: className1,
    children: children1,
  };

  const props2 = {
    className: className2,
    children: children2,
  };
  const exampleDiv = <div>
    <div {...props1} />
    <div {...props2} />
  </div>;

  ReactDOM.render(exampleDiv, document.getElementById('root'));
</script>
````

Pour afficher les deux props il faut mettre les deux div séparées à l'interieur de la div principal (voir ci-dessus)
Le problème c'est que les deux div sont à l'inteireur d'une div inutile, pour remedier à ce probleme on utilise les fragments (on met des balises vides) :

````
<script type="text/babel">
  const root = document.getElementById('root');

  const className1 = 'main';
  const children1 = 'ma div1';

  const className2 = 'secondary';
  const children2 = 'ma div2';

  const props1 = {
    className: className1,
    children: children1,
  };

  const props2 = {
    className: className2,
    children: children2,
  };
  const exampleDiv = <>
    <div {...props1} />
    <div {...props2} />
  </>;

  ReactDOM.render(exampleDiv, root);
</script>
````

## Créer un composant

````
function getTitle(className, title, number) {
    return <div className={className}>{`Titre n°${number}: ${title}`}</div>
  }

const exampleDiv =
      <div>
        {getTitle('main', 'coucou', 1)}
      </div>
````

Se composant est lourd, on va donc le faire d'une autre manière :

````
<script type="text/babel">
  const root = document.getElementById('root');

  function getTitle(className, title, number) {
    return <div className={className}>{`Titre n°${number}: ${title}`}</div>
  }

  function MyTitle({className, children, number}) {
    const props = {
      children: `Titre n°${number}: ${children}`,
      className
    };
    return <div {...props} />

  }

  const exampleDiv =
      <div>
        {getTitle('main', 'coucou', 1)}
        <MyTitle className="main" number="1">coucou</MyTitle>
      </div>

  ReactDOM.render(exampleDiv, root);
</script>
````

## Passer les bons types

Quand on veut être sur d'avoir les bons types dans notre component :

````
<script type="text/babel">
  const root = document.getElementById('root');

  function Hello({firstName, lastName, age, car}) {
    return (
        <div>
          <div>age : {typeof age}</div>
          <div>car : {typeof car}</div>
          Bonjour je m'appelle {firstName} {lastName} et j'ai {age} an(s)!
        </div>
    );
  }

  const exampleDiv = <Hello
      firstName='sebastien'
      lastName='Bianchi'
      age={17}
      car={true}
  />;

  ReactDOM.render(exampleDiv, root);
</script>
````

## Spécifier les types des props

On va ajouter la librairie et ensuite on va spécifier les types avec .propTypes

````
<script src="https://unpkg.com/prop-types@15.6/prop-types.js"></script>

<script type="text/babel">
  const root = document.getElementById('root');

  function Hello({firstName, lastName, age, car}) {
    return (
        <div>
          <div>age : {typeof age}</div>
          <div>car : {typeof car}</div>
          Bonjour je m'appelle {firstName} {lastName} et j'ai {age} an(s)!
        </div>
    );
  }

  Hello.propTypes = {
    firstName: PropTypes.string.isRequired,
    lastName: PropTypes.string.isRequired,
    age: PropTypes.number.isRequired,
    car: PropTypes.bool,
  };

  const exampleDiv = <Hello
      lastName='Bianchi'
      age={17}
      car={true}
  />;

  ReactDOM.render(exampleDiv, root);
</script>
````

Si jamais on se trompe et on met un string au lieu d'un boolean, une erreur s'affichera dans la console. 
Si on ne met pas de "car" du tout il ne va rien se passer il y aura simplement le car en moins dans le component.

## Mettre du CSS

````
<style>
    .container {
        border: 2px solid black;
    }
</style>

<script type="text/babel">
  const root = document.getElementById('root');

  function Box({...props}) {
    return (
        <div
          className="container bg-blue"
          {...props}
        />
    )
  }

  const exampleDiv = (
      <>
        <Box>
        mon container
        </Box>
      </>

  ReactDOM.render(exampleDiv, root);
</script>
````

## Passer des classes CSS dans un component

````
<style>
    .container {
        border: 2px solid black;
    }

    .bg-blue {
        background-color: #1edcff;
    }
    .bg-red {
        background-color: #ff5454;
    }
    .big {
        font-size: 50px;
    }
</style>

<script type="text/babel">
  const root = document.getElementById('root');

  function Box({className, ...props}) {
    return (
        <div
          className={`container ${className}`}
          {...props}
        />
    )
  }

  const exampleDiv = (
      <>
        <Box className="bg-blue big>
        mon container
        </Box>

        <Box className="bg-red>
        mon container
        </Box>
      </>

  ReactDOM.render(exampleDiv, root);
</script>
````

On a ajouté des couleurs et une taille.

## Choisir une classe grâce à une props

````
<style>
    .container {
        border: 2px solid black;
    }

    .bg-blue {
        background-color: #1edcff;
    }
    .bg-red {
        background-color: #ff5454;
    }
    .small {
        width: 50px;
        height: 50px;
    }
    .medium {
        width: 100px;
        height: 100px;
    }
    .large {
        width: 150px;
        height: 150px;
    }
</style>

<script type="text/babel">
  const root = document.getElementById('root');

  function Box({className, size = '', ...props}) {
    let sizeClass;
    if (size === 'big') {
      sizeClass = 'large'
    }
    if (size === 'middle') {
      sizeClass = 'medium'
    }
    if (size === 'little') {
      sizeClass = 'small'
    }
    return (
        <div
          className={`container ${className} ${sizeClass}`}
          {...props}
        />
    )
  }

  const exampleDiv = (
      <>
        <Box size="big" className="bg-blue">
        mon container
        </Box>
        <Box size="little" className="bg-red">
        mon container
        </Box>
      </>
  );

  ReactDOM.render(exampleDiv, root);
</script>
````

## La prop style

Il y a certaines propriétés qui sont prédéfinit en React comme style :

````
const exampleDiv = (
      <>
        <Box size="big" className="bg-blue">
        style={
            {color: 'white'}
        }>
        mon container
        </Box>
        <Box size="little" className="bg-red">
        mon container
        </Box>
      </>
  );
````
Il fonctionne car React connait style, si on avait créee une prop toto par exemple 

````
 toto={{name: 'hamza'}}
````

Le navigateur n'aurait rien affiché car il ne connait pas cette prop. Si on fait nos propres props
il faut les traiter dans la fonction.

## Gérer les événements

Pour gérer les événements en react on créee une application racine (App).

### Gérer les clics

On va créer un boutton, et afficher un compteur qui va compter le nombre de click

````
<script type="text/babel">

  const state = {count: 0};
  function App() {
    function handleClick() {
      setState({count: state.count + 1})
      console.log(state);
    }
    return (
        <>
            <h1>Nombre de clicks: {state.count}</h1>
            <button onClick={handleClick}>Ajouter 1</button>
        </>
    )
  }

  function setState(newState) {
    Object.assign(state, newState);
    renderApplication()
    }

function renderApplication() {
  ReactDOM.render(<App/>, document.getElementById('root'));
}

renderApplication();

</script>
````

* La fonction setState va remplacer l'ancien state par le nouveau.
* La fonction handleClick est la fonction qui va gérer le click.
* onClick va faire fonctionner le boutton.

## Gérer tous types d'évenements

Gérer plusieurs événements ainsi que les inputs :

````
<script type="text/babel">

  const state = {count: 0, lastEventType: ''};
  function App() {
    function handleEvent(event) {
      setState({count: state.count + 1, lastEventType: event.type});
    }

    function handleInputChange(event) {
        console.log(event.target.value)
      setState({name: event.target.value})
    }

    return (
        <>
            <h1>Bonjour {state.name}</h1>
          <h1>Nombre de clicks: {state.count}</h1>
          <h1>Dernier event: {state.lastEventType}</h1>
          <button
              onClick={handleEvent}
              onMouseEnter={handleEvent}
              onMouseLeave={handleEvent}
          >
            Ajouter 1
          </button>
            <input type="text" onChange={handleInputChange}/>

        </>
    )
  }

  function setState(newState) {
    Object.assign(state, newState);
    renderApplication()
  }

  function renderApplication() {
    ReactDOM.render(<App/>, document.getElementById('root'));
  }

  renderApplication();

</script>
````

## Gérer les états proprement

Il ne faut pas fabriquer sois-même les setState. On a un outil pour gérer les états : React.useState();
Il nous renvoie deux choses dans un tableau : state, setState.
On oubliera pas d'ajouter ...state à chaque setState à l'interieur des functions pour que tous les états fonctionnent correctement.

````
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Gérer les evenements</title>
</head>
<body>

<a href="./">Retour</a>
<h1>Gérer tous types d'evenements</h1>
<div id="root"></div>

<script crossorigin src="https://unpkg.com/react@16.13.1/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@16.13.1/umd/react-dom.development.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

<script type="text/babel">

  function App() {
   const [state, setState] = React.useState({
     count: 0,
     lastEventType: '',
     name: ''
   });

    function handleEvent(event) {
      setState({
        ...state,
        count: state.count + 1,
        lastEventType: event.type
      });
    }

    function handleInputChange(event) {
        console.log(event.target.value);
      setState({...state, name: event.target.value})
    }

    return (
        <>
            <h1>Bonjour {state.name}</h1>
          <h1>Nombre de clicks: {state.count}</h1>
          <h1>Dernier event: {state.lastEventType}</h1>
          <button
              onClick={handleEvent}
              onMouseEnter={handleEvent}
              onMouseLeave={handleEvent}
          >
            Ajouter 1
          </button>
            <input type="text" onChange={handleInputChange}/>
        </>
    )
  }

  function setState(newState) {
    Object.assign(state, newState);
    renderApplication()
  }

  function renderApplication() {
    ReactDOM.render(<App/>, document.getElementById('root'));
  }

  renderApplication();

</script>
</body>
</html>

````

## Structure d'un formulaire

````
<script type="text/babel">
  function MyForm() {

    const [state, setState] = React.useState({name: 'coucou', age: 12});

    function handleSubmit(event) {
      event.preventDefault();
      console.log(state);
    }

    function handleInput(event) {
      const {id, value, type} = event.target;
      setState({
        ...state,
        [id]: type === 'number' ? parseInt(value) : value,
      })
    }

    return <form onSubmit={handleSubmit}>
      <label htmlFor="name">Nom</label>
      <input
          value={state.name}
          onChange={handleInput}
          type="text" id="name"/>
      <label htmlFor="age">Age</label>
      <input
          value={state.age}
          onChange={handleInput}
          type="number" id="age"/>
      <button type="button">Annuler</button>
      <button type="submit">Valider</button>
    </form>;
  }

  ReactDOM.render(<MyForm/>, document.getElementById('root'));
</script>
````

## l'affichage conditionnel

Le code affichera un, deux ou trois en fonction de la valeur qui sera indiqué.

````
<script type="text/babel">
  function Un() {
    return <h1>Je suis Un</h1>;
  }

  function Deux() {
    return <h1>Je suis Deux</h1>;
  }

  function Trois() {
    return <h1>Je suis Trois</h1>;
  }

  function ManageDisplay({value}) {
    switch (value) {
      case 1:
        return <Un/>;
      case 2:
        return <Deux/>;
      case 3:
        return <Trois/>;
        default:
          return null
    }
  }

  function App() {

    return <>
      <ManageDisplay value={1}/>
    </>;
  }

  ReactDOM.render(<App/>, document.getElementById('root'));
</script>
````

## Rendre une liste

Afficher une liste à partir d'un array

````
<script type="text/babel">

  function Touche(props) {
    return <button>{props.display}</button>;
  }

  const liste = ['un', 'deux', 2, 'toto', 'tata'];

  function Calc() {
    return liste.map((value, index) =>
        <Touche display={value} key={index}/>,
  );
  }

  function App() {
    return <>
      <Calc/>
    </>
  }

  ReactDOM.render(<App/>, document.getElementById('root'));
</script>
````

## Passer des functions en props

Manipuler des données qui se trouvent dans un autre component

````
<script type="text/babel">
  const liste = ['un', 'deux', 2, 'toto', 'tata'];

  function Touche(props) {
    return <button onClick={() => props.action(props.display)}> {props.display} </button>;
  }

  function Calc(props) {
    return liste.map((value, index) =>
        <Touche action={props.action} display={value} key={index}/>,
    );
  }

  function App() {
    const [state, setState] = React.useState({display: null});

    const handleState = (display) => setState({display});

    return <>
      <h1>La dernière valeur est : {state.display}</h1>
      <Calc action={handleState}/>
    </>;
  }

  ReactDOM.render(<App/>, document.getElementById('root'));
</script>
````

* Fonction App : Il y a seulement un appel au composant Calc
* Fonction Calc : Il affiche les touches
* Fonction Touche : Il fabrique les touches, et change l'etat de App avec onClick. Pour que ça marche le setState doit passer par Calc et donc aussi par touche.
* props.action : va déclancher une action quand on clique , on le retrouve dans chaque component
* La fonction handleState prend en parametre display, ce display sera passé en paramètre à la fonction setState
* Dans onClick on met une fonction anonyme qui va s'auto exécuter et qui va mettre props.display en paramètre.

## Gérer le monde extérieur (à react)

* En dehors de react on utilise await/async
* Pour faire un get à partir d'une API en react on utilise la librairie axios.
* Le but est de faire un get d'un user en fonction de son id :

````
<script type="text/babel">

  const api = 'https://jsonplaceholder.typicode.com/users/';

  function DisplayUser({uid}) {

    const [user, setUser] = React.useState(null);

    React.useEffect(() => {
      async function getUserByUid(uid) {
        if (!uid) {
          return;
        }
        if (user) {
          return;
        }
        const temp = await axios.get(api + uid);
        setUser(temp);
      }
      getUserByUid(uid);
    }, [user]);

    return <div>{JSON.stringify(user)}</div>;
  }

  function App() {
    return <>
      <DisplayUser uid={1}/>
    </>;
  }

  ReactDOM.render(<App/>, document.getElementById('root'));
</script>
````

* Le get fonctionne aussi sans React.useEffect.
* JSNON.stringify = Permet de faire l'interpolation d'un objet

## React useEffect

React.useEffect permet de gérer les effets. 
On utilise ce Hook pour indiquer à React que notre composant doit exécuter quelque chose après chaque affichage. 
React enregistre ce qui est passé en argument, et l’appellera plus tard, après avoir mis à jour le DOM.

````
<script type="text/babel">

  const api = 'http://localhost:3015/api/hostels/';

  function State({state}) {
    return <pre>{state.message}</pre>;
  }

  function List({setState, reload}) {
    const [hotels, setHotels] = React.useState([]);
    React.useEffect(() => {
      async function getHotels() {
        console.log('USE EFFECT');
        try {
          const hotelsToGet = await axios.get(api);
          setHotels(hotelsToGet.data);
          setState({message: 'ok'});
        } catch (e) {
          setState({message: 'error'});
        }
      }
      getHotels();
    }, [reload]);

    return hotels.map((hotel, index) => <li key={index}>{hotel.name} {hotel.roomNumbers}</li>);
  }

  function App() {
    const [state, setState] = React.useState({message: 'initializing'});
    const [reload, setReload] = React.useState(false);
    function handleClick() {
      setReload(!reload)
    }
    return <>
      <ul>
        <List setState={setState} state={state} reload={reload}/>
      </ul>
      <State state={state}/>
      <button onClick={handleClick}>reload</button>
    </>;
  }
  ReactDOM.render(<App/>, document.getElementById('root'));
</script>
````

Ce qu'on met entre les [] à la fin de useEffect, permettra de relancer useEffect à chaque fois qu'on ferra une modification (set) dessus. 
Si on utilise reload comme dans notre exemple il n'y aura pas d'appel infini et le boutton permettra de recharger la page une fois seulement.
