# Evénements

## Lier une fonction à un événement

Il existe deux manières d'affecter une fonction à l'événement d'un élément.

1. Utiliser les **gestionnaires d'événements "on-event"**
2. Créer des écouteur d'événement \(listener\) avec **la méthode `addEventListener()`** 

Avec la première méthode, chaque objet ne peut avoir qu'un seul gestionnaire d'événement pour un événement donné. C'est pourquoi `addEventListener()` est souvent le meilleur moyen d'être averti des événements.

### Gestionnaires d'événements "on-event"

Les gestionnaires d'événements "on-event" sont nommées selon l'événement lié : `onclick`, `onkeypress`, `onfocus`, `onsubmit`, etc. 

Liste des gestionnaires d'événements : [https://www.w3schools.com/tags/ref\_eventattributes.asp](https://www.w3schools.com/tags/ref_eventattributes.asp)

On peut scpécifier un "on-event" pour un événement particulier de différentes manières :

* Avec un attribut HTML : `<button onclick="bonjour()">`
* En utilisant la propriété correspondante en JavaScript : `Element.onclick = bonjour;`

{% hint style="warning" %}
En JavaScript, afin d'affecter la fonction `bonjour()` et non son résultat, on n'ajoute pas les parenthèses après le nom de la fonction.

* `Element.onclick = bonjour;`  affecte la fonction `bonjour()`.
* `Element.onclick = bonjour();`  affecte le résultat de la fonction `bonjour()`.
{% endhint %}

```javascript
function citationLeia() {
  alert("Plutôt embrasser un Wookie");
}

// Affecte la fonction citationLeia() au click du bouton
document.querySelector('button').onclick = citationLeia;

// Variante avec fonction anonyme
document.querySelector('button').onclick = function() {
  alert("Plutôt embrasser un Wookie");
};

// Variante avec fonction fléchée (arrow function)
document.querySelector('button').onclick = () => alert("Plutôt embrasser un Wookie");
```

{% embed url="https://codepen.io/fallinov/pen/wYOxKN?editors=101" caption="Gestion d\'événements \"on-event\"" %}

### addEventListener\(\)



```javascript
let newElement = document.getElementsByTagName('h1');

newElement.onclick = function() {
  console.log('clicked');
};

let logEventType = function(e) {
    console.log('event type:', e.type);
};

newElement.addEventListener('focus', logEventType, false);
newElement.removeEventListener('focus', logEventType, false);

window.onload = function() {
  console.log('Im loaded');
};
```

### Récupérer la cible `target`

en construction...

### Ajouter un événement `click` à une liste d'éléments

{% code-tabs %}
{% code-tabs-item title="main.js" %}
```javascript
let boutons = document.querySelectorAll("button");

for (const bouton of boutons) {
   bouton.addEventListener("click", function(event) {
      bouton.classList.toggle("rouge");
   });
}
```
{% endcode-tabs-item %}

{% code-tabs-item title="index.html" %}
```markup
<button>Bouton 1</button>
<button>Bouton 3</button>
<button>Bouton 3</button>

```
{% endcode-tabs-item %}

{% code-tabs-item title="styles.css" %}
```css
button {
   cursor: pointer;
   color: #7f8c8d;
   font-weight: bold;
   background-color: #ecf0f1;
   padding: 1em 2em;
   border: 2px solid #7f8c8d;
}

button.rouge {
   border-color: #c0392b;
   background-color: #e74c3c;
   color: #ecf0f1;
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% embed url="https://codepen.io/fallinov/pen/WaPXEQ/" %}



