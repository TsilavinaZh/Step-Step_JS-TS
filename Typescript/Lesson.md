# Cours Typescript

### 1. Introduction à TypeScript

#### Exemple : Additionner deux nombres

Voici un exemple simple pour comprendre TypeScript :

```typescript
// Déclarer deux nombres
let nombre1: number = 5;
let nombre2: number = 10;

// Fonction pour additionner deux nombres
function additionner(a: number, b: number): number {
    return a + b;
}

// Appeler la fonction et afficher le résultat
console.log("Le résultat est : " + additionner(nombre1, nombre2));
```

#### Explication :

1. **Qu'est-ce qu'on fait ici ?**  
   On a deux nombres, 5 et 10, et on veut les additionner.

2. **Pourquoi TypeScript est utile ?**  
   TypeScript nous aide à dire que `nombre1` et `nombre2` sont des nombres. Si on essaye de mettre autre chose, comme du texte, TypeScript nous avertira.

3. **Comment ça marche ?**  
   La fonction `additionner` prend deux nombres (`a` et `b`), les additionne et renvoie le résultat. Ensuite, on affiche ce résultat avec `console.log`.

C'est comme une calculatrice, mais dans un programme !

### 2. Types fondamentaux

#### Types primitifs

Voici les types primitifs les plus courants en TypeScript :

- **`boolean`** : Représente une valeur vraie ou fausse.  
    Exemple :  
    ```typescript
    let estActif: boolean = true;
    ```

- **`number`** : Représente des nombres (entiers ou flottants).  
    Exemple :  
    ```typescript
    let age: number = 25;
    ```

- **`string`** : Représente des chaînes de caractères.  
    Exemple :  
    ```typescript
    let nom: string = "Alice";
    ```

- **`void`** : Utilisé pour les fonctions qui ne retournent rien.  
    Exemple :  
    ```typescript
    function saluer(): void {
            console.log("Bonjour !");
    }
    ```

- **`undefined`** et **`null`** : Représentent des valeurs non définies ou nulles.  
    Exemple :  
    ```typescript
    let valeurIndefinie: undefined = undefined;
    let valeurNulle: null = null;
    ```

#### Autres types

- **`any`** : Permet de stocker n'importe quel type de valeur. À utiliser avec précaution.  
    Exemple :  
    ```typescript
    let variable: any = "texte";
    variable = 42; // Pas d'erreur
    ```

- **`object`** : Représente des objets non primitifs.  
    Exemple :  
    ```typescript
    let personne: object = { nom: "Alice", age: 25 };
    ```

- **`unknown`** : Similaire à `any`, mais impose une vérification de type avant utilisation.  
    Exemple :  
    ```typescript
    let valeurInconnue: unknown = "texte";
    if (typeof valeurInconnue === "string") {
            console.log(valeurInconnue.toUpperCase());
    }
    ```

