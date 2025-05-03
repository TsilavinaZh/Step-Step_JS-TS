# Cours Javascript

## Introduction à JS
JavaScript est un langage de programmation polyvalent utilisé pour créer du contenu web dynamique et interactif. Il est pris en charge par tous les navigateurs modernes.

### Exemple 1 :
```javascript
console.log("Bienvenue en JavaScript !");
```

### Exemple 2 :
```javascript
let message = "Hello, World!";
console.log(message);
```

## Où utiliser JS
JavaScript peut être placé dans la balise `<head>` ou `<body>` d'un document HTML, ou dans un fichier externe.

### Exemple 1 :
```html
<script>
    console.log("JavaScript dans la balise <head> ou <body>");
</script>
```

### Exemple 2 :
```html
<script src="script.js"></script>
```

## Sortie JS
JavaScript peut afficher des résultats à l'aide de méthodes comme `console.log()`, `alert()` ou en manipulant le DOM.

### Exemple 1 :
```javascript
console.log("Ceci est une sortie dans la console.");
```

### Exemple 2 :
```javascript
document.getElementById("demo").innerHTML = "Bonjour, le monde !";
```

## Instructions JS
Les instructions JavaScript sont des commandes exécutées par le navigateur.

### Exemple 1 :
```javascript
let x = 5;
let y = 10;
console.log(x + y);
```

### Exemple 2 :
```javascript
let a = 20;
let b = 15;
console.log(a - b);
```

## Syntaxe JS
La syntaxe JavaScript définit les règles pour écrire du code, y compris les mots-clés, les opérateurs et la structure.

### Exemple 1 :
```javascript
if (x > y) {
    console.log("x est supérieur à y");
}
```

### Exemple 2 :
```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

## Commentaires JS
Les commentaires sont utilisés pour expliquer le code et sont ignorés par le navigateur.

### Exemple 1 :
```javascript
// Ceci est un commentaire sur une ligne
```

### Exemple 2 :
```javascript
/* Ceci est un commentaire
   sur plusieurs lignes */
