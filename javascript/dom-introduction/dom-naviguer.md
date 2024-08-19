# Naviguer dans le DOM

"Naviguer dans la DOM", représente l'action de se déplacer, ou récupérer un noeud parent, enfant ou adjacent.

![Propriétés de navigations DOM](<../../.gitbook/assets/image (3).png>)

## Tableau des propriétés

| Action                           | Propriétés des noeud                                                             | Retour                                                                                                                |
| -------------------------------- | -------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| <p>Récupérer les fils</p><p></p> | <p><code>node.childNodes</code></p><p><code>element.children</code></p>          | <p><code>NodeList</code> <em>tableau de noeuds</em></p><p><code>HTMLCollection</code> <em>tableau d'éléments</em></p> |
| Premier fils                     | <p><code>node.firstChild</code></p><p><code>element.firstElementChild</code></p> | <p><code>Node</code></p><p><code>Element</code></p>                                                                   |
| Dernier fils                     | <p><code>node.lastChild</code></p><p><code>element.lastElementChild</code></p>   | <p><code>Node</code></p><p><code>Element</code></p>                                                                   |
| Frère suivant                    | `node.nextSibling`                                                               | `Node`                                                                                                                |
| Frère précédent                  | `node.previousSibling`                                                           | `Node`                                                                                                                |
| Récupèrer le parent              | `node.parentNode`                                                                | `Node`                                                                                                                |

Comme on peut le voir, certaines actions sont réalisables avec deux propriétés différentes.

Il existe deux "familles" de propriétés pour naviguer dans la DOM :

* Les propriétés de type  `Node` , pour naviguer dans **tous les types de noeuds** : éléments, textes ou  commentaires
* Les propriétés de type `Element` , pour naviguer **uniquement dans les éléments**

Dans l'exemple ci après, on récupère le premier fils de la `div`  avec la propriété `firstChild`, avec la propriété`firstElementChild` .

* La propriété `firstChild` retourne le premier noeud peut importe son type.\
  Dans l'exemple le premier noeud est un noeud texte contenant `"Bonjour le"`.
* La propriété `firstElementChild` retourne le premier noeud de type élément.\
  Dans l'exemple le premier élément de la div est `<strong>monde</strong>`.

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

