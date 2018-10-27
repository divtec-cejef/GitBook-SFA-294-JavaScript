---
description: 'Ajouter, modifier, vérifier, alterner des classes CSS'
---

# Classes CSS

```javascript
// Récupère l'élément #menu
let menu = document.getElementById('menu');

// Supprime la class rouge de #menu si présente
menu.classList.remove('rouge');

// Ajoute la class vert à #menu si non présente
menu.classList.add('vert');

// Ajoute ou retire plusieurs classes
menu.classList.add('jaune', 'bleu');
menu.classList.remove('jaune', 'bleu');

/* Alternance :
    Si #menu a la classe .rouge toggle('rouge') la retire
    Si #menu n'a pas la classe .rouge toggle('rouge') l'ajoute */
menu.classList.toggle('rouge');

// Retoune true si #menu a la classe .rouge, false s'il ne l'a pas
menu.classList.contains('rouge');
```