```

## Variables JS
Les variables stockent des valeurs de données et sont déclarées à l'aide de `var`, `let` ou `const`.

### Exemple 1 :
```javascript
let nom = "Alice";
console.log(nom);
```

### Exemple 2 :
```javascript
const age = 25;
console.log(age);
```

## Let en JS
`let` déclare des variables à portée de bloc.

### Exemple 1 :
```javascript
let x = 10;
{
    let x = 20;
    console.log(x); // 20
}
```

### Exemple 2 :
```javascript
let y = 30;
console.log(y); // 30
```

## Const en JS
`const` déclare des constantes à portée de bloc qui ne peuvent pas être réaffectées.

### Exemple 1 :
```javascript
const PI = 3.14;
console.log(PI);
```

### Exemple 2 :
```javascript
const nom = "Alice";
console.log(nom);
```

## JS Operators
Les opérateurs JavaScript sont utilisés pour effectuer des opérations sur des variables et des valeurs.

### Exemple 1 :
```javascript
let a = 10;
let b = 5;
console.log(a + b); // 15
```

### Exemple 2 :
```javascript
let x = 8;
let y = 2;
console.log(x / y); // 4
```

## JS Arithmetic
Les opérateurs arithmétiques effectuent des calculs mathématiques sur des nombres.

### Exemple 1 :
```javascript
let x = 20;
let y = 3;
console.log(x % y); // 2
```

### Exemple 2 :
```javascript
let base = 2;
let exp = 3;
console.log(base ** exp); // 8
```

## JS Assignment
Les opérateurs d'affectation attribuent des valeurs aux variables.

### Exemple 1 :
```javascript
let z = 10;
z += 5;
console.log(z); // 15
```

### Exemple 2 :
```javascript
let a = 20;
a *= 2;
console.log(a); // 40
```

## JS Data Types
JavaScript prend en charge différents types de données, comme les chaînes, les nombres, les objets, etc.

### Exemple 1 :
```javascript
let str = "Bonjour";
console.log(typeof str); // string
```

### Exemple 2 :
```javascript
let num = 42;
console.log(typeof num); // number
```

## JS Functions
Les fonctions sont des blocs de code conçus pour effectuer une tâche particulière.

### Exemple 1 :
```javascript
function saluer(nom) {
    return `Bonjour, ${nom} !`;
}
console.log(saluer("Alice"));
```

### Exemple 2 :
```javascript
function addition(a, b) {
    return a + b;
}
console.log(addition(5, 7)); // 12
```

## JS Objects
Les objets sont des collections de paires clé-valeur.

### Exemple 1 :
```javascript
let personne = {
    nom: "Alice",
    age: 25
};
console.log(personne.nom);
```

### Exemple 2 :
```javascript
let voiture = {
    marque: "Toyota",
    modele: "Corolla"
};
console.log(voiture.modele);
```

## JS Number Properties
Les propriétés des nombres en JavaScript fournissent des informations sur les valeurs numériques.

### Exemple 1 :
```javascript
console.log(Number.MAX_VALUE); // Valeur maximale possible
```

### Exemple 2 :
```javascript
console.log(Number.MIN_VALUE); // Valeur minimale possible
```

## JS Arrays
Les tableaux en JavaScript sont utilisés pour stocker plusieurs valeurs dans une seule variable.

### Exemple 1 :
```javascript
let fruits = ["Pomme", "Banane", "Cerise"];
console.log(fruits[0]); // Pomme
```

### Exemple 2 :
```javascript
let nombres = [1, 2, 3, 4];
console.log(nombres.length); // 4
```

## JS Array Methods
Les méthodes de tableau permettent de manipuler et de travailler avec des tableaux.

### Exemple 1 :
```javascript
let fruits = ["Pomme", "Banane"];
fruits.push("Cerise");
console.log(fruits); // ["Pomme", "Banane", "Cerise"]
```

### Exemple 2 :
```javascript
let nombres = [1, 2, 3];
nombres.pop();
console.log(nombres); // [1, 2]
```

## JS Array Search
Les méthodes de recherche permettent de trouver des éléments dans un tableau.

### Exemple 1 :
```javascript
let fruits = ["Pomme", "Banane", "Cerise"];
console.log(fruits.indexOf("Banane")); // 1
```

### Exemple 2 :
```javascript
let nombres = [10, 20, 30];
console.log(nombres.includes(20)); // true
```

## JS Array Sort
Les tableaux peuvent être triés à l'aide de la méthode `sort()`.

### Exemple 1 :
```javascript
let fruits = ["Banane", "Pomme", "Cerise"];
fruits.sort();
console.log(fruits); // ["Banane", "Cerise", "Pomme"]
```

### Exemple 2 :
```javascript
let nombres = [40, 10, 30, 20];
nombres.sort((a, b) => a - b);
console.log(nombres); // [10, 20, 30, 40]
```

## JS Array Iteration
Les méthodes d'itération permettent de parcourir les éléments d'un tableau.

### Exemple 1 :
```javascript
let fruits = ["Pomme", "Banane", "Cerise"];
fruits.forEach(fruit => console.log(fruit));
```

### Exemple 2 :
```javascript
let nombres = [1, 2, 3];
let doubles = nombres.map(n => n * 2);
console.log(doubles); // [2, 4, 6]
```

## JS Array Const
Les tableaux déclarés avec `const` ne peuvent pas être réaffectés, mais leurs éléments peuvent être modifiés.

### Exemple 1 :
```javascript
const fruits = ["Pomme", "Banane"];
fruits[0] = "Cerise";
console.log(fruits); // ["Cerise", "Banane"]
```

### Exemple 2 :
```javascript
const nombres = [1, 2, 3];
nombres.push(4);
console.log(nombres); // [1, 2, 3, 4]
```

## JS Dates
Les objets Date en JavaScript permettent de travailler avec des dates et des heures.

### Exemple 1 :
```javascript
let date = new Date();
console.log(date.toDateString()); // Affiche la date sous forme lisible
```

### Exemple 2 :
```javascript
let date = new Date("2023-01-01");
console.log(date.getFullYear()); // 2023
```

## JS Date Formats
Les dates peuvent être formatées de différentes manières en JavaScript.

### Exemple 1 :
```javascript
let date = new Date();
console.log(date.toISOString()); // Format ISO 8601
```

### Exemple 2 :
```javascript
let date = new Date();
console.log(date.toLocaleDateString("fr-FR")); // Format local français
```

## JS Date Get Methods
Les méthodes `get` permettent d'extraire des informations spécifiques d'un objet Date.

### Exemple 1 :
```javascript
let date = new Date();
console.log(date.getFullYear()); // Année actuelle
```

### Exemple 2 :
```javascript
let date = new Date();
console.log(date.getMonth()); // Mois actuel (0-11)
```

## JS Date Set Methods
Les méthodes `set` permettent de modifier les valeurs d'un objet Date.

### Exemple 1 :
```javascript
let date = new Date();
date.setFullYear(2025);
console.log(date.getFullYear()); // 2025
```

### Exemple 2 :
```javascript
let date = new Date();
date.setMonth(11); // Décembre
console.log(date.getMonth()); // 11
```

## JS Math
L'objet Math fournit des méthodes et des propriétés pour effectuer des calculs mathématiques.

### Exemple 1 :
```javascript
console.log(Math.sqrt(16)); // 4
```

### Exemple 2 :
```javascript
console.log(Math.pow(2, 3)); // 8
```

## JS Random
La méthode `Math.random()` génère un nombre aléatoire entre 0 (inclus) et 1 (exclus).

### Exemple 1 :
```javascript
console.log(Math.random()); // Nombre aléatoire entre 0 et 1
```

### Exemple 2 :
```javascript
console.log(Math.floor(Math.random() * 10)); // Nombre entier entre 0 et 9
```

## JS Booleans
Les valeurs booléennes représentent `true` ou `false`.

### Exemple 1 :
```javascript
let isAdult = true;
console.log(isAdult); // true
```

### Exemple 2 :
```javascript
let isMinor = 5 < 3;
console.log(isMinor); // false
```

## JS Comparisons
Les opérateurs de comparaison sont utilisés pour comparer des valeurs.

### Exemple 1 :
```javascript
console.log(10 > 5); // true
```

### Exemple 2 :
```javascript
console.log(10 === "10"); // false
```

## JS If Else
Les instructions `if...else` permettent d'exécuter du code en fonction d'une condition.

### Exemple 1 :
```javascript
let age = 18;
if (age >= 18) {
    console.log("Adulte");
} else {
    console.log("Mineur");
}
```

### Exemple 2 :
```javascript
let score = 75;
if (score >= 90) {
    console.log("Excellent");
} else if (score >= 50) {
    console.log("Passable");
} else {
    console.log("Échec");
}
```

## JS Switch
L'instruction `switch` est utilisée pour exécuter différentes actions en fonction de différentes conditions.

### Exemple 1 :
```javascript
let fruit = "Pomme";
switch (fruit) {
    case "Pomme":
        console.log("C'est une pomme");
        break;
    case "Banane":
        console.log("C'est une banane");
        break;
    default:
        console.log("Fruit inconnu");
}
```

### Exemple 2 :
```javascript
let jour = 3;
switch (jour) {
    case 1:
        console.log("Lundi");
        break;
    case 2:
        console.log("Mardi");
        break;
    case 3:
        console.log("Mercredi");
        break;
    default:
        console.log("Jour inconnu");
}
```

## JS Loop For
La boucle `for` est utilisée pour exécuter un bloc de code un nombre spécifique de fois.

### Exemple 1 :
```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

