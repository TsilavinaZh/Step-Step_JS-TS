# Cours React JS
## Introduction
- React est une bibliothèque JavaScript pour construire des interfaces utilisateur.
- Elle est maintenue par Facebook et une communauté de développeurs.
- React permet de créer des applications web dynamiques et réactives.

## Fondations de React (Explications pour enfants)

React, c'est comme des LEGO pour construire des sites web ! Tu peux assembler des petites pièces (appelées composants) pour créer des pages super cool.

### Exemple 1 : Un composant simple
Voici un exemple d'un composant React qui dit "Bonjour !".

```jsx
function Bonjour() {
    return <h1>Bonjour, tout le monde !</h1>;
}
```

Quand tu utilises ce composant, il affiche un joli message sur ton site.

---

### Exemple 2 : Un composant avec des données (props)
Les "props", c'est comme des cadeaux que tu donnes à tes composants. Voici un exemple :

```jsx
function Salutation(props) {
    return <h1>Bonjour, {props.nom} !</h1>;
}

// Utilisation
<Salutation nom="Alice" />
```

Ici, le composant affiche "Bonjour, Alice !" parce qu'on lui a donné "Alice" comme cadeau.

---

Avec React, tu peux créer plein de choses amusantes et dynamiques en combinant ces petites briques !

## Hooks fondamentaux

### useState : Gestion de l'état local
Le hook `useState` permet de gérer l'état dans un composant fonctionnel. Voici un exemple simple :

```jsx
import React, { useState } from 'react';

function Compteur() {
    const [compteur, setCompteur] = useState(0);

    return (
        <div>
            <p>Vous avez cliqué {compteur} fois</p>
            <button onClick={() => setCompteur(compteur + 1)}>
                Cliquez ici
            </button>
        </div>
    );
}
```

### useEffect : Effets secondaires et cycle de vie
Le hook `useEffect` est utilisé pour gérer les effets secondaires, comme les appels API ou la mise à jour du DOM. Exemple :

```jsx
import React, { useState, useEffect } from 'react';

function Horloge() {
    const [heure, setHeure] = useState(new Date());

    useEffect(() => {
        const interval = setInterval(() => {
            setHeure(new Date());
        }, 1000);

        return () => clearInterval(interval); // Nettoyage
    }, []);

    return <h2>Il est {heure.toLocaleTimeString()}.</h2>;
}
```

### Gestion des événements : Interaction utilisateur
Avec React, vous pouvez facilement gérer les événements comme les clics, les saisies clavier, etc. Exemple :

```jsx
function Bouton() {
    function handleClick() {
        alert('Bouton cliqué !');
    }

    return <button onClick={handleClick}>Cliquez-moi</button>;
}
```

### Formulaires : Création et gestion des entrées utilisateur
Les formulaires en React utilisent l'état pour gérer les données saisies. Exemple :

```jsx
import React, { useState } from 'react';

function Formulaire() {
    const [nom, setNom] = useState('');

    function handleSubmit(event) {
        event.preventDefault();
        alert(`Bonjour, ${nom} !`);
    }

    return (
        <form onSubmit={handleSubmit}>
            <label>
                Nom :
                <input
                    type="text"
                    value={nom}
                    onChange={(e) => setNom(e.target.value)}
                />
            </label>
            <button type="submit">Envoyer</button>
        </form>
    );
}
```

Ces hooks et concepts sont essentiels pour construire des applications React modernes et interactives !


## Architecture et bonnes pratiques

### Structure des dossiers
Une bonne organisation des dossiers est essentielle pour maintenir un projet React clair et évolutif. Voici une structure courante :

```
src/
├── components/   # Composants réutilisables
├── pages/        # Pages principales
├── hooks/        # Hooks personnalisés
├── utils/        # Fonctions utilitaires
├── assets/       # Images, styles, etc.
└── App.js        # Composant racine
```

