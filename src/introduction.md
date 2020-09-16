## Avant de commencer
> Avant de commencer ce Dojo sur React, vous devez configurer votre poste.

#### Quel éditeur de code utiliser ?
Vous pouvez utiliser n’importe quel éditeur de code, et si vous n’avez pas encore fait votre choix, nous vous conseillons d’utiliser Visual Studio Code (gratuit et maintenu par Microsoft).

#### Télécharger Visual Studio Code
Cliquez sur ce lien, https://code.visualstudio.com/ afin de télécharger l’éditeur de code

#### Configuration Visual Studio Code
Une fois Visual Studio Code installé sur votre poste, nous allons ajouter des extensions qui vous seront fort utiles lors des phases de live coding.
Lancer l'éditeur, une fois l’écran affiché, cliquer sur l’icône « Extensions », elle se situe sur la barre latérale de gauche.
*Installer ces deux extensions : *
- Prettier Formatter 
- Live Server

#### Configuration Prettier
Utiliser le raccourcis, Ctrl + P depuis Visual Code Studio
Une fois la console affichée, mettez ceci ">preferences: Open Settings (Json) " puis taper sur « Entrée »

Remplacer le code json par ceci :
```javascript
{
    "prettier.singleQuote": true,
    "editor.formatOnSave": true,
    "[javascript]": {
        "editor.formatOnSave": true,
    },
    "window.zoomLevel": 0
}
```
**Enregistrer le fichier et redémarrer votre éditeur.  Voilà, vous êtes enfin prêt pour l’aventure 😊**

## 1.1 Qu'est ce que react

> _**React** est une bibliothèque JavaScript pour la construction d’interfaces utilisateur (UI)_ de reactjs.org

## 1.2 Pourquoi React?

Creation d'un système qui permet d'afficher les tranches d'imposition

**En natif**

```javascript
class TrancheList {
  tranches = [];
  element = null;

  constructor(element) {
    this.element = element;
  }

  addTranche(name) {
    this.tranches.push(name);
    const li = document.createElement("li");
    const a = document.createElement("a");
    a.innerText = "Supprimer";
    li.appendChild(a);
    a.addEventListener("click", () => this.remove(name));
    this.element.appendChild(li);
  }
}
```

####:warning: Ce qui ne va pas:

- Il est difficile de synchroniser notre état et notre vue.
- La manipulation du DOM et peu performante.
- Code Spaghetti

**Avec React**

```javascript
class TodoList extends React.Component {
  constructor(props) {
    super(props);
    this.state = { todos: [] };
  }

  addItem(name) {
    const todos = [...this.state.todos, name];
    this.setState({ todos: todos });
  }

  render() {
    return (
      <ul>
        {this.states.todos.map((name) => {
          return (
            <li>
              {name}{" "}
              <button onClick={this.removeItem.bind(this, name)}>
                Supprimer
              </button>
            </li>
          );
        })}
      </ul>
    );
  }
}
```

####:ok_hand: Qu'est ce qui change:

- Pas de manupulation directe du DOM.
- Sépration entre etat et vue (Séparation of concern).
- Notre vue est une fonction de l'etat.

## 1.3 Difference avec les frameworks du marché

- Une API simple (peu de fonctions)
- Excellent ecosystème
- JSX (système de template facile à apprendre)

## 1.4 Configuration du projet

Pour utiliser React sur une page nous avons besoin de récupérer les paquets sur NPM mais il existe un service qui s'appelle unpkg qui nous permet d'ajouter React à nos pages web.
Dans ce chapitre, pour des raisons de simplicité nous allons utilisé unpkg pour ajouter React à notre projet. Cela nous permettra de nous abstraire des outils satellites (CRA, WEBPACK, NPM,...).
