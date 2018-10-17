
### Accéder aux éléments du DOM

```javascript
// Renvoie l'élément identifier avec "menu" <nav id="menu">...</nav>
const menuPrincipal = document.getElementById('menu');

// Renvoie un tableau de tous les éléments du document appartenant à la classe rouge
let elementsRouges = document.getElementsByClassName('rouge');
//Renvoie un tableau de tous les enfants de rootElement appartenant aux classes rouge ET gras
let elementsRougesGras = monElement.getElementsByClassName('rouge gras'); 

// Renvoie un tableau de tous les éléments <li> du document
let elementsDeListes = document.getElementsByTagName('li');
// Renvoie un tableau des éléments <strong> enfants de monElement
let taches = monElement.getElementsByTagName('strong');

// Returns the first element within the document that matches the specified group of selectors.

// Renvoie le premier élément du document correspondant à l'un des sélecteur CSS 'img.rouge, img-jaune' (images appartenant à la classe rouge OU jaune)
const imageRouge = document.querySelector('img.rouge, img.jaune');
// Renvoie le premier élément enfants de monElement correspondant au sélecteur CSS 'input:checked' (checkboxes ou radios cochés)
const elementCoche = monElement.querySelector('input:checked');

// Retourne un tableau de tous les éléments correspondants à l'un des sélecteurs CSS
// Sélectionne les div appartenant à la classe "note" OU "alert"
let notesEtAlertes = document.querySelectorAll('div.note, div.alert');
```



### Naviguer dans le DOM  

#### Récupérer les enfants d'un élément `element.childNodes`

```javascript
let monElement = document.getElementById('monElement');
let enfants = monElement.childNodes;
```

#### Récupérer le parent d'un élément  `element.parentNode`

```javascript
let parent = enfants.parentNode;
```