### Réutilisation des composants
Créer des composants modulaires et réutilisables permet de réduire la duplication de code. Par exemple :

```jsx
function Bouton({ texte, onClick }) {
    return <button onClick={onClick}>{texte}</button>;
}

// Réutilisation
<Bouton texte="Envoyer" onClick={handleEnvoyer} />
<Bouton texte="Annuler" onClick={handleAnnuler} />
```

### Composition vs héritage
React privilégie la composition des composants plutôt que l'héritage. Exemple de composition :

```jsx
function Carte({ titre, contenu }) {
    return (
        <div className="carte">
            <h2>{titre}</h2>
            <p>{contenu}</p>
        </div>
    );
}

// Utilisation
<Carte titre="Bienvenue" contenu="Ceci est une carte." />
```

### Gestion des erreurs
Pour gérer les erreurs dans React, vous pouvez utiliser les Error Boundaries. Exemple :

```jsx
import React from 'react';

class ErrorBoundary extends React.Component {
    constructor(props) {
        super(props);
        this.state = { hasError: false };
    }

    static getDerivedStateFromError() {
        return { hasError: true };
    }

    componentDidCatch(error, info) {
        console.error("Erreur capturée :", error, info);
    }

    render() {
        if (this.state.hasError) {
            return <h1>Quelque chose s'est mal passé.</h1>;
        }

        return this.props.children;
    }
}

// Utilisation
<ErrorBoundary>
    <MonComposant />
</ErrorBoundary>
```

Adopter ces bonnes pratiques garantit un code propre, maintenable et évolutif pour vos projets React.


## Hooks avancés et logique personnalisée

### useRef, useMemo, useCallback : Optimisation des performances

#### useRef
Le hook `useRef` permet de créer une référence mutable qui persiste entre les rendus. Exemple :

```jsx
import React, { useRef } from 'react';

function ChampTexte() {
    const inputRef = useRef(null);

    function focusInput() {
        inputRef.current.focus();
    }

    return (
        <div>
            <input ref={inputRef} type="text" />
            <button onClick={focusInput}>Focus</button>
        </div>
    );
}
```

#### useMemo
Le hook `useMemo` mémorise une valeur calculée pour éviter des recalculs inutiles. Exemple :

```jsx
import React, { useState, useMemo } from 'react';

function Calculateur() {
    const [nombre, setNombre] = useState(0);
    const [autre, setAutre] = useState(0);

    const resultat = useMemo(() => {
        console.log('Calcul en cours...');
        return nombre * 2;
    }, [nombre]);

    return (
        <div>
            <input
                type="number"
                value={nombre}
                onChange={(e) => setNombre(Number(e.target.value))}
            />
            <p>Résultat : {resultat}</p>
            <button onClick={() => setAutre(autre + 1)}>Incrémenter autre</button>
        </div>
    );
}
```

#### useCallback
Le hook `useCallback` mémorise une fonction pour éviter de la recréer à chaque rendu. Exemple :

```jsx
import React, { useState, useCallback } from 'react';

function Bouton({ onClick }) {
    console.log('Bouton rendu');
    return <button onClick={onClick}>Cliquez-moi</button>;
}

function Exemple() {
    const [compteur, setCompteur] = useState(0);

    const incrementer = useCallback(() => {
        setCompteur((prev) => prev + 1);
    }, []);

    return (
        <div>
            <p>Compteur : {compteur}</p>
            <Bouton onClick={incrementer} />
        </div>
    );
}
```

---

### useReducer : Gestion d'états complexes
Le hook `useReducer` est utile pour gérer des états complexes avec des actions. Exemple :

```jsx
import React, { useReducer } from 'react';

function reducer(state, action) {
    switch (action.type) {
        case 'increment':
            return { compteur: state.compteur + 1 };
        case 'decrement':
            return { compteur: state.compteur - 1 };
        default:
            throw new Error('Action inconnue');
    }
}

function CompteurAvance() {
    const [state, dispatch] = useReducer(reducer, { compteur: 0 });

    return (
        <div>
            <p>Compteur : {state.compteur}</p>
            <button onClick={() => dispatch({ type: 'increment' })}>+</button>
            <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
        </div>
    );
}
```

