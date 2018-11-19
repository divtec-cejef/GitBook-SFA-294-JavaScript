# Timers

## setTimeout\(\)

`setTimeout(function, delai)` permet de définir un « minuteur » \(_timer_\) qui **exécute une fonction** ou un code donné **après la fin du délai indiqué en millisecondes**.

```javascript
function bonjour() {
  alert('Bonjour !');
}

// Attend 5000 millisecondes avant d'appeler la fonction bonjour
window.setTimeout(bonjour, 5000);

// Pour supprimer un timer
let timer = window.setTimeout(bonjour, 5000);
window.clearTimeout(timer);
```

### Exemple

```markup
<button>Affiche un alerte après 3 secondes...</button>
<button>Annuler l'affichage</button>

<script>
let timerBonjour;

function bonjour() {
  alert("Bonjour !");
}

function startBonjour() {
  timerBonjour = window.setTimeout(bonjour, 3000);
}

function stopBonjour() {
  window.clearTimeout(timerBonjour);
}

// Affectation des fonctions aux boutons
boutons = document.querySelectorAll("button");
boutons[0].addEventListener("click", startBonjour);
boutons[1].addEventListener("click", stopBonjour);
</script>
```

{% embed url="https://codepen.io/fallinov/pen/MzEdJV?editors=0010" %}

## setInterval\(\)

```javascript
function bonjour() {
  alert('Bonjour !');
}

// Intervalle : Appelle la fonction bonjour toutes les 5000 millisecondes
window.setInterval(bonjour, 5000);

// Pour supprimer un interval
let intervalHandler = window.setInterval(bonjour, 5000);
window.clearInterval(intervalHandle);
```

