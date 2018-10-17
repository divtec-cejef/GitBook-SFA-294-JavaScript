# Modifier les contenus textes

## `innerHTML`

Récupère ou définit le contenu HTML d'un élément, de ses descendants.

```markup
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

## `innerText`

Représente le contenu textuel, le rendu visuel d'un noeud. Il fait donc abstraction des balises HTML.

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