---

### Custom Hooks : Création de hooks personnalisés
Les hooks personnalisés permettent de réutiliser la logique entre plusieurs composants. Exemple :

```jsx
import React, { useState, useEffect } from 'react';

function useHorloge() {
    const [heure, setHeure] = useState(new Date());

    useEffect(() => {
        const interval = setInterval(() => {
            setHeure(new Date());
        }, 1000);

        return () => clearInterval(interval);
    }, []);

    return heure;
}

function HorlogePersonnalisee() {
    const heure = useHorloge();

    return <h2>Il est {heure.toLocaleTimeString()}.</h2>;
}
```

Ces hooks avancés et personnalisés permettent d'optimiser vos applications React et de rendre votre code plus réutilisable et performant.



## Écosystème React

### React Router : Navigation et routage
React Router est une bibliothèque permettant de gérer la navigation entre les différentes pages d'une application React. Exemple simple :

```jsx
import React from 'react';
import { BrowserRouter as Router, Route, Routes, Link } from 'react-router-dom';

function Accueil() {
    return <h2>Page d'accueil</h2>;
}

function APropos() {
    return <h2>À propos</h2>;
}

function App() {
    return (
        <Router>
            <nav>
                <Link to="/">Accueil</Link> | <Link to="/apropos">À propos</Link>
            </nav>
            <Routes>
                <Route path="/" element={<Accueil />} />
                <Route path="/apropos" element={<APropos />} />
            </Routes>
        </Router>
    );
}

export default App;
```

### Gestion de l'état global
Pour gérer l'état global dans une application React, plusieurs solutions sont disponibles :

#### Context API
La Context API est intégrée à React et permet de partager des données entre composants sans passer par les props.

```jsx
import React, { createContext, useContext, useState } from 'react';

const ThemeContext = createContext();

function ThemeProvider({ children }) {
    const [theme, setTheme] = useState('clair');

    return (
        <ThemeContext.Provider value={{ theme, setTheme }}>
            {children}
        </ThemeContext.Provider>
    );
}

function BoutonTheme() {
    const { theme, setTheme } = useContext(ThemeContext);

    return (
        <button onClick={() => setTheme(theme === 'clair' ? 'sombre' : 'clair')}>
            Thème actuel : {theme}
        </button>
    );
}

function App() {
    return (
        <ThemeProvider>
            <BoutonTheme />
        </ThemeProvider>
    );
}

export default App;
```

#### Redux
Redux est une bibliothèque populaire pour gérer des états complexes dans des applications React.

```bash
npm install @reduxjs/toolkit react-redux
```

Exemple avec Redux Toolkit :

```jsx
import { configureStore, createSlice } from '@reduxjs/toolkit';
import { Provider, useDispatch, useSelector } from 'react-redux';

const compteurSlice = createSlice({
    name: 'compteur',
    initialState: { valeur: 0 },
    reducers: {
        increment: (state) => { state.valeur += 1; },
        decrement: (state) => { state.valeur -= 1; },
    },
});

const store = configureStore({ reducer: { compteur: compteurSlice.reducer } });

function Compteur() {
    const valeur = useSelector((state) => state.compteur.valeur);
    const dispatch = useDispatch();

    return (
        <div>
            <p>Compteur : {valeur}</p>
            <button onClick={() => dispatch(compteurSlice.actions.increment())}>+</button>
            <button onClick={() => dispatch(compteurSlice.actions.decrement())}>-</button>
        </div>
    );
}

function App() {
    return (
        <Provider store={store}>
            <Compteur />
        </Provider>
    );
}

export default App;
```

