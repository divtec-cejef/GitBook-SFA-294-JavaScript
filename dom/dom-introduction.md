## Document Object Model (DOM)

Le DOM (Document Object Model) est un modèle de document chargé dans le navigateur. Le document HTML (ou XML) y est **représenté comme un arbre nodal**. Chaque nœud `Node` représente une partie du document. Il existe trois pricipaux type de nœud :  

- `Element` : un élément HTML 
- `Text` : chaine de caractères
- `Comment` : commenaire HTML



Ci-après un repésentation typique du DOM sous forme d'arbre nodal.

![image](http://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/JS_DOMExample.png)



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



### Créer de nouveaux éléments

#### Ajouter un élément enfant à la fin d'un élément existant

Pour ajouter un élément comme dernier fils d'un élément existant il faut :

1. Créer un nouvel élément : `createElement("nomTagHTML")`
2. Créer un nœud texte : `createTextNode("chaine de caractères")`
3. Attacher le nœud texte au nouvel élément : `appendChild(nœudTexte)`
4. Récupérer un élément existant du DOM : voir chapitre [Accéder aux éléments de la DOM](#Accéder-aux éléments-de-la-DOM)
5. Attacher le nouvel élément à l'élément existant du DOM : `appendChild(element)`



##### Exemple : Ajouter un élément à la fin d'une liste

Voici comment ajouter le nouvel élément `<li>2kg de Pain</li>` **à la fin** de la liste `#fondue`. 

```html
<ul id="fondue">
    <li>2kg de Fromage</li>
    <li>1L de Kirsh</li>
</ul>

<script>
// 1. Création du nouvel élément <li> 
let newLi = document.createElement('li');

// 2. Création du nœud texte
let newLiTexte = document.createTextNode("2kg de Pain");

// 3. Ajout du texte au <li>
newLi.appendChild(newLiTexte);
    
// 4. Récupération de la liste
let listeFondue = document.getElementById('fondue');

// 5. Ajoute le nouvel élément <li> à la fin de la liste
listeFondue.appendChild(newLi);
</script>
```

###### Résultat

```html
<ul id="fondue">
    <li>2kg de Fromage</li>
    <li>1L de Kirsh</li>
    <li>2kg de Pain</li>
</ul>
```



#### Ajouter un nouvel élément avant un élément enfant existant

L'exemple précédent nous a montré comment ajouter un nouvel élément enfant à la fin d'un élément existant avec  `appendChild()`.

Il existe un autre méthode pour ajouter des éléments :  `element.insertBefore()`

```javascript
elementParent.insertBefore(nouvelElement, elementEnfantExistant);
```

Cette méthode permet d'ajouter à un élément existant `elementParent` un élément enfant `nouvelElement` juste avant l'élément enfant spécifié  `elementEnfantExistant`.



##### Exemple : Ajouter un élément au début d'une liste

Voici comment ajouter le nouvel élément `<li>2kg de Pain</li>` **au début** de la liste `#fondue`.

```html
<ul id="fondue">
    <li>2kg de Fromage</li>
    <li>1L de Kirsh</li>
</ul>

<script>
// 1. Création du nouvel élément <li> 
let newLi = document.createElement('li');

// 2. Création du nœud texte
let newLiTexte = document.createTextNode("2kg de Pain");

// 3. Ajout du texte au <li>
newLi.appendChild(newLiTexte);

// 4. Récupération d'un 1er élément <li> de la liste actuelle existant du DOM
let premierLi = document.querySelector('#fondue li:first-child');

// 3. Récupération du parent de premierLi
let parentLi = premierLi.parentNode;

// 6. Ajout de newLi avant premierLi
parentLi.insertBefore(newLi, premierLi);
</script>
```

###### Résultat

```html
<ul id="fondue">
	<li>2kg de Pain</li>
    <li>2kg de Fromage</li>
    <li>1L de Kirsh</li>
</ul>
```



### Récupérer et modifier le contenu texte et HTML d'un élément

#### `innerHTML`

Récupère ou définit le contenu HTML d'un élément, de ses descendants.

```html
<p id="intro">
  Je suis un <strong>joli</strong> paragraphe !
</p>

<script>
// Récupère le paragraphe #intro
let introPara = document.getElementById('intro');
// Récupère le contenu HTML du paragraphe avec la propriété .innerHTML
let contenu = introPara.innerHTML; //Je suis un <strong>joli</strong> paragraphe !

// Remplacer le contenu HTML du paragraphe
introPara.innerHTML = 'Je suis un <em>nouveau</em> paragraphe !';
// <p>Je suis un <em>nouveau</em> paragraphe !</p>

// Ajouter du contenu HTML à la fin du contenu existant avec +=
introPara.innerHTML += ' <a href="http://kode.ch">Lien</a>';
// <p>Je suis un <em>nouveau</em> paragraphe ! <a href="http://kode.ch">Lien</a></p>
</script>
```



#### `innerText`

Représente le contenu textuel, le rendu visuel d'un noeud. Il fait donc abstraction des balises HTML.

Utilisé en lecture, il renvoie une approximation du texte que l’utilisateur ou utilisatrice obtiendrait s’il ou elle sélectionnnait le contenu d’un élément avec le curseur, et le copiait dans le presse-papier.

```html
<p id="intro">
  Je suis un <strong>joli</strong> paragraphe !
</p>

<script>
// Récupère le paragraphe #intro
let introPara = document.getElementById('intro');

// Récupération du contenu avec innerText
console.log(introPara.innerText); // Je suis un joli paragraphe !

// Récupération du contenu avec innerHTML
console.log(introPara.innerHTML); // Je suis un <strong>joli</strong> paragraphe !
</script>
```



#### `insertAdjacentHTML(position, text);`

Permet d'ajouter du `text` HTML à une `position` donnée autours ou à l'intérieur d'un `element` existant.

Il existe quatre `positions `:

- `'beforebegin'` : **Avant** l'`element`  lui-même.
- `'afterbegin'` : Juste à l'intérieur de l'`element` , **avant son premier enfant**.
- `'beforeend'` : Juste à l'intérieur de l'`element` , **après son dernier enfant**.
- `'afterend'` : **Après** `element` lui-même.



```html
<p>bla bla</p>
<!-- beforebegin -->
<p id='intro'>
  <!-- afterbegin -->
  Un peu de texte
  <!-- beforeend -->
</p>
<!-- afterend -->
<p>bla bla</p>
```

##### Exemple

```html
<ul id="liste1">
  <li>élément de #liste1</li>
</ul>

<ul id="liste2">
  <li>élément de #liste2</li>
</ul>

<script>
// Ajouter un nouveau contenu entre #liste1 et #liste2
let liste2 = document.getElementById('liste2');

// Ajout de <p> juste avant et juste après #liste2
liste2.insertAdjacentHTML('beforebegin', '<p>Juste avant #liste2</p>');
liste2.insertAdjacentHTML('afterend', '<p>Juste après #liste2</p>');

// Ajout de <li> comme premier et dernier fils de la #liste2
liste2.insertAdjacentHTML('afterbegin', '<li>Nouveau premier fils de #liste2</li>');
liste2.insertAdjacentHTML('beforeend', '<li>Nouveau dernier fils de #liste2</li>');
</script>
```

### Classes : Ajouter, modifier, vérifier, alterner

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