### Exemple 2 :
```javascript
let fruits = ["Pomme", "Banane", "Cerise"];
for (let i = 0; i < fruits.length; i++) {
    console.log(fruits[i]);
}
```


## JS Loop For In
La boucle `for...in` est utilisée pour itérer sur les propriétés énumérables d'un objet.

### Exemple 1 :
```javascript
let personne = { nom: "Alice", age: 25 };
for (let cle in personne) {
    console.log(`${cle}: ${personne[cle]}`);
}
```

### Exemple 2 :
```javascript
let tableau = [10, 20, 30];
for (let index in tableau) {
    console.log(index); // Affiche les indices
}
```

## JS Loop For Of
La boucle `for...of` est utilisée pour itérer sur des objets itérables comme les tableaux ou les chaînes.

### Exemple 1 :
```javascript
let fruits = ["Pomme", "Banane", "Cerise"];
for (let fruit of fruits) {
    console.log(fruit);
}
```

### Exemple 2 :
```javascript
let chaine = "Bonjour";
for (let lettre of chaine) {
    console.log(lettre);
}
```

## JS Loop While
La boucle `while` exécute un bloc de code tant qu'une condition est vraie.

### Exemple 1 :
```javascript
let i = 0;
while (i < 5) {
    console.log(i);
    i++;
}
```

### Exemple 2 :
```javascript
let nombre = 10;
while (nombre > 0) {
    console.log(nombre);
    nombre--;
}
```

## JS Break
L'instruction `break` permet de sortir d'une boucle avant qu'elle ne soit terminée.

### Exemple 1 :
```javascript
for (let i = 0; i < 10; i++) {
    if (i === 5) {
        break;
    }
    console.log(i);
}
```

### Exemple 2 :
```javascript
let i = 0;
while (true) {
    if (i === 3) {
        break;
    }
    console.log(i);
    i++;
}
```

## JS Iterables
Les objets itérables sont des objets qui peuvent être parcourus avec une boucle `for...of`.