#### Zustand
Zustand est une alternative légère à Redux pour gérer l'état global.

```bash
npm install zustand
```

Exemple :

```jsx
import create from 'zustand';

const useStore = create((set) => ({
    compteur: 0,
    increment: () => set((state) => ({ compteur: state.compteur + 1 })),
    decrement: () => set((state) => ({ compteur: state.compteur - 1 })),
}));

function Compteur() {
    const { compteur, increment, decrement } = useStore();

    return (
        <div>
            <p>Compteur : {compteur}</p>
            <button onClick={increment}>+</button>
            <button onClick={decrement}>-</button>
        </div>
    );
}

export default Compteur;
```

### Requêtes HTTP
Pour effectuer des requêtes HTTP dans React, vous pouvez utiliser des bibliothèques comme Fetch, Axios ou TanStack Query.

#### Fetch
Fetch est une API native pour effectuer des requêtes HTTP.

```jsx
import React, { useState, useEffect } from 'react';

function Donnees() {
    const [data, setData] = useState([]);

    useEffect(() => {
        fetch('https://jsonplaceholder.typicode.com/posts')
            .then((response) => response.json())
            .then((data) => setData(data));
    }, []);

    return (
        <ul>
            {data.map((item) => (
                <li key={item.id}>{item.title}</li>
            ))}
        </ul>
    );
}

export default Donnees;
```

#### Axios
Axios est une bibliothèque populaire pour effectuer des requêtes HTTP.

```bash
npm install axios
```

Exemple :

```jsx
import React, { useState, useEffect } from 'react';
import axios from 'axios';

function Donnees() {
    const [data, setData] = useState([]);

    useEffect(() => {
        axios.get('https://jsonplaceholder.typicode.com/posts')
            .then((response) => setData(response.data));
    }, []);

    return (
        <ul>
            {data.map((item) => (
                <li key={item.id}>{item.title}</li>
            ))}
        </ul>
    );
}

export default Donnees;
```

#### TanStack Query
TanStack Query (anciennement React Query) est une bibliothèque puissante pour gérer les requêtes et le cache.

```bash
npm install @tanstack/react-query
```

Exemple :

```jsx
import React from 'react';
import { useQuery, QueryClient, QueryClientProvider } from '@tanstack/react-query';

const queryClient = new QueryClient();

function Donnees() {
    const { data, isLoading } = useQuery(['posts'], async () => {
        const response = await fetch('https://jsonplaceholder.typicode.com/posts');
        return response.json();
    });

    if (isLoading) return <p>Chargement...</p>;

    return (
        <ul>
            {data.map((item) => (
                <li key={item.id}>{item.title}</li>
            ))}
        </ul>
    );
}

function App() {
    return (
        <QueryClientProvider client={queryClient}>
            <Donnees />
        </QueryClientProvider>
    );
}

export default App;
```

Ces outils de l'écosystème React permettent de construire des applications robustes et performantes.


## Styling et composants UI

### CSS Modules, Styled Components, Tailwind CSS

#### CSS Modules
CSS Modules permettent de scoper les styles localement à un composant. Exemple :

```css
/* styles.module.css */
.bouton {
    background-color: blue;
    color: white;
    padding: 10px;
    border: none;
    border-radius: 5px;
}
```

```jsx
import styles from './styles.module.css';

function Bouton() {
    return <button className={styles.bouton}>Cliquez-moi</button>;
}
```

#### Styled Components
Styled Components est une bibliothèque pour écrire du CSS dans vos fichiers JavaScript. Exemple :

```bash
npm install styled-components
```

```jsx
import styled from 'styled-components';

const Bouton = styled.button`
    background-color: blue;
    color: white;
    padding: 10px;
    border: none;
    border-radius: 5px;
`;

function App() {
    return <Bouton>Cliquez-moi</Bouton>;
}
```

#### Tailwind CSS
Tailwind CSS est un framework utilitaire pour styliser rapidement vos composants. Exemple :

