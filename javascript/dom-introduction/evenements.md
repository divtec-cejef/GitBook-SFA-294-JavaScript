# Evénements

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



