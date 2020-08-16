# Naviguer dans le DOM

"Naviguer dans la DOM", représente l'action de se déplacer, ou récupérer un noeud parent, enfant ou adjacent.

![Propri&#xE9;t&#xE9;s de navigations DOM](../../.gitbook/assets/image.png)

## Tableau des propriétés

<table>
  <thead>
    <tr>
      <th style="text-align:left">Action</th>
      <th style="text-align:left">Propri&#xE9;t&#xE9;s des noeud</th>
      <th style="text-align:left">Retour</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>R&#xE9;cup&#xE9;rer les fils</p>
        <p></p>
      </td>
      <td style="text-align:left">
        <p><code>node.childNodes</code>
        </p>
        <p><code>element.children</code>
        </p>
      </td>
      <td style="text-align:left">
        <p><code>NodeList</code>  <em>tableau de noeuds</em>
        </p>
        <p><code>HTMLCollection</code>  <em>tableau d&apos;&#xE9;l&#xE9;ments</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Premier fils</td>
      <td style="text-align:left">
        <p><code>node.firstChild</code>
        </p>
        <p><code>element.firstElementChild</code>
        </p>
      </td>
      <td style="text-align:left">
        <p><code>Node</code>
        </p>
        <p><code>Element</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Dernier fils</td>
      <td style="text-align:left">
        <p><code>node.lastChild</code>
        </p>
        <p><code>element.lastElementChild</code>
        </p>
      </td>
      <td style="text-align:left">
        <p><code>Node</code>
        </p>
        <p><code>Element</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Fr&#xE8;re suivant</td>
      <td style="text-align:left"><code>node.nextSibling</code>
      </td>
      <td style="text-align:left"><code>Node</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Fr&#xE8;re pr&#xE9;c&#xE9;dent</td>
      <td style="text-align:left"><code>node.previousSibling</code>
      </td>
      <td style="text-align:left"><code>Node</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">R&#xE9;cup&#xE8;rer le parent</td>
      <td style="text-align:left"><code>node.parentNode</code>
      </td>
      <td style="text-align:left"><code>Node</code>
      </td>
    </tr>
  </tbody>
</table>

Comme on peut le voir, certaines actions sont réalisables avec deux propriétés différentes.

Il existe deux "familles" de propriétés pour naviguer dans la DOM :

* Les propriétés de type  `Node` , pour naviguer dans **tous les types de noeuds** : éléments, textes ou  commentaires
* Les propriétés de type `Element` , pour naviguer **uniquement dans les éléments**

Dans l'exemple ci après, on récupère le premier fils de la `div`  avec la propriété `firstChild`, avec la propriété`firstElementChild` .

* La propriété `firstChild` retourne le premier noeud peut importe son type. Dans l'exemple le premier noeud est un noeud texte contenant `"Bonjour le"`.
* La propriété `firstElementChild` retourne le premier noeud de type élément. Dans l'exemple le premier élément de la div est `<strong>monde</strong>`.

```markup
<div>Bonjour le <strong>monde</strong>!</div>

<script>
// Récupère la première <div> du document
const div = document.querySelector("div");

// Affiche le premier fils avec firstChild
console.log( div.firstChild ); // "Bonjour le" 

// Affiche le premier fils de type Element avec firstElementChild
console.log( div.firstElementChild ); // "<strong>monde</strong>"
</script>
```

### Propriétés de type `Node`

```markup
<div>Bonjour <strong>le <em>monde</em></strong>!</div>

<script>
// Récupère le premier élément strong du document
const strongElement = document.querySelector("strong");

// Noeud parent
moneElement.parentNode; // <div>

// Tous les fils (tableau de noeuds)
monElement.childNodes; // ["le ", <em>]

// Premier fils
monElement.firstChild; // "le "

// Dernier fils
monElement.lastChild; // <em>

// Frêre suivant
monElement.nextSibling; // "!"

// Frêre précédent
monElement.previousSibling; // "Bonjour "
</script>
```

### Propriétés de type `Element`

```markup
<div id="animaux">
   <h1>Animaux</h1>
   <ul>
      <li>🐔</li>
      <li>🐷</li>
   </ul>
</div>

<script>
// Récupère la première liste non triée du document
const listeAnimaux = document.querySelector("ul");

// Noeud parent
listeAnimaux.parentNode; // <div id="animaux">...</div>

// Tous les fils (tableau de noeuds)
listeAnimaux.children; // [<li>🐔</li>, <li>🐷</li>]

// Premier fils
listeAnimaux.firstElementChild; // <li>🐔</li>

// Dernier fils
listeAnimaux.lastElementChild; // <li>🐷</li>
</script>
```



