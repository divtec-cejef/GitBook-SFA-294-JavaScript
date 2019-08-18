# Introduction

JavaScript est un **langage de script**, **multiplateforme** et **orienté objet**.

C'est un **langage léger** qui **doit faire partie d'un environnement hôte** \(un navigateur web par exemple\) pour qu'il puisse être **utilisé sur les objets de cet environnement**.

Quelques généralités sur JavaScript :

* Langage interprété
  * Nécessite un interpréteur \(versus. un compilateur\)
* Langage orienté objet
  * Langage à « prototype »

    Un prototype est un objet à partir duquel on crée de nouveaux objets
* Sensible à la casse
* Confusion fréquente avec Java
  * Aucun lien entre ces 2 langages !
* Anciennement appelé ECMAScript
  * Standardisé par ECMA \( European Computer Manufacturers Association\)

## Ou écrire du JavaScript

### Dans la console d'un navigateur

![Console JavaScript de Firefox](../../.gitbook/assets/133a-js-firefox-console%20%281%29.gif)

1. Ouvrir la **console** de votre navigateur `command` + `option` + `J` \(Mac\) ou `control` + `shift` + `J` \(Windows, Linux, Chrome OS\) pour ouvrir la **console**.
2. Sélectionner l'**onglet Console**.
3. Écrire l'instruction suivante : `alert("Bonjour les apprentis en JS");`
4. Valider l'instruction avec la touche `↵ Enter`

### Dans une fichier HTML

Il suffit de placer le code JavaScript dans un élément HTML `<script>`.

Le code JavaScript contenu dans les balises `<script>` est interprété instruction par instruction comme les éléments HTML.

```markup
<h1>Titre de ma page</h1>

<script>
    alert("Bonjour depuis une page HTML !");
</script>

<p>Un petit paragraphe</p>
```

{% hint style="success" %}
**Eviter de mélanger JavaScript et HTML.**

Un bon développeur séparera toujours le contenu \(HTML\), la mise en forme \(CSS\) et les traitements \(JavaScript\).
{% endhint %}

### Dans un fichier externe

Généralement on écrit le code JavaScript dans des fichiers portant l'extension `.js`. Exemple : `panier-achats.js`

Pour intégrer un fichier JavaScript dans un document HTML on utilisera l'élément `<script>` et l'attribut `src`. Exemple :

```markup
<script src="panier-achats.js"></script>
```

#### Ou placer la balise `<script>`

On peut placer la balise `<script>` dans l'entête du document `<head>` ou dans le corpts `<body>`.

La meilleure pratique consite a placer ses scripts à la fin du document juste avant la balise de fermeture du corps du document `</body>`.

```markup
<!DOCTYPE html>
<html lang="fr">
  <head>
    <title>Panier d'achats</title>
  </head>
  <body>
    <h1>Votre panier d'acahts</h1>
    <p>Cette semaine promotion sur les loutres blanches du Gabon</p>

    <!-- Inclusion des scipts -->  
    <script src="panier-achats.js"></script>
  </body>
</html>
```

#### Pourquoi à la fin du et pas au début du document, dans l'entête  ?

Le navigateur interprète le code de la page et résout les éléments un par un.

Lorsqu'il rencontre un élément `<script>` il va charger tout son contenu avant de passer à l’élément suivant.

L’inclusion des script à la fin du document va donc permettre :

* d'afficher rapidement quelque chose à l’écran. Le navigateur ne doit pas attendre le chargement des scripts avant d'interpréter les autres éléments HTML.
* de manipuler les éléments HTML de la page car tous créés avant l'importation du script.

## La directive "use strict"

En ajoutant la directive `"use strict"` au début d'un script, on demande au navigateur de respecter la nomre ECMAScript et d'ainsi arrêter le script à la moindre erreur.

{% hint style="info" %}
Appliquer "use strict" à tous vos scripts afin d'éviter les auto-correction des navigateurs. Il vaut mieux stopper un script erroné le plus rapidement possible.
{% endhint %}

On peut placer la directive au début d'un script ou au début d'une fonction.

Les deux exemples suivant généreront un erreur et le script sera stoppé, car la variable `msg`n'a pas été correctement déclarée.

```markup
<script>
    "use strict";
    msg = "Bonjour";
    alert(msg);
</script>
```

```javascript
function maFonction() {
    "use strict";
    msg = "Bonjour";
}
```

## Conventions de nommage, JavaScript Style Guide

Beaucoup de guides exposent leur règles de "codage" pour le JavaScipt.

Les plus connus sont ceux de AirBnB, GitHub, & Google : 

* [https://google.github.io/styleguide/jsguide.html](https://google.github.io/styleguide/jsguide.html)
* [https://github.com/airbnb/javascript](https://github.com/airbnb/javascript)
* [https://github.com/standard/standard](https://github.com/standard/standard)

Il existe également des outils permettant d'analyser votre code comme [ESLint](https://eslint.org/) & [JSLint](https://www.jslint.com/).

A vous de trouvez celui qui vous convient le mieux. Peut importe votre choix, l'important c'est de choisir un style et de le respecter.

Ce support de cours est basé sur les conventions de **Google** et de **JSLint**.



