# try...catch :

_L'instruction try...catch regroupe des instructions à exécuter et définit une réponse si l'une de ces instructions provoque une exception._

# Demo: Statement - Try...Catch :

````js
try {
  nonExistentFunction();
}
catch(error) {
  console.error(error);
  // expected output: ReferenceError: nonExistentFunction is not defined
  // Note - error messages will vary depending on browser
}
````

### Syntaxe

````js
try {
   instructions_try
}
[catch (exception_var_1 if condition_1) { // non-standard
   instructions_catch_1
}]
````

