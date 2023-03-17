# Titre de la compétence

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- l'état (_state_) pour contrôler l'affichage d'un composant ✔️
const [currentState, setState] = useState(intialState)
currentState permet d'appeler le state du composant, setState permet de l'enregistrer dans currentState et initialState est le state par défaut du composant.

- les composants enfants et les _props_ qu'on leur passe ✔️
On peut faire passer des données à un composant enfant grace aux props.

- le déclenchement d'instructions en fonction des actions de l'utilisateur ✔️
Grace aux fonctions onClick() qui se déclenche au clique de l'utilisateur ou onChange() qui se déclenche quand l'élement en question change par exemple.

- le déclenchement d'instructions en fonction de l'étape du cycle de vie du composant ou du changement de valeur de ses props ✔️
On peut utiliser useEffect(() => {}, []) pour déclencher une action au montage et démontage du composant.

- l'usage d'un reducer (_useReducer_) pour gérer un état composé dans un composant ❌ / ✔️
- l'état stocké dans un composant avec un _context provider_ et accessible dans ses descendants via `useContext` ❌ / ✔️

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```
import React, { useEffect, useState } from 'react';
import './App.css';
import axios from 'axios';
import Wilder from './components/Wilder';
import AddWilder from './components/AddWilder';
import { IWilderProps } from './entity/Wilder';
import { IGradeFromApi, IWilderFromApi } from './entity/WilderApi';

const formatWildersFromApi = (wilders: IWilderFromApi[]): IWilderProps[] =>
  wilders.map((wilder) => {
    return {
      id: wilder.id,
      city: wilder.city,
      name: wilder.name,
      skill: wilder.grade.map((grade: IGradeFromApi) => {
        return { id: grade.id, votes: grade.grade, title: grade.skill.name };
      }),
    };
  });

function App() {
  const [wilders, setWilders] = useState<IWilderProps[]>([]);

  const fetchWilders = async () => {
    const apiWilders = await axios.get<IWilderFromApi[]>("http://localhost:5000/api/wilder");
    setWilders(formatWildersFromApi(apiWilders.data));
  }

  useEffect(() => {
    fetchWilders();
  }, []);

  return (
    <div>
      
      <header>
        <div className="container">
          <h1>Wilders Book</h1>
        </div>
      </header>
      <main className="container">
        <h2>Wilders</h2>

        <AddWilder/>
        
        <section className="card-row">

          {
            wilders.map((wilder: IWilderProps) => (
              <Wilder 
                key={wilder.id} 
                name={wilder.name}
                city={wilder.city}
                skill={wilder.skill} 
                id={wilder.id} 
              />
            ))
          }

        </section>
      </main>
      <footer>
        <div className="container">
          <p>&copy; 2022 Wild Code School</p>
        </div>
      </footer>
    </div>
  );
}

export default App;

```

### Utilisation dans un projet ❌ / ✔️

[lien github](...)

Description :

### Utilisation en production si applicable❌ / ✔️

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌ / ✔️

Description :

## 🌐 J'utilise des ressources

### Doc React

- https://react.dev/
- La documentation officiel de React

### Google en général

- https://www.google.com/
- Pour tous problemes rencontré je me sers de google pour essayer d'y voir plus clair et de trouver une solution.

### Stack Overflow

- https://stackoverflow.com/
- LE forum ou des millions de personnes posent des questions sur multitudes de problèmes.

## 🚧 Je franchis les obstacles

### Point de blocage ❌ / ✔️

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️
