# Accéder aux éléments

On peut rechercher, accéder, aux éléments du document de deux manières :

1. En recherchant **dans tous le document**, en utilisant l'objet `document`.
2. En recherchant **depuis un noeud spécifique** de type `Element`.

La deuxième méthode est plus efficace, puisqu'elle ne nécessite pas un parcours complet du document.

> L' objet `document` représente l'élément  `<html>` de la page.

## document.getElementById\(\)

Ne peut être appelée qu'avec l'objet `document`.

Renvoie **un objet `Element`** représentant l'élément dont l' **`id`** correspond à la chaîne de caractères passée en paramètre.

```javascript
// Renvoie l'élément avec l'id "menu" <nav id="menu">...</nav>
const MENU = document.getElementById('menu');
```



## Element.getElementsByClassName\(\)

Peut être appelée avec l'objet `document` ou un objet de type `Element`.

Retourne un **tableau** \(HTMLCollection\) contenant une référence sur tous les éléments ayant les **noms de classes** passés en paramètre.

```javascript
// Renvoie un tableau de tous les éléments du document
// appartenant à la classe rouge
let elementsRouges = document.getElementsByClassName('rouge');

// Renvoie un tableau de tous les enfants de l'élément spécifié
// appartenant aux classes rouge ET gras
let elementsRougesGras = monElement.getElementsByClassName('rouge gras');
```

{% embed url="https://codepen.io/fallinov/pen/BqPNjK" %}



## Element.getElementsByTagName\(\)

Peut être appelée avec l'objet `document` ou un objet de type `Element`.

Retourne un **tableau** \(HTMLCollection\) contenant une référence sur tous les éléments portant le **nom de balise** donné passé en paramètre.

```javascript
// Renvoie un tableau de tous les éléments <li> du document
let elementsDeListes = document.getElementsByTagName('li');

// Renvoie un tableau des éléments <strong> enfants de monElement
let taches = monElement.getElementsByTagName('strong');
```



## Element.querySelector\(\)

Peut être appelée avec l'objet `document` ou un objet de type `Element`.

Retourne **le premier `Element`** dans le document correspondant au **sélecteur CSS** - ou groupe de sélecteurs - spécifié(s), ou null si aucune correspondance n'est trouvée.

```javascript
// Revoie le premier paragraphe du document
const PREMIER_PARA = document.querySelector('p');

// Renvoie le premier élément du document correspondant à l'un des sélecteur CSS 'img.rouge, img-jaune' (images appartenant à la classe rouge OU jaune)
const IMG_ROUGE_OU_JAUNE = document.querySelector('img.rouge, img.jaune');

// Renvoie la valeur (.value) de l'élément coché (:checked) du groupe d'input "pays"
let pays = document.querySelector('input[name="pays"]:checked').value;

// Renvoi le champ texte "login" présent dans la div avec la classe ".panneau-utilisateur"
const INPUT_LOGIN = document.querySelector('div.panneau-utilisateur input[name="login"]);
```



## Element.querySelectorAll\(\)

Peut être appelée avec l'objet `document` ou un objet de type `Element`.

Retourne un **tableau** \(NodeList\) contenant une référence sur tous les éléments correspondent au **sélecteur CSS** - ou groupe de sélecteurs - spécifié(s).

```javascript
// Retourne tous les paragraphes du document
let paras = document.querySelectorAll("p");

// Retourne tous les paragraphes présents dans une div avec la classe "article"
let parasAticle = container.querySelectorAll("div.article > p");

// Retourne un tableau de tous les éléments correspondants à l'un des sélecteurs CSS
// Sélectionne les div appartenant à la classe "note" OU "alert"
let notesEtAlertes = document.querySelectorAll('div.note, div.alert');
```