```bash
npm install -D tailwindcss
npx tailwindcss init
```

```jsx
function Bouton() {
    return <button className="bg-blue-500 text-white py-2 px-4 rounded">Cliquez-moi</button>;
}
```

### Bibliothèques UI

#### Chakra UI
Chakra UI est une bibliothèque de composants accessibles et personnalisables.

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

```jsx
import { Button } from '@chakra-ui/react';

function App() {
    return <Button colorScheme="blue">Cliquez-moi</Button>;
}
```

#### Material UI
Material UI propose des composants suivant les guidelines de Material Design.

```bash
npm install @mui/material @emotion/react @emotion/styled
```

```jsx
import Button from '@mui/material/Button';

function App() {
    return <Button variant="contained" color="primary">Cliquez-moi</Button>;
}
```

#### Ant Design
Ant Design est une bibliothèque populaire pour les applications professionnelles.

```bash
npm install antd
```

```jsx
import { Button } from 'antd';

function App() {
    return <Button type="primary">Cliquez-moi</Button>;
}
```

### Accessibilité (a11y)
Pour rendre votre application accessible, suivez ces pratiques :

- **Utilisez des balises sémantiques** : `<header>`, `<main>`, `<footer>`, etc.
- **Ajoutez des attributs ARIA** : Exemple : `aria-label`, `role`.
- **Gérez le focus** : Assurez-vous que les éléments interactifs sont accessibles via le clavier.
- **Testez avec des outils** : Utilisez des outils comme Lighthouse ou axe pour vérifier l'accessibilité.

Exemple d'un bouton accessible :

```jsx
function BoutonAccessible() {
    return <button aria-label="Envoyer le formulaire">Envoyer</button>;
}
```

Ces techniques et outils garantissent une application stylée, moderne et accessible.


## Tests et performances

### Tests unitaires et d'intégration
Les tests sont essentiels pour garantir la qualité et la stabilité de votre application. Voici quelques outils populaires :

#### Jest
Jest est un framework de test JavaScript complet et facile à configurer.

```bash
npm install --save-dev jest
```

Exemple de test unitaire avec Jest :

```jsx
// addition.js
export function addition(a, b) {
    return a + b;
}

// addition.test.js
import { addition } from './addition';

test('addition de 2 et 3 donne 5', () => {
    expect(addition(2, 3)).toBe(5);
});
```

#### React Testing Library
React Testing Library est utilisée pour tester les composants React de manière accessible.

```bash
npm install --save-dev @testing-library/react
```

Exemple :

```jsx
import { render, screen } from '@testing-library/react';
import '@testing-library/jest-dom';
import Bouton from './Bouton';

test('affiche le texte du bouton', () => {
    render(<Bouton texte="Cliquez-moi" />);
    expect(screen.getByText('Cliquez-moi')).toBeInTheDocument();
});
```

#### Cypress
Cypress est un outil puissant pour les tests d'intégration et end-to-end.

```bash
npm install --save-dev cypress
```

Exemple de test :

```javascript
describe('Page d\'accueil', () => {
    it('affiche le titre', () => {
        cy.visit('/');
        cy.contains('Bienvenue sur notre site');
    });
});
```

---

### Optimisation des performances

#### Lazy Loading
Le lazy loading permet de charger les composants ou ressources uniquement lorsqu'ils sont nécessaires.

```jsx
import React, { Suspense } from 'react';

const ComposantLourd = React.lazy(() => import('./ComposantLourd'));

function App() {
    return (
        <Suspense fallback={<div>Chargement...</div>}>
            <ComposantLourd />
        </Suspense>
    );
}
```

#### Code Splitting
Le code splitting divise votre application en bundles plus petits pour améliorer les temps de chargement.

```jsx
import { lazy, Suspense } from 'react';

const Page = lazy(() => import('./Page'));

function App() {
    return (
        <Suspense fallback={<div>Chargement...</div>}>
            <Page />
        </Suspense>
    );
}
```

