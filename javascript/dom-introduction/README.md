---
description: >-
  JavaScript permet de créer, modifier et supprimer dynamiquement les éléments
  HTML, les styles CSS et les événements d'une page Web.
---

# Manipuler une page Web via le DOM

### Dis papa c'est quoi le DOM ?

Le DOM \(Document Object Model\) est un modèle de document chargé dans le navigateur. Le document HTML \(ou XML\) y est **représenté comme un arbre nodal**. Chaque nœud `Node` représente une partie du document. Il existe trois pricipaux type de nœud :

* `Element` : un élément HTML 
* `Text` : chaine de caractères
* `Comment` : commenaire HTML

Ci-après un repésentation typique du DOM sous forme d'arbre nodal.

![Repr&#xE9;sentation d&apos;un document HTML sous forme d&apos;arbre nodal](http://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/JS_DOMExample.png)

### Et JavaScript dant tou ça ?

Grâce au DOM, JavaScript à le pouvoir de :

* **Récupérer un élément** HTML du document
* **Modifier un élément** du document et personaliser
  * son **contenu texte ou HTML**
  * son **style CSS**
  * ses **attributs**
* **Supprimer un élément** HTML du document
* 


