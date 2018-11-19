# Modifier les contenus textes

Il existe deux propriétés pour récupérer ou modifier le contenu d'un élément HTML :

1. [`innerHTML`](dom-modifier-texte.md#innerhtml) : lecture ou modification au **format HTML** 
2. [`innerText`](dom-modifier-texte.md#innertext) : lecture ou modification au **format texte brut**

La méthode, [`insertAdjacentHTML()`](dom-modifier-texte.md#insertadjacenthtml-position-text) permet elle d'ajouter du HTML à différents emplacement d'un élément.

## `innerHTML`

Récupère ou définit le contenu HTML d'un élément et de ses descendants.

```markup
<p id="intro">
  Je suis un <strong>joli</strong> paragraphe !
</p>

<script>
// Récupère le paragraphe #intro
let introPara = document.getElementById('intro');
// Récupère le contenu HTML du paragraphe
let contenu = introPara.innerHTML; //Je suis un <strong>joli</strong> paragraphe !

// Remplacer le contenu HTML du paragraphe
introPara.innerHTML = 'Je suis un <em>nouveau</em> paragraphe !';
// <p>Je suis un <em>nouveau</em> paragraphe !</p>

// Ajouter du contenu HTML à la fin du contenu existant avec +=
introPara.innerHTML += ' <a href="http://kode.ch">Lien</a>';
// <p>Je suis un <em>nouveau</em> paragraphe ! <a href="http://kode.ch">Lien</a></p>
</script>
```

{% embed url="https://codepen.io/fallinov/pen/KrypqZ?editors=1000" %}

## `innerText`

Représente le contenu textuel, le rendu visuel d'un élément. Il fait donc abstraction des balises HTML.

Utilisé en lecture, il renvoie une approximation du texte que l’utilisateur ou utilisatrice obtiendrait s’il ou elle sélectionnnait le contenu d’un élément avec le curseur, et le copiait dans le presse-papier.

```markup
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

{% embed url="https://codepen.io/fallinov/pen/qQVdXG?editors=0010" %}

## `insertAdjacentHTML(position, text);`

Permet d'ajouter du `text` HTML à une `position` donnée autours ou à l'intérieur d'un `element` existant.

Il existe quatre `positions`:

* `'beforebegin'` : **Avant** l'`element`  lui-même.
* `'afterbegin'` : Juste à l'intérieur de l'`element` , **avant son premier enfant**.
* `'beforeend'` : Juste à l'intérieur de l'`element` , **après son dernier enfant**.
* `'afterend'` : **Après** `element` lui-même.

```markup
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

### Exemple

```markup
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

{% embed url="https://codepen.io/fallinov/pen/qQVdPz?editors=1000" %}

