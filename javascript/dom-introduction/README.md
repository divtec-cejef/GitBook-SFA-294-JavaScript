---
description: >-
  JavaScript permet de créer, modifier et supprimer dynamiquement les éléments
  HTML, les styles CSS et les événements d'une page Web.
---

# Manipuler une page Web via le DOM

## Dis papa c'est quoi le DOM ?

Le DOM \(Document Object Model\) est un objet JavaScript représentant le document HTML \(ou XML\) actuellement chargé dans le navigateur.

Dans cet objet, le document `Document` y est **représenté comme un arbre nodal**, chaque nœud `Node` représentant une partie du document.

Il existe trois pricipaux type de nœud :

* `Element` : un élément HTML `<p>, <h1>, <body>, <img>, ...`
* `Text` : chaine de caractères `"C'est pas faux !"`
* `Comment` : commenaire HTML `<!-- Je suis un simple commentaire -->`

### Exemple

Ci-après le code source d'un document HTML et sa repésentation sous forme d'arbre nodal de type DOM.

```markup
<!doctype html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Geek Power</title>
    </head>

    <body>
        <h1>Vive le Kode</h1>
        <p>J'aime le <a href="http://www.kode.ch">Kooode</a> !</p>
    </body>
</html>
```

![](../../.gitbook/assets/dom-arbre-nodal.png)

## Et JavaScript dant tou ça ?

Grâce au DOM, JavaScript à le pouvoir de :

* **Récupérer un élément** HTML du document
* **Modifier un élément** en personalisant
  * son **contenu texte** `"texte"` **ou HTML** `"<li>Yoda</li>"`
  * son **style CSS** `fontSize, backgroundColor, border, ...`
  * ses **attributs** `href, class, src, …`
  * ses **événements** `click, submit, mouseover, load, ...`
* **Créer un élément** et l'ajouter au document
* **Supprimer un élément** HTML du document

