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

```javascript
let boutons = document.querySelectorAll("button");

for (const bouton of boutons) {
   bouton.addEventListener("click", function(event) {
      bouton.classList.toggle("rouge");
   });
}
```

{% embed url="https://codepen.io/fallinov/pen/WaPXEQ/" %}



