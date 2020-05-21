# Introduction à Angular

C'est un framework crée par Google.

## Installation et création de projet :

1. Saisir `npm install -g @angular/cli` pour installer Angular
2. Saisir ``cd ..`` pour aller dans WebstormProject
3. Créer un nouveau projet `ng new myProject`
4. Choisir y pour le routing
5. Chosir SCSS
6. Créer un nouveau projet dans git, copié son url
7. Ouvrir le projet sur webstorm, aller dans vcs/git/push puis coller l'url

Le projet est maintenant relié à git.

## Les modules

Il ya deux types de modules : les modules type page (home, about etc) 
et les modules type component qui sont réutilisables partout dans l'application (header, footer etc). 
Les components sont ensuite importés dans les modules de type page.

### Créer un module de type page 

`ng g m home --route=home --module=app-routing`
Cela va créer le module et le chemin (route) dans la racine de l'application (app-routing-module).

A chaque création de module de type page, la route va venir s'ajouter dans le fichier dans app-routing-module.

> Les fichiers App sont la racine de toute l'application, dans le App.html on ne laissera que la balise `<router-outlet></router-outlet>`
> Tout ce qui se trouvera dans ce fichier apparaitra partout dans l'application. 

Dans chaque module il y a des fichiers :
* module : `@NgModule`, c'est un décorateur qui va expliquer comment fonctionne le module. On notera qu'il y a un component de chaque module, on peut en importer d'autres si besoin.
* routing: avec la route du module.

### Créer un module de type component

`ng g m components/menu-main`
Cela va créer un dossier components et un module menu-main à l'intérieur. C'est dans ce même dossier que l'on va créer des components menus.
`ng g c components/menu-main/menu1`
Cela va créer un component menu1 et modifier le module main-menu en ajoutant le menu1 dans la déclaration. 
* Si on ajoute un deuxième menu il va venir également s'ajouter dans déclarations.
* Si on décide de n'afficher qu'un seul menu entre les deux, on va ajouter `exports` au module main-menu et on y ajoutera seulement le menu qu'on veut afficher et réutilisé à l'extérieur du module.
* Si on veut faire un menu avec des liens, on utilisera routerLink sans oublier de l'importer dans module menu.ts `RouterModule`

On peut donc ajouter le component menu dans app.component.html pour qu'il apparaisse dans toutes les pages (le menu devra être importé dans app.module).

## Faire des liens entre les pages

Pour passer de la page home à la page about on utilisera dans la page home la balise routerLink : `<a routerLink = "about">about</a>`

## Interpolation simple

