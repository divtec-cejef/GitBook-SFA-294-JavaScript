# Timers & Intervalles

## setTimeout\(\)

`setTimeout(function, delai)` permet de définir un « minuteur » \(_timer_\) qui **exécute une fonction** ou un code donné **après la fin du délai indiqué en millisecondes**.

```javascript
function bonjour() {
  alert('Bonjour !');
}

// Créer un timer et stoque son ID dans timerBonjour
// Le timer attendra 5000 millisecondes avant d'appeler la fonction bonjour()
let timerBonjour = window.setTimeout(bonjour, 5000);

// Annule le timer correspondant à l'ID passé en paramètre
window.clearTimeout(timerBonjour);
```

### Exemple

```markup
<button onclick="startBonjour();">
  Affiche une alerte après 3 secondes...
</button>
<button onclick="stopBonjour();">
  Annuler l'affichage
</button>

<script>
let timerBonjour;

function bonjour() {
  alert("Bonjour !");
}

// Crée un timer qui appelle bonjour() après 3 secondes
// Stoque l'ID du timer dans la variable timerBonjour
function startBonjour() {
  timerBonjour = window.setTimeout(bonjour, 3000);
}

// Annule le timer timerBonjour
function stopBonjour() {
  window.clearTimeout(timerBonjour);
}
</script>
```

{% embed url="https://codepen.io/fallinov/pen/MzEdJV?editors=0010" caption="" %}

## setInterval\(\)

`setInterval(function, delai)` appelle une fonction **de manière répétée**, avec un certain **délai** fixé entre chaque appel.

```javascript
function bonjour() {
  alert('Bonjour !');
}

// Créer un intervalle et stoque son ID dans intervalleBonjour
// L'intervalle appellera bonjour() toutes les 5000 millisecondes
let intervalleBonjour = window.setInterval(bonjour, 5000);

// Annule l'intervalle correspondant à l'ID passé en paramètre
window.clearInterval(intervalleBonjour);
```

### Exemple

```markup
<div>
   <p>pin-pon, pin-pon, pin-pon ...</p>
</div>

<button onclick="changeCouleur();">Start</button>
<button onclick="stopChangeCouleur();">Stop</button>

<script>
let intervalleCouleur;

// Crée un intervalle qui appelle flashText() toute les 500 millisecondes
function changeCouleur() {
   intervalleCouleur = setInterval(flashText, 500);
}

function flashText() {
   // Récupère 1er paragraphe du document
   let para = document.querySelector("p");

   // Change la couleur du texte en rouge ou en bleu
   if (para.style.color === "red") {
      para.style.color = "blue";
   } else {
      para.style.color = "red";
   }
}

// Annule l'intervalle
function stopChangeCouleur() {
   clearInterval(intervalleCouleur);
}
</script>
```

{% embed url="https://codepen.io/fallinov/pen/MzEdJV?editors=0011" caption="" %}

