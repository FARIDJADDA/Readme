# JSX empêche les attaques par injection

Il est sûr d'incorporer des entrées utilisateur dans JSX:

````jsx
const title = response.potentiallyMaliciousInput;
// This is safe:
const element = <h1>{title}</h1>;
````

Par défaut, React DOM échappe à toutes les valeurs incorporées dans JSX avant de les rendre. Il garantit ainsi que vous ne pouvez jamais injecter quoi que ce soit qui ne soit pas explicitement écrit dans votre application. Tout est converti en chaîne avant d'être rendu. Cela aide à prévenir les attaques XSS (cross-site-scripting) .

