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

for (let bouton of boutons) {
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

## L'objet `event`

Un objet `event` est automatiquement passé comme premier paramètre de la fonction affectée à un événement. Pour le récupérer il suffit d'ajouter un paramètre à la fonction liée. Le nom de ce paramètre est libre mais on le nomme régulièrement `event` ou plus simplement `e`.

```markup
<button>Clique moi !</button>

<script>
// Récupère le 1er boutons du document
const BOUTON = document.querySelector("button");
// Ajoute événement click avec une fonction avec paramètre event
BOUTON.addEventListener("click", function (event) {
  // Affiche le type d'événement envoyé
  alert(event.type); // click
});
</script>
```

{% embed url="https://codepen.io/fallinov/pen/PyLVjJ" %}

### Récupérer la cible d'un événement

On appelle "cible" l'objet ou 'élément qui a envoyé l'événement. Pour récupérer la cible on utiliser la propriété `target` de l'événement.

```markup
<button>Clique moi !</button>

<script>
// Récupère le 1er boutons du document
const BOUTON = document.querySelector("button");
// Ajoute événement click avec une fonction avec paramètre event
BOUTON.addEventListener("click", function (event) {
  // Récupère l'élément qui a envoyé l'événement, la cible
  let cible = event.target;
  // Modifie la taille du texte de la cible
  cible.style.fontSize = "2em";
  // Affiche le contenu texte de la cible
  alert(cible.innerText); // Clique moi !
});
</script>
```

{% embed url="https://codepen.io/fallinov/pen/mzovXM" %}

## Bubbling & Capturing

Capture ? Bouillonnement ? De quoi parle-t-on ?

Ces deux phases sont deux étapes distinctes de l'exécution d'un événement. La première, la **capture** \(_capture_ en anglais\), s'exécute avant le déclenchement de l'événement, tandis que la deuxième, le **bouillonnement** \(_bubbling_ en anglais\), s'exécute après que l'événement a été déclenché. Toutes deux permettent de définir le sens de propagation des événements.  


![](../../.gitbook/assets/image%20%285%29.png)

```markup
<div id="div1">
  <p id="p1">I am Bubbling</p>
</div><br>

<div id="div2">
  <p id="p2">I am Capturing.</p>
</div>

<script>
document.getElementById("p1").addEventListener("click", function() {
    alert("You clicked the P element!");
}, false);

document.getElementById("div1").addEventListener("click", function() {
    alert("You clicked the DIV element!");
}, false);

document.getElementById("p2").addEventListener("click", function() {
    alert("You clicked the P element!");
}, true);

document.getElementById("div2").addEventListener("click", function() {
    alert("You clicked the DIV element!");
}, true);
</script>
```

{% embed url="https://codepen.io/fallinov/pen/zmbeev?editors=1111" %}

## A lire...

{% embed url="https://developer.mozilla.org/en-US/docs/Web/Guide/Events/Creating\_and\_triggering\_events" %}