### Exemple 1 :
```javascript
let tableau = [1, 2, 3];
for (let valeur of tableau) {
    console.log(valeur);
}
```

### Exemple 2 :
```javascript
let chaine = "JavaScript";
for (let caractere of chaine) {
    console.log(caractere);
}
```

## JS Sets
Un `Set` est une collection d'éléments uniques.

### Exemple 1 :
```javascript
let ensemble = new Set([1, 2, 3, 3]);
console.log(ensemble); // {1, 2, 3}
```

### Exemple 2 :
```javascript
let ensemble = new Set();
ensemble.add(10);
ensemble.add(20);
console.log(ensemble.has(10)); // true
```

## JS Set Methods
Les méthodes des `Set` permettent d'ajouter, supprimer ou vérifier des éléments.

### Exemple 1 :
```javascript
let ensemble = new Set();
ensemble.add(1);
ensemble.add(2);
ensemble.delete(1);
console.log(ensemble); // {2}
```

### Exemple 2 :
```javascript
let ensemble = new Set([1, 2, 3]);
ensemble.clear();
console.log(ensemble.size); // 0
```

## JS Maps
Un `Map` est une collection de paires clé-valeur.

### Exemple 1 :
```javascript
let carte = new Map();
carte.set("nom", "Alice");
carte.set("age", 25);
console.log(carte.get("nom")); // Alice
```

### Exemple 2 :
```javascript
let carte = new Map([["cle1", "valeur1"], ["cle2", "valeur2"]]);
console.log(carte.size); // 2
```

## JS Map Methods
Les méthodes des `Map` permettent de manipuler les paires clé-valeur.

### Exemple 1 :
```javascript
let carte = new Map();
carte.set("nom", "Alice");
carte.delete("nom");
console.log(carte.has("nom")); // false
```

### Exemple 2 :
```javascript
let carte = new Map();
carte.set("a", 1);
carte.set("b", 2);
carte.clear();
console.log(carte.size); // 0
```


## JS Typeof
L'opérateur `typeof` retourne une chaîne indiquant le type d'une variable ou d'une valeur.

### Exemple 1 :
```javascript
let x = 42;
console.log(typeof x); // "number"
```

### Exemple 2 :
```javascript
let y = "Bonjour";
console.log(typeof y); // "string"
```

## JS Type Conversion
La conversion de type permet de convertir une valeur d'un type à un autre.

### Exemple 1 :
```javascript
let num = "42";
let convertedNum = Number(num);
console.log(typeof convertedNum); // "number"
```

### Exemple 2 :
```javascript
let bool = true;
let convertedBool = String(bool);
console.log(typeof convertedBool); // "string"
```

## JS Destructuring
La déstructuration permet d'extraire des valeurs d'objets ou de tableaux.

### Exemple 1 :
```javascript
let [a, b] = [1, 2];
console.log(a, b); // 1, 2
```

### Exemple 2 :
```javascript
let { nom, age } = { nom: "Alice", age: 25 };
console.log(nom, age); // Alice, 25
```

## JS Bitwise
Les opérateurs bit à bit effectuent des opérations sur les représentations binaires des nombres.

### Exemple 1 :
```javascript
let x = 5 & 1; // AND bit à bit
console.log(x); // 1
```

### Exemple 2 :
```javascript
let y = 5 | 1; // OR bit à bit
console.log(y); // 5
```

## JS RegExp
Les expressions régulières sont utilisées pour rechercher des motifs dans des chaînes.

### Exemple 1 :
```javascript
let regex = /bonjour/i;
console.log(regex.test("Bonjour")); // true
```

### Exemple 2 :
```javascript
let texte = "JavaScript est génial";
let resultat = texte.match(/génial/);
console.log(resultat[0]); // "génial"
```

## JS Precedence
La priorité des opérateurs détermine l'ordre dans lequel les opérations sont effectuées.

### Exemple 1 :
```javascript
let x = 5 + 3 * 2;
console.log(x); // 11
```

### Exemple 2 :
```javascript
let y = (5 + 3) * 2;
console.log(y); // 16
```

## JS Errors
Les erreurs en JavaScript peuvent être gérées avec `try...catch`.

### Exemple 1 :
```javascript
try {
    console.log(x);
} catch (error) {
    console.log("Erreur détectée :", error.message);
}
```

### Exemple 2 :
```javascript
try {
    throw new Error("Ceci est une erreur personnalisée");
} catch (error) {
    console.log(error.message);
}
```

## JS Scope
La portée détermine où les variables sont accessibles dans le code.

