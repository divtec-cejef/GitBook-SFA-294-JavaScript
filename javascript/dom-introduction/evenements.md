# Evénements

Les événements permettent de déclencher une fonction pour une action spécifique, comme par exemple le clic ou le survol d'un élément, le chargement du document HTML ou encore l'envoi d'un formulaire.

## Principaux événements du DOM

| Evénement DOM | Description |
| :--- | :--- |
| `click` | Bouton de la souris enfoncé puis relâché sur un élément. |
| `dblclick` | Deux foix l'événement `click` |
| `mouseover` | Souris au-dessus d'un élément. |
| `mouseout` | Souris sort d'un élément. |
| `mousedown` | Bouton de la souris enfoncé, pas relâché, sur un élément. |
| `mouseup` | Bouton de la souris relâché sur un élément. |
| `mousemove` | Souris en mouvement au-dessus d'un élément. |
| `keydown` | Touche clavier enfoncée, pas relâchée, sur un élément. |
| `keyup` | Touche clavier relâchée sur un élément. |
| `keypress` | Touche clavier enfoncée et relâchée sur un élément. |
| `focus` | L'élément reçoit, gagne, le focus.   Quand un objet devient l'élément actif du document. |
| `blur` | Elément perd le focus. |
| `change` | Changement de a valeur d'un élément de formulaire. |
| `select` | Sélection du texte d'un élémen, mis en srubrillance. |
| `submit` | Envoi d'un formulaire |
| `reset` | Réinitialisation d'un formulaire |

 🔗 Liste complète des événements : [https://www.w3schools.com/jsref/dom\_obj\_event.asp](https://www.w3schools.com/jsref/dom_obj_event.asp)

## Affecter une fonction à un événement

Il existe différentes manières d'affecter une fonction à l'événement d'un objet.

* Utiliser les [**gestionnaires d'événements "on-event"**](evenements.md#on-event) ****👎 
* Créer des écouteur d'événement \(listener\) avec [**la méthode `addEventListener()`**](evenements.md#addeventlistener) 👍 

{% hint style="success" %}
**Le meilleure moyen est souvent `addEventListener()`**

Avec la méthode "on-event", chaque objet ne peut avoir qu'un seul gestionnaire d'événement pour un événement donné. C'est pourquoi `addEventListener()` est souvent le meilleur moyen d'être averti des événements.
{% endhint %}

### On-event

Les gestionnaires d'événements "on-event" sont nommées selon l'événement lié : `onclick`, `onkeypress`, `onfocus`, `onsubmit`, etc. 

🔗 Liste des gestionnaires d'événements : [https://www.w3schools.com/tags/ref\_eventattributes.asp](https://www.w3schools.com/tags/ref_eventattributes.asp)

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

### addEventListener\(\)

🔗 Liste des événements JavaScript : [https://www.w3schools.com/jsref/dom\_obj\_event.asp](https://www.w3schools.com/jsref/dom_obj_event.asp)

La méthode `addEventListener()` permet de définir une fonction à appeler chaque fois que l'événement spécifié est détecté sur l'élément ciblé.

```typescript
ElementCible.addEventListener("nomEvenement", nomFonction);
```



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

## Ajouter un événement à une liste d'éléments

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



## Récupérer la cible `target` d'un événement

```javascript
// Produit une liste
var ul = document.createElement('ul');
document.body.appendChild(ul);

var li1 = document.createElement('li');
var li2 = document.createElement('li');
ul.appendChild(li1);
ul.appendChild(li2);

function hide(e){
  // e.target se réfère à l'élément <li> cliqué
  // C'est différent de e.currentTarget qui doit faire référence au parent <ul> dans ce contexte
  e.target.style.visibility = 'hidden';
}

// Attache l'écouteur à la liste
// Il se déclenche pour chaque <li> clické
ul.addEventListener('click', hide, false);
```