- **`never`** : Représente des valeurs qui ne se produisent jamais (par exemple, une fonction qui lève toujours une erreur).  
    Exemple :  
    ```typescript
    function erreur(message: string): never {
            throw new Error(message);
    }
    ```

    ### 3. Types complexes

    #### Objets

    - **Interfaces** : Permettent de définir la structure d'un objet.  
        Exemple :  
        ```typescript
        interface Personne {
            nom: string;
            age: number;
        }

        let utilisateur: Personne = { nom: "Alice", age: 25 };
        ```

    - **Classes** : Utilisées pour créer des objets avec des propriétés et des méthodes.  
        Exemple :  
        ```typescript
        class Animal {
            nom: string;

            constructor(nom: string) {
                this.nom = nom;
            }

            parler(): void {
                console.log(`${this.nom} fait un bruit.`);
            }
        }

        let chien = new Animal("Chien");
        chien.parler();
        ```

    - **Énumérations** : Permettent de définir un ensemble de valeurs nommées.  
        Exemple :  
        ```typescript
        enum Couleur {
            Rouge,
            Vert,
            Bleu
        }

        let maCouleur: Couleur = Couleur.Vert;
        ```

    - **Tableaux** : Représentent une collection de valeurs du même type.  
        Exemple :  
        ```typescript
        let nombres: number[] = [1, 2, 3];
        ```

    - **Tuples** : Représentent un tableau avec un nombre fixe d'éléments de types spécifiques.  
        Exemple :  
        ```typescript
        let tuple: [string, number] = ["Alice", 25];
        ```

    #### Combinaison de types

    - **Unions** : Permettent de combiner plusieurs types possibles pour une variable.  
        Exemple :  
        ```typescript
        let identifiant: string | number;
        identifiant = "123";
        identifiant = 123;
        ```

    - **Intersections** : Permettent de combiner plusieurs types en un seul.  
        Exemple :  
        ```typescript
        interface A {
            propA: string;
        }

        interface B {
            propB: number;
        }

        type AB = A & B;

        let objet: AB = { propA: "texte", propB: 42 };
        ```

    - **Alias de types** : Permettent de donner un nom à un type complexe.  
        Exemple :  
        ```typescript
        type Point = { x: number; y: number };

        let coordonnees: Point = { x: 10, y: 20 };
        ```

        ### 4. Fonctions en TypeScript

        #### Typage des fonctions

        En TypeScript, on peut spécifier les types des paramètres et du retour d'une fonction.

        Exemple :  
        ```typescript
        function multiplier(a: number, b: number): number {
            return a * b;
        }

        let resultat = multiplier(3, 4); // Retourne 12
        ```

        #### Surcharge de fonctions

        TypeScript permet de définir plusieurs signatures pour une même fonction. Cela s'appelle la surcharge de fonctions.

        Exemple :  
        ```typescript
        function concatener(a: string, b: string): string;
        function concatener(a: number, b: number): number;
        function concatener(a: any, b: any): any {
            return a + b;
        }

        let texte = concatener("Bonjour, ", "monde !"); // Retourne "Bonjour, monde !"
        let somme = concatener(10, 20); // Retourne 30
        ```

        La surcharge permet de définir des comportements différents en fonction des types des arguments.
        ### 5. Contrôle de type et inférence

        #### Type Guards / Narrowing

        TypeScript permet de restreindre les types possibles d'une variable grâce à des gardes de type (Type Guards). Cela inclut l'utilisation de `typeof`, `instanceof` et des prédicats de type.

        Exemple avec `typeof` :  
        ```typescript
        function afficherValeur(valeur: string | number): void {
            if (typeof valeur === "string") {
                console.log("C'est une chaîne de caractères : " + valeur.toUpperCase());
            } else {
                console.log("C'est un nombre : " + (valeur * 2));
            }
        }
        ```

        Exemple avec `instanceof` :  
        ```typescript
        class Animal {
            nom: string;
            constructor(nom: string) {
                this.nom = nom;
            }
        }

        class Chien extends Animal {
            aboyer(): void {
                console.log("Woof !");
            }
        }

        function verifierAnimal(animal: Animal): void {
            if (animal instanceof Chien) {
                animal.aboyer();
            } else {
                console.log(`${animal.nom} n'est pas un chien.`);
            }
        }
        ```

        Exemple avec un prédicat de type :  
        ```typescript
        function estNombre(valeur: unknown): valeur is number {
            return typeof valeur === "number";
        }

        function traiterValeur(valeur: unknown): void {
            if (estNombre(valeur)) {
                console.log("C'est un nombre : " + (valeur * 2));
            } else {
                console.log("Ce n'est pas un nombre.");
            }
        }
        ```

        #### Inférence et compatibilité

        TypeScript peut déduire automatiquement les types des variables et des fonctions, ce qui simplifie le code tout en maintenant la sécurité des types.

        Exemple d'inférence de type :  
        ```typescript
        let message = "Bonjour"; // TypeScript déduit que `message` est de type `string`
        ```

        Exemple de compatibilité des types :  
        ```typescript
        let valeur: string | number = "texte";
        valeur = 42; // Pas d'erreur, car `valeur` peut être un `string` ou un `number`
        ```

        L'inférence et la compatibilité des types permettent d'écrire du code plus concis tout en bénéficiant des avantages du typage statique.

    ### 6. Programmation orientée objet

    #### Classes et interfaces

    En TypeScript, les classes et les interfaces sont des éléments clés de la programmation orientée objet.

    - **Déclaration de classes** :  
        Exemple :  
        ```typescript
        class Personne {
            nom: string;
            age: number;

            constructor(nom: string, age: number) {
                this.nom = nom;
                this.age = age;
            }

            saluer(): void {
                console.log(`Bonjour, je m'appelle ${this.nom} et j'ai ${this.age} ans.`);
            }
        }

        let utilisateur = new Personne("Alice", 25);
        utilisateur.saluer();
        ```

    - **Héritage** :  
        Exemple :  
        ```typescript
        class Employe extends Personne {
            poste: string;

            constructor(nom: string, age: number, poste: string) {
                super(nom, age);
                this.poste = poste;
            }

            afficherPoste(): void {
                console.log(`Je suis ${this.poste}.`);
            }
        }

        let employe = new Employe("Bob", 30, "Développeur");
        employe.saluer();
        employe.afficherPoste();
        ```

    - **Polymorphisme** :  
        Exemple :  
        ```typescript
        class Animal {
            parler(): void {
                console.log("L'animal fait un bruit.");
            }
        }

        class Chat extends Animal {
            parler(): void {
                console.log("Le chat miaule.");
            }
        }

        class Chien extends Animal {
            parler(): void {
                console.log("Le chien aboie.");
            }
        }

        let animaux: Animal[] = [new Chat(), new Chien()];
        animaux.forEach(animal => animal.parler());
        ```

    #### Modificateurs d'accès

    TypeScript propose trois modificateurs d'accès pour les membres des classes :

    - **`public`** : Accessible partout (par défaut).  
    - **`private`** : Accessible uniquement dans la classe où il est défini.  
    - **`protected`** : Accessible dans la classe où il est défini et dans ses sous-classes.

    Exemple :  
    ```typescript
    class CompteBancaire {
        private solde: number;

        constructor(soldeInitial: number) {
            this.solde = soldeInitial;
        }

        public deposer(montant: number): void {
            this.solde += montant;
        }

        public afficherSolde(): void {
            console.log(`Solde : ${this.solde}€`);
        }
    }

    let compte = new CompteBancaire(100);
    compte.deposer(50);
    compte.afficherSolde();
    ```

    #### Classes abstraites et surcharge de constructeurs

    - **Classes abstraites** : Une classe abstraite ne peut pas être instanciée directement. Elle sert de modèle pour d'autres classes.  
        Exemple :  
        ```typescript
        abstract class Forme {
            abstract aire(): number;

            afficherAire(): void {
                console.log(`L'aire est : ${this.aire()}`);
            }
        }

        class Cercle extends Forme {
            rayon: number;

            constructor(rayon: number) {
                super();
                this.rayon = rayon;
            }

            aire(): number {
                return Math.PI * this.rayon * this.rayon;
            }
        }

        let cercle = new Cercle(5);
        cercle.afficherAire();
        ```

    - **Surcharge de constructeurs** : TypeScript permet de définir plusieurs signatures pour un constructeur.  
        Exemple :  
        ```typescript
        class Point {
            x: number;
            y: number;

            constructor(x: number);
            constructor(x: number, y: number);
            constructor(x: number, y?: number) {
                this.x = x;
                this.y = y ?? 0;
            }

            afficher(): void {
                console.log(`Point(${this.x}, ${this.y})`);
            }
        }

        let p1 = new Point(5);
        let p2 = new Point(5, 10);

        p1.afficher();
        p2.afficher();
        ```


        ### 7. Types avancés

        #### Types utilitaires

        TypeScript propose plusieurs types utilitaires pour manipuler et transformer les types existants :

        - **`Partial<T>`** : Rend toutes les propriétés d'un type optionnelles.  
            Exemple :  
            ```typescript
            interface Utilisateur {
                nom: string;
                age: number;
            }

            let utilisateurPartiel: Partial<Utilisateur> = { nom: "Alice" };
            ```

        - **`Pick<T, K>`** : Sélectionne un sous-ensemble de propriétés d'un type.  
            Exemple :  
            ```typescript
            interface Utilisateur {
                nom: string;
                age: number;
                email: string;
            }

            let utilisateurSimplifie: Pick<Utilisateur, "nom" | "email"> = { nom: "Alice", email: "alice@example.com" };
            ```

        - **`Omit<T, K>`** : Exclut certaines propriétés d'un type.  
            Exemple :  
            ```typescript
            interface Utilisateur {
                nom: string;
                age: number;
                email: string;
            }

            let utilisateurSansEmail: Omit<Utilisateur, "email"> = { nom: "Alice", age: 25 };
            ```

        - **`Readonly<T>`** : Rend toutes les propriétés d'un type immuables.  
            Exemple :  
            ```typescript
            interface Utilisateur {
                nom: string;
                age: number;
            }

            let utilisateurReadonly: Readonly<Utilisateur> = { nom: "Alice", age: 25 };
            // utilisateurReadonly.nom = "Bob"; // Erreur : la propriété est en lecture seule
            ```

        - **`Record<K, T>`** : Crée un type d'objet avec des clés de type `K` et des valeurs de type `T`.  
            Exemple :  
            ```typescript
            let dictionnaire: Record<string, number> = { a: 1, b: 2, c: 3 };
            ```

        - **`Exclude<T, U>`** : Exclut de `T` les types assignables à `U`.  
            Exemple :  
            ```typescript
            type SansString = Exclude<string | number | boolean, string>; // Résultat : number | boolean
            ```

        - **`Extract<T, U>`** : Extrait de `T` les types assignables à `U`.  
            Exemple :  
            ```typescript
            type SeulementString = Extract<string | number | boolean, string>; // Résultat : string
            ```

        - **`NonNullable<T>`** : Exclut `null` et `undefined` d'un type.  
            Exemple :  
            ```typescript
            type SansNull = NonNullable<string | null | undefined>; // Résultat : string
            ```

        - **`Parameters<T>`** : Extrait les types des paramètres d'une fonction.  
            Exemple :  
            ```typescript
            type Parametres = Parameters<(a: string, b: number) => void>; // Résultat : [string, number]
            ```

        - **`ReturnType<T>`** : Extrait le type de retour d'une fonction.  
            Exemple :  
            ```typescript
            type Retour = ReturnType<() => string>; // Résultat : string
            ```

        - **`InstanceType<T>`** : Extrait le type d'instance d'une classe ou d'un constructeur.  
            Exemple :  
            ```typescript
            class Personne {
                nom: string = "Alice";
            }

            type InstancePersonne = InstanceType<typeof Personne>; // Résultat : Personne
            ```

        - **`Awaited<T>`** : Extrait le type de la valeur résolue d'une promesse.  
            Exemple :  
            ```typescript
            type ValeurPromise = Awaited<Promise<string>>; // Résultat : string
            ```

        #### Types conditionnels et mappés

        - **Types conditionnels** : Permettent de créer des types dynamiques en fonction d'une condition.  
            Exemple :  
            ```typescript
            type EstString<T> = T extends string ? true : false;

            type Test1 = EstString<string>; // Résultat : true
            type Test2 = EstString<number>; // Résultat : false
            ```

        - **Types mappés** : Permettent de transformer les propriétés d'un type.  
            Exemple :  
            ```typescript
            type Readonly<T> = {
                [P in keyof T]: T[P];
            };

            interface Utilisateur {
                nom: string;
                age: number;
            }

            type UtilisateurReadonly = Readonly<Utilisateur>;
            ```

        #### Types littéraux et récursifs

        - **Types littéraux** : Permettent de restreindre une variable à des valeurs spécifiques.  
            Exemple :  
            ```typescript
            type Couleur = "rouge" | "vert" | "bleu";

            let maCouleur: Couleur = "rouge";
            ```

        - **Types récursifs** : Permettent de définir des structures de données complexes comme des arbres ou des listes imbriquées.  
            Exemple :  
            ```typescript
            type Arbre<T> = {
                valeur: T;
                enfants?: Arbre<T>[];
            };

            let monArbre: Arbre<number> = {
                valeur: 1,
                enfants: [
                    { valeur: 2 },
                    { valeur: 3, enfants: [{ valeur: 4 }] }
                ]
            };
            ```

            ### 8. Génériques

            #### Types génériques

            Les types génériques permettent de créer des composants réutilisables en acceptant des types comme paramètres. Cela permet d'écrire du code flexible et fortement typé.

            Exemple :  
            ```typescript
            function identite<T>(valeur: T): T {
                return valeur;
            }

            let nombre = identite<number>(42); // Retourne 42
            let texte = identite<string>("Bonjour"); // Retourne "Bonjour"
            ```

            Dans cet exemple, la fonction `identite` peut accepter n'importe quel type grâce au paramètre générique `T`.

            #### Contraintes génériques

            On peut restreindre les types acceptés par un générique en utilisant des contraintes.

            Exemple :  
            ```typescript
            interface AvecLongueur {
                longueur: number;
            }

            function afficherLongueur<T extends AvecLongueur>(element: T): void {
                console.log(`Longueur : ${element.longueur}`);
            }

            afficherLongueur({ longueur: 10 }); // Fonctionne
            // afficherLongueur(42); // Erreur : le type 'number' n'a pas de propriété 'longueur'
            ```

            Ici, le générique `T` est contraint par l'interface `AvecLongueur`, ce qui garantit que l'argument passé possède une propriété `longueur`.

            Les génériques permettent de créer des fonctions, des classes et des interfaces réutilisables tout en maintenant la sécurité des types.


            ### 9. Décorateurs

            #### Utilisation des décorateurs

            Les décorateurs sont une fonctionnalité avancée de TypeScript qui permet d'ajouter des métadonnées ou de modifier le comportement des classes, méthodes, propriétés ou paramètres.

            Pour utiliser les décorateurs, il faut activer l'option `experimentalDecorators` dans le fichier `tsconfig.json` :

            ```json
            {
                "compilerOptions": {
                    "experimentalDecorators": true
                }
            }
            ```

            #### Exemple : Décorateur de classe

            Un décorateur de classe est une fonction qui prend la classe comme argument et peut modifier ou étendre son comportement.

            Exemple :  
            ```typescript
            function Journalisation(construction: Function) {
                console.log(`Classe créée : ${construction.name}`);
            }

            @Journalisation
            class Personne {
                constructor(public nom: string) {}
            }

            let utilisateur = new Personne("Alice");
            // Affiche : "Classe créée : Personne"
            ```

            #### Exemple : Décorateur de méthode

            Un décorateur de méthode peut être utilisé pour modifier ou intercepter l'exécution d'une méthode.

            Exemple :  
            ```typescript
            function Chronometrer(
                cible: any,
                nomMethode: string,
                descripteur: PropertyDescriptor
            ) {
                const methodeOriginale = descripteur.value;

                descripteur.value = function (...args: any[]) {
                    console.time(nomMethode);
                    const resultat = methodeOriginale.apply(this, args);
                    console.timeEnd(nomMethode);
                    return resultat;
                };
            }

            class Calculatrice {
                @Chronometrer
                additionner(a: number, b: number): number {
                    return a + b;
                }
            }

            let calc = new Calculatrice();
            calc.additionner(5, 10);
            // Affiche le temps d'exécution de la méthode "additionner"
            ```

            #### Exemple : Décorateur de propriété

            Un décorateur de propriété peut être utilisé pour ajouter des métadonnées ou valider les valeurs d'une propriété.

            Exemple :  
            ```typescript
            function MinValeur(min: number) {
                return function (cible: any, nomPropriete: string) {
                    let valeur: number;

                    const getter = () => valeur;
                    const setter = (nouvelleValeur: number) => {
                        if (nouvelleValeur < min) {
                            throw new Error(`La valeur de ${nomPropriete} doit être au moins ${min}`);
                        }
                        valeur = nouvelleValeur;
                    };

                    Object.defineProperty(cible, nomPropriete, {
                        get: getter,
                        set: setter,
                    });
                };
            }

            class Produit {
                @MinValeur(10)
                prix: number;

                constructor(prix: number) {
                    this.prix = prix;
                }
            }

            let produit = new Produit(20); // Fonctionne
            // produit.prix = 5; // Erreur : La valeur de prix doit être au moins 10
            ```

            #### Exemple : Décorateur de paramètre

            Un décorateur de paramètre peut être utilisé pour ajouter des métadonnées sur les paramètres d'une méthode.

            Exemple :  
            ```typescript
            function ParametreJournalisation(cible: any, nomMethode: string, indexParam: number) {
                console.log(`Paramètre journalisé : ${nomMethode}, index ${indexParam}`);
            }

            class Service {
                saluer(@ParametreJournalisation nom: string): void {
                    console.log(`Bonjour, ${nom}`);
                }
            }

            let service = new Service();
            service.saluer("Alice");
            // Affiche : "Paramètre journalisé : saluer, index 0"
            ```

            Les décorateurs permettent d'ajouter des fonctionnalités puissantes et modulaires à votre code TypeScript.

            ### 10. Modules et espaces de noms

            #### Modules

            Les modules permettent d'organiser le code en plusieurs fichiers et de contrôler ce qui est exposé à d'autres parties de l'application.

            - **Exportation** : On peut exporter des variables, fonctions, classes ou interfaces pour les rendre accessibles dans d'autres fichiers.  
                Exemple :  
                ```typescript
                // fichier math.ts
                export function addition(a: number, b: number): number {
                        return a + b;
                }
                ```

            - **Importation** : On peut importer des éléments exportés dans d'autres fichiers.  
                Exemple :  
                ```typescript
                // fichier app.ts
                import { addition } from "./math";

                console.log(addition(5, 10)); // Affiche 15
                ```

            - **Exportation par défaut** : Permet d'exporter un élément par défaut.  
                Exemple :  
                ```typescript
                // fichier utils.ts
                export default function saluer(nom: string): void {
                        console.log(`Bonjour, ${nom}`);
                }
                ```

                ```typescript
                // fichier app.ts
                import saluer from "./utils";

                saluer("Alice"); // Affiche "Bonjour, Alice"
                ```

            #### Espaces de noms

            Les espaces de noms (ou namespaces) permettent d'organiser le code en regroupant des éléments sous un même nom.

            - **Déclaration d'un espace de noms** :  
                Exemple :  
                ```typescript
                namespace Geometrie {
                        export function aireCarre(cote: number): number {
                                return cote * cote;
                        }

                        export function aireRectangle(longueur: number, largeur: number): number {
                                return longueur * largeur;
                        }
                }

                console.log(Geometrie.aireCarre(5)); // Affiche 25
                console.log(Geometrie.aireRectangle(10, 5)); // Affiche 50
                ```

            - **Espaces de noms imbriqués** :  
                Exemple :  
                ```typescript
                namespace MathUtils {
                        export namespace Trigo {
                                export function sinus(angle: number): number {
                                        return Math.sin(angle);
                                }
                        }
                }

                console.log(MathUtils.Trigo.sinus(Math.PI / 2)); // Affiche 1
                ```

            #### Augmentation de modules

            TypeScript permet d'étendre des modules existants en ajoutant de nouvelles fonctionnalités.

            - **Exemple d'augmentation de module** :  
                ```typescript
                // fichier original.ts
                export class Utilisateur {
                        constructor(public nom: string) {}
                }

                // fichier augmentation.ts
                import { Utilisateur } from "./original";

                declare module "./original" {
                        interface Utilisateur {
                                saluer(): void;
                        }
                }

                Utilisateur.prototype.saluer = function () {
                        console.log(`Bonjour, je suis ${this.nom}`);
                };

                const utilisateur = new Utilisateur("Alice");
                utilisateur.saluer(); // Affiche "Bonjour, je suis Alice"
                ```

            Les modules et espaces de noms permettent de structurer et de maintenir un code TypeScript propre et modulaire.


            ### 11. Configuration et outils

            #### Options du compilateur

            Le fichier `tsconfig.json` permet de configurer le compilateur TypeScript. Voici un exemple de configuration de base :

            ```json
            {
                "compilerOptions": {
                    "target": "ES6", // Version de JavaScript cible
                    "module": "commonjs", // Système de modules
                    "strict": true, // Active les vérifications strictes
                    "outDir": "./dist", // Répertoire de sortie
                    "rootDir": "./src", // Répertoire source
                    "esModuleInterop": true // Compatibilité avec les modules ES
                },
                "include": ["src/**/*"], // Fichiers inclus
                "exclude": ["node_modules"] // Fichiers exclus
            }
            ```

            #### Outils de compilation

            - **`tsc`** : Le compilateur TypeScript. Compile les fichiers `.ts` en `.js`.
                Exemple :
                ```bash
                tsc
                ```

            - **`ts-node`** : Permet d'exécuter directement du code TypeScript sans le compiler en JavaScript.
                Exemple :
                ```bash
                ts-node fichier.ts
                ```

        ### 12. Écosystème et bonnes pratiques

        #### Packages utiles

        Voici quelques bibliothèques et outils populaires dans l'écosystème TypeScript :

        - **`lodash`** : Fournit des utilitaires pour manipuler des tableaux, objets, chaînes, etc.  
            Exemple :  
            ```typescript
            import _ from "lodash";

            const tableau = [1, 2, 3, 4];
            console.log(_.shuffle(tableau)); // Mélange les éléments du tableau
            ```

        - **`axios`** : Client HTTP pour effectuer des requêtes API.  
            Exemple :  
            ```typescript
            import axios from "axios";

            axios.get("https://api.example.com/data").then(response => {
                console.log(response.data);
            });
            ```

        - **`class-transformer`** : Permet de transformer des objets en instances de classes.  
            Exemple :  
            ```typescript
            import { plainToClass } from "class-transformer";

            class Utilisateur {
                nom: string;
                age: number;
            }

            const donnees = { nom: "Alice", age: 25 };
            const utilisateur = plainToClass(Utilisateur, donnees);
            console.log(utilisateur instanceof Utilisateur); // true
            ```

        - **`jest`** : Framework de tests pour écrire et exécuter des tests unitaires.  
            Exemple :  
            ```typescript
            test("addition", () => {
                expect(1 + 2).toBe(3);
            });
            ```

        #### Linting et formatage

        Pour maintenir un code propre et cohérent, utilisez des outils de linting et de formatage :

        - **`ESLint`** : Analyse statique pour détecter les problèmes dans le code.  
            Exemple de configuration (`.eslintrc.json`) :  
            ```json
            {
                "extends": ["eslint:recommended", "plugin:@typescript-eslint/recommended"],
                "parser": "@typescript-eslint/parser",
                "plugins": ["@typescript-eslint"]
            }
            ```

        - **`Prettier`** : Formateur de code pour garantir un style uniforme.  
            Exemple de configuration (`.prettierrc`) :  
            ```json
            {
                "semi": true,
                "singleQuote": true,
                "trailingComma": "all"
            }
            ```

        - **Intégration ESLint + Prettier** : Combinez les deux outils pour éviter les conflits.  
            Installez les packages nécessaires :  
            ```bash
            npm install eslint-config-prettier eslint-plugin-prettier --save-dev
            ```

            Ajoutez à la configuration ESLint :  
            ```json
            {
                "extends": ["plugin:prettier/recommended"]
            }
            ```

        #### Outils de build

        Automatisez les tâches de développement avec des outils de build :

        - **`webpack`** : Bundler pour regrouper les fichiers TypeScript, CSS, etc.  
            Exemple de configuration (`webpack.config.js`) :  
            ```javascript
            const path = require("path");

            module.exports = {
                entry: "./src/index.ts",
                output: {
                    filename: "bundle.js",
                    path: path.resolve(__dirname, "dist"),
                },
                resolve: {
                    extensions: [".ts", ".js"],
                },
                module: {
                    rules: [
                        {
                            test: /\.ts$/,
                            use: "ts-loader",
                            exclude: /node_modules/,
                        },
                    ],
                },
            };
            ```

        - **`Rollup`** : Alternative légère à Webpack pour les bibliothèques.  
            Exemple de configuration (`rollup.config.js`) :  
            ```javascript
            import typescript from "@rollup/plugin-typescript";

            export default {
                input: "src/index.ts",
                output: {
                    file: "dist/bundle.js",
                    format: "cjs",
                },
                plugins: [typescript()],
            };
            ```

        - **`Parcel`** : Bundler simple et rapide avec configuration minimale.  
            Exemple :  
            ```bash
            parcel index.html
            ```

        En combinant ces outils, vous pouvez améliorer la qualité, la maintenabilité et l'efficacité de vos projets TypeScript.