Dans le fichier TS on aura le code, la logique, et à partir de ce fichier on pourra afficher des éléments dans le fichier HTML du module :
````
`Bonjour, {{name}}
````

On exporte avec ce symbole la variable name du fichier TS vers le HTML.

Fichier TS :

````
@Component({
  selector: 'app-menu1',
  templateUrl: './menu1.component.html',
  styleUrls: ['./menu1.component.scss']
})
export class Menu1Component implements OnInit {

  name: string;

  constructor() { }

  ngOnInit(): void {
    this.name = 'Jean Michel';
  }
}
````

le ngOnInit est une fonction équivalente au render ou au return dans react.

## Interpolation détaillée

On peut faire une interpolation :
* d'une opération `{{1 + 1}}`
* d'une fonction `{{sayHello()}}`
* d'un objet à condition d'utiliser un pipe qui va transformer l'objet en json `{{sayHello() | json}}`

>Cependant, il n'est pas possible d'utiliser un map ou une structure conditionnelle.

Il est aussi possible d'utiliser la notation dot `{{sayHello().name}}`

## Interpolation attribut

Pour faire un link avec une variable on utilise des crochets pour lui dire de récupérer la valeur de link1 et n'ont pas le string link1.
`<a [routerLink] = "link1">home</a>` 
Dans le fichier component on va créer la variable link1 = 'home';

## La directive NgFor

Pour éviter de répéter du code on va mettre toutes nos routes dans un array `allRoutes: string = ['about', 'home' etc]` puis utiliser Ng For :

````
<ul>
  Bonjour, {{sayHello() | json}}
  <li *ngFor="let current of allRoutes">
    <a [routerLink]="current">{{current}}</a>
  </li>
</ul>
````

ng For va donc parcourir le array et afficher en li chaque route/lien du array. Dans le cas ou on a un array d'objet dans le component :
````
allRoutes: MenuModel[] = [
    {url: 'home', name: 'acceuil'},
    {url: 'à-propos', name: 'à propos'}
];
````

On va également créer un dossier models, pour créer un fichier menu.model.ts et typer le menu dans allRoutes :

````
export interface MenuModel {
  url: string;
  name: string;
}
````
Dans le fichier html on pourra maintenant afficher nos liens à l'aide d'une interpolation et de ngFor :

````
<li *ngFor="let current of allRoutes">
    <a [routerLink]="current.url">{{current.name}}</a>
  </li>
````

## Ng If

On part du principe qu'on ne doit afficher le titre que si l'utilisateur à 18 ans ou plus :

````
<h2 *ngIf="age >= 18">POUR LES VIEUX</h2>
````

Si on veut mixer des directives structurelles (directives qui commencent par *) on utilisera ng container, on va donc afficher le menu en fonction de l'âge de l'utilisateur :

````
<ul>
  Bonjour, {{sayHello().age}} {{sayHello().name}}

  <ng-container *ngFor="let current of allRoutes">
    <li *ngIf="age>current.minimumAge">
      <a
        [routerLink]="current.url">
        {{current.name}}
      </a>
    </li>
  </ng-container>
</ul>
````

Dans le fichier menu1.Compnent

````
@Component({
  selector: 'app-menu1',
  templateUrl: './menu1.component.html',
  styleUrls: ['./menu1.component.scss']
})
export class Menu1Component implements OnInit {

  name: string;
  age = 70;

  allRoutes: MenuModel[] = [
    {url: 'home', name: 'acceuil', minimumAge: 0},
    {url: 'à-propos', name: 'à propos', minimumAge: 32}];

  constructor() {
  }

  ngOnInit(): void {
    this.name = 'Jean Michel';
  }

  sayHello() {
    return {name: 'hamza', age: 32};
  }
}
````

## Input

Dans les exemples précédents, on a mis notre array de routes à l'intérieur d'un component donc personne ne pourra y accéder dans l'application à part le component lui-même.
On va donc le déplacer en le remontant d'un cran (dans app.component.ts).

Pour passer en props un élément au app.html on va devoir ajouter un input dans le menu1.component `@input() routes: MenuModel[]`.
On peut maintenant ajouter la props dans le fichier app.component.html `<app-menu1[routes] = "allRoutes"></app-menu1>`
C'est de cette façon qu'on passe des données d'un component à un autre, du parent (app) à l'enfant (menu1).

## Services et injection de dépendance

Contrairement à ce que nouss avons fait avec le array allRoutes, On ne doit pas mettre un array ou des données dans un component mais dans des services. Les components servent à gérer les actions des utilisateurs.
Pour créer un service il faut saisir `ng g s services/menu` dans le terminal.
Une fois le service crée on se rend compte que le service est un injectable `@injectable` on va donc injecter les données du service là ou on en aura besoin :
Pour récupérer l'injection on va créer un private dans le constructor du app.component.ts par exemple:

````
export class AppComponent {
  title = 'promo3Angular';

  allRoutes: MenuModel[] = this.menuService.allRoutes;

  age = 54;

  constructor(
    private menuService: MenuService
  ) {
  }
}
````

Quand on veut juste passer une info du père à ses enfants on créé un input sinon on crée un service pour stocker des informations communes à toute notre application.

## Click

On veut maintenant passer une info de l'enfant au parent. On va donc créer un module mood pour gérer les humeurs d'une personne.
`ng g m component/mood`, cela va créer le mood module. Puis `ng g c components/mood` pour créer le component mood. Dans le mood module on va exporter mood.component puis on va dans app.component.html et on ajoute :
`<app-mood></app-mood>`.

Dans mood.component.html, on va créer nos bouttons

````
<div>
  <ul>
    <li><button (click)="iAmOk()">Je suis ok</button></li>
    <li><button (click)="iAmNotOk()">Je suis pas ok</button></li>
    <li><button (click)="iAmNeutral()">neutre</button></li>
  </ul>
</div>
````

Puis nos fonctions dans le moof.component.ts

````
export class MoodComponent implements OnInit {

  constructor() { }

  ngOnInit(): void {
  }

  iAmOk() {
    console.log('ok');
  }
  iAmNotOk() {
    console.log('pas ok');
  }
  iAmNeutral() {
    console.log('neutral');
  }
}
````

## Output et event emitter :

Pour remonter une info aux parents on va emettre une info au mood.ts avec eventEmmiter :

````
   export class MoodComponent implements OnInit {
   
     @Output() handleMoodChange: EventEmitter<string> = new EventEmitter<string>();
   
     constructor() { }
   
     ngOnInit(): void {
     }
   
     iAmOk() {
       this.handleMoodChange.emit('ok');
     }
     iAmNotOk() {
       this.handleMoodChange.emit('pas ok');
     }
     iAmNeutral() {
       this.handleMoodChange.emit('neutral');
     }
   }
````

Ce qui veut dire que quand handleMoodChange va emit on va recevoir cette information dans le comoonent app.
Puis on va faire en sorte que le père soit informé dans le fichier app.component.html :

````
<h1>{{message}}</h1>
<h1>Mon App</h1>
<app-menu1 [age]="age"></app-menu1>
<router-outlet></router-outlet>

<app-mood (handleMoodChange)="manageMoodChange($event)"></app-mood>
````
`$event` permet d'afficher le message du emit.

Dans le fichier app.components.ts on créer la méthode manageMoodChange :

````
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.scss']
})
export class AppComponent {
  title = 'promo3Angular';
  message: string;

  allRoutes: MenuModel[] = this.menuService.allRoutes;
  age = 54;

  constructor(
    private menuService: MenuService
  ) {
  }

  manageMoodChange(message: string) {
    this.message = message;
  }
}
````
