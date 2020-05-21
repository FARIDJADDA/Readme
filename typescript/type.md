# Étapes du typage

1) Créer un dossier dans le projet qu'on va appeler models
2) Créer des interfaces pour chaque objet du tableau company :

exemples : 

````
const company = {
    name: '',
    address: '',
    size: 0,
    users: [],
}
````

3) Créer dans le dossier models :
* un fichier company.model.ts 
* un fichier user.model.ts 

Dans le fichier user.model.ts :

````
export interface UserModel {
    id: number;
    lastName: string;
    age: number;
}
````

Dans le fichier company.model.ts : 
````
export interface CompanyModel {
    name: string;
    address: string;
    size: number;
    users: userModel[];
}
````

4) Retourner sur serveur.ts et typer chaque élément :

````
const company: CompanyModel = {
    name: '',
    address: '',
    size: 0,
    users: [],
};

let users: UserModel[] = [
{
    id: 1,
    lastName: 'toto',
    age: 34,
}
{
    id: 2,
    lastName: 'titi',
    age: 29,
}

]
````

Sur les fonctions : 

````
function getUserById(id : number): Usermodel | undefined {
    return users.find((user) => user.id === id);
}

console.log(getUserById(2));
````

On type les paramètres (id) ainsi que la valeur de retour juste après les parenthèses (la fonction renvoie userModel ou undefined).