#### Suspense
React Suspense permet de gérer le rendu asynchrone de composants.

---

### Analyse des performances

#### Profiler
Le Profiler de React permet de mesurer les performances des composants.

```jsx
import React, { Profiler } from 'react';

function onRenderCallback(
    id, // Nom du composant
    phase, // "mount" ou "update"
    actualDuration, // Temps réel de rendu
    baseDuration, // Durée estimée sans mémoisation
    startTime, // Début du rendu
    commitTime, // Fin du rendu
    interactions // Interactions déclenchées
) {
    console.log({ id, phase, actualDuration });
}

function App() {
    return (
        <Profiler id="App" onRender={onRenderCallback}>
            <MonComposant />
        </Profiler>
    );
}
```

Ces outils et techniques permettent de tester et d'optimiser efficacement vos applications React.

## Tests et performances

### Tests unitaires et d'intégration
Les tests sont essentiels pour garantir la qualité et la stabilité de votre application. Voici quelques outils populaires :

#### Jest
Jest est un framework de test JavaScript complet et facile à configurer.

```bash
npm install --save-dev jest
```

Exemple de test unitaire avec Jest :

```jsx
// addition.js
export function addition(a, b) {
    return a + b;
}

// addition.test.js
import { addition } from './addition';

test('addition de 2 et 3 donne 5', () => {
    expect(addition(2, 3)).toBe(5);
});
```

#### React Testing Library
React Testing Library est utilisée pour tester les composants React de manière accessible.

```bash
npm install --save-dev @testing-library/react
```

Exemple :

```jsx
import { render, screen } from '@testing-library/react';
import '@testing-library/jest-dom';
import Bouton from './Bouton';

test('affiche le texte du bouton', () => {
    render(<Bouton texte="Cliquez-moi" />);
    expect(screen.getByText('Cliquez-moi')).toBeInTheDocument();
});
```

#### Cypress
Cypress est un outil puissant pour les tests d'intégration et end-to-end.

```bash
npm install --save-dev cypress
```

Exemple de test :

```javascript
describe('Page d\'accueil', () => {
    it('affiche le titre', () => {
        cy.visit('/');
        cy.contains('Bienvenue sur notre site');
    });
});
```

---

### Optimisation des performances

#### Lazy Loading
Le lazy loading permet de charger les composants ou ressources uniquement lorsqu'ils sont nécessaires.

```jsx
import React, { Suspense } from 'react';

const ComposantLourd = React.lazy(() => import('./ComposantLourd'));

function App() {
    return (
        <Suspense fallback={<div>Chargement...</div>}>
            <ComposantLourd />
        </Suspense>
    );
}
```

#### Code Splitting
Le code splitting divise votre application en bundles plus petits pour améliorer les temps de chargement.

```jsx
import { lazy, Suspense } from 'react';

const Page = lazy(() => import('./Page'));

function App() {
    return (
        <Suspense fallback={<div>Chargement...</div>}>
            <Page />
        </Suspense>
    );
}
```

#### Suspense
React Suspense permet de gérer le rendu asynchrone de composants.

---

### Analyse des performances

#### Profiler
Le Profiler de React permet de mesurer les performances des composants.

```jsx
import React, { Profiler } from 'react';

function onRenderCallback(
    id, // Nom du composant
    phase, // "mount" ou "update"
    actualDuration, // Temps réel de rendu
    baseDuration, // Durée estimée sans mémoisation
    startTime, // Début du rendu
    commitTime, // Fin du rendu
    interactions // Interactions déclenchées
) {
    console.log({ id, phase, actualDuration });
}

function App() {
    return (
        <Profiler id="App" onRender={onRenderCallback}>
            <MonComposant />
        </Profiler>
    );
}
```

Ces outils et techniques permettent de tester et d'optimiser efficacement vos applications React.