### Exemple 1 :
```javascript
function test() {
    let x = 10; // Portée locale
    console.log(x);
}
test();
// console.log(x); // Erreur : x n'est pas défini
```

### Exemple 2 :
```javascript
let y = 20; // Portée globale
function afficher() {
    console.log(y);
}
afficher();
```

## JS Hoisting
Le "hoisting" permet d'utiliser des variables ou des fonctions avant leur déclaration.

### Exemple 1 :
```javascript
console.log(x); // undefined
var x = 5;
```

### Exemple 2 :
```javascript
saluer();
function saluer() {
    console.log("Bonjour !");
}
```

## JS Strict Mode
Le mode strict en JavaScript impose une syntaxe plus stricte pour éviter les erreurs courantes.

### Exemple 1 :
```javascript
"use strict";
x = 10; // Erreur : x n'est pas déclaré
```

### Exemple 2 :
```javascript
"use strict";
function test() {
    let y = 20;
    console.log(y);
}
test();
```

## JS this Keyword
Le mot-clé `this` fait référence à l'objet auquel il appartient.

### Exemple 1 :
```javascript
let personne = {
    nom: "Alice",
    saluer: function() {
        console.log(`Bonjour, je suis ${this.nom}`);
    }
};
personne.saluer();
```

### Exemple 2 :
```javascript
function afficherThis() {
    console.log(this);
}
afficherThis(); // Dans un navigateur, cela affiche l'objet global (window)
```

## JS Arrow Function
Les fonctions fléchées offrent une syntaxe concise et ne lient pas leur propre `this`.

### Exemple 1 :
```javascript
let addition = (a, b) => a + b;
console.log(addition(5, 3)); // 8
```

### Exemple 2 :
```javascript
let saluer = nom => `Bonjour, ${nom} !`;
console.log(saluer("Alice"));
```

## JS Classes
Les classes en JavaScript sont des modèles pour créer des objets.

### Exemple 1 :
```javascript
class Personne {
    constructor(nom, age) {
        this.nom = nom;
        this.age = age;
    }
    saluer() {
        console.log(`Bonjour, je m'appelle ${this.nom}`);
    }
}
let alice = new Personne("Alice", 25);
alice.saluer();
```

### Exemple 2 :
```javascript
class Animal {
    constructor(type) {
        this.type = type;
    }
    faireDuBruit() {
        console.log(`${this.type} fait du bruit`);
    }
}
let chien = new Animal("Chien");
chien.faireDuBruit();
```

## JS Modules
Les modules permettent de structurer le code en le divisant en fichiers réutilisables.

### Exemple 1 : Exportation
```javascript
// fichier math.js
export function addition(a, b) {
    return a + b;
}
```

### Exemple 2 : Importation
```javascript
// fichier main.js
import { addition } from './math.js';
console.log(addition(5, 3)); // 8
```

## JS JSON
JSON (JavaScript Object Notation) est un format léger pour échanger des données.

### Exemple 1 : Conversion en JSON
```javascript
let objet = { nom: "Alice", age: 25 };
let json = JSON.stringify(objet);
console.log(json); // {"nom":"Alice","age":25}
```

### Exemple 2 : Conversion depuis JSON
```javascript
let json = '{"nom":"Alice","age":25}';
let objet = JSON.parse(json);
console.log(objet.nom); // Alice
```

## JS Debugging
Le débogage permet d'identifier et de corriger les erreurs dans le code.

### Exemple 1 : Utilisation de `console.log`
```javascript
let x = 10;
console.log("Valeur de x :", x);
```

### Exemple 2 : Utilisation de `debugger`
```javascript
function test() {
    let y = 20;
    debugger; // Pause l'exécution ici
    console.log(y);
}
test();
```

## JS Style Guide
Un guide de style garantit un code cohérent et lisible.

### Exemple 1 : Utilisation de `const` et `let`
```javascript
const PI = 3.14;
let rayon = 5;
console.log(PI * rayon * rayon);
```

### Exemple 2 : Indentation et espaces
```javascript
function addition(a, b) {
    return a + b;
}
console.log(addition(5, 3));
```

## JS Best Practices
Les bonnes pratiques améliorent la qualité et la maintenabilité du code.

### Exemple 1 : Éviter les variables globales
```javascript
function calculer() {
    let resultat = 10; // Variable locale
    return resultat;
}
```

### Exemple 2 : Utiliser des commentaires clairs
```javascript
// Cette fonction calcule la somme de deux nombres
function addition(a, b) {
    return a + b;
}
```