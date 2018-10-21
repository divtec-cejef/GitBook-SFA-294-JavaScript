# Accéder aux éléments

On peut rechercher, accéder, aux éléments du document de deux manières :

1. En recherchant **dans tous le document**, en utilisant l'objet `document`.
2. En recherchant **depuis un noeud spécifique** de type `Element`.

La deuxième méthode est plus efficace, puisqu'elle ne nécessite pas un parcours complet du document.

> L' objet `document` est un noeud de type `Element` et correspond à l'élément `<html>` de la page.

## document.getElementById\(\)

Ne peut être appelée qu'avec l'objet `document`.

Renvoie un objet `Element` représentant l'élément dont l' `id` correspond à la chaîne de caractères passée en paramètre.

```javascript
// Renvoie l'élément avec l'id "menu" <nav id="menu">...</nav>
const menuPrincipal = document.getElementById('menu');
```

## Element.getElementsByClassName\(\)

Peut être appelée avec l'objet `document` ou un objet de type `Element`.

Retourne un "tableau" \(HTMLCollection\) contenant une référence sur tous les éléments ayant les noms de classes passés en paramètre.

```javascript
// Renvoie un tableau de tous les éléments du document
// appartenant à la classe rouge
let elementsRouges = document.getElementsByClassName('rouge');

// Renvoie un tableau de tous les enfants de l'élément spécifié
// appartenant aux classes rouge ET gras
let elementsRougesGras = monElement.getElementsByClassName('rouge gras');
```

{% embed url="https://codepen.io/fallinov/pen/BqPNjK" %}



```javascript
// Renvoie l'élément avec l'id "menu" <nav id="menu">...</nav>
const menuPrincipal = document.getElementById('menu');

// Renvoie un tableau de tous les éléments du document appartenant à la classe rouge
let elementsRouges = document.getElementsByClassName('rouge');
// Renvoie un tableau de tous les enfants de rootElement appartenant aux classes rouge ET gras
let elementsRougesGras = monElement.getElementsByClassName('rouge gras'); 

// Renvoie un tableau de tous les éléments <li> du document
let elementsDeListes = document.getElementsByTagName('li');
// Renvoie un tableau des éléments <strong> enfants de monElement
let taches = monElement.getElementsByTagName('strong');

// Renvoie le premier élément du document correspondant à l'un des sélecteur CSS 'img.rouge, img-jaune' (images appartenant à la classe rouge OU jaune)
const imageRouge = document.querySelector('img.rouge, img.jaune');
// Renvoie le premier élément enfants de monElement correspondant au sélecteur CSS 'input:checked' (checkboxes ou radios cochés)
const elementCoche = monElement.querySelector('input:checked');

// Retourne un tableau de tous les éléments correspondants à l'un des sélecteurs CSS
// Sélectionne les div appartenant à la classe "note" OU "alert"
let notesEtAlertes = document.querySelectorAll('div.note, div.alert');
```

## Naviguer dans le DOM

### Récupérer les enfants d'un élément `element.childNodes`

```javascript
let monElement = document.getElementById('monElement');
let enfants = monElement.childNodes;
```

### Récupérer le parent d'un élément  `element.parentNode`

```javascript
let parent = enfants.parentNode;
```

