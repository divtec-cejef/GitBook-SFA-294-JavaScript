# Commentaires & entêtes

Les commentaires et en-têtes jouent un rôle crucial dans la documentation du code JavaScript. Ils facilitent la compréhension du code par d'autres développeurs (ou par vous-même dans le futur) en expliquant la logique, les fonctionnalités et les détails importants du programme. Il est essentiel d'utiliser les commentaires de manière judicieuse pour assurer la maintenabilité du code.

### **Commentaires en JavaScript**

Il existe deux types de commentaires en JavaScript : les commentaires sur une seule ligne et les commentaires en bloc.

#### **Commentaire sur une seule ligne :**

```javascript
// Ceci est une ligne de commentaire
```

Utilisé pour annoter des parties spécifiques du code, souvent une ligne ou une partie de ligne.

#### **Commentaire en bloc :**

```javascript
/*
Ceci est un bloc 
de commentaires
*/
```

Utilisé pour commenter plusieurs lignes de code, idéal pour ajouter des explications détaillées ou désactiver de grandes sections de code.

### **En-têtes de Document**

Les en-têtes de document sont des blocs de commentaires placés au début des fichiers JavaScript. Ils servent à fournir des informations générales sur le fichier, comme l'auteur, la version du fichier, et la date de création. Ces en-têtes permettent de suivre l'évolution du code et d'attribuer le travail correctement.

```javascript
/**
 * @author Steve Fallet <steve.fallet@divtec.ch>
 * @version 1.6 (Version actuelle)
 * @since 2018-03-31 (Date de création)
 */
```

* **@author** : Indique l'auteur du code.
* **@version** : Spécifie la version actuelle du fichier ou du script.
* **@since** : Mentionne la date de création du fichier ou la version à laquelle il a été introduit.

### **En-têtes de Fonction**

Les en-têtes de fonction sont utilisés pour décrire les fonctions, leurs paramètres, et la valeur de retour. Ils permettent de comprendre rapidement ce que fait une fonction sans avoir à plonger dans le code.

```javascript
/**
 * Additionne deux nombres.
 * @param {number} a - nombre a.
 * @param {number} b - nombre b.
 * @return {number} résultat de a + b.
 */
function add(a, b) {
    return a + b;
}
```

* **@param {type} nom - description** : Décrit un paramètre de la fonction, en spécifiant son type et sa description.
* **@return {type} description** : Décrit la valeur de retour de la fonction, en précisant son type.

### **En-têtes de Classe**

Les en-têtes de classe décrivent la classe, ses constructeurs, et ses méthodes. Ils sont essentiels pour documenter des objets complexes et les méthodes associées.

```javascript
/** Classe représentant un point. */
class Point {
    /**
     * Crée un point.
     * @param {number} x - coordonnée x.
     * @param {number} y - coordonnée y.
     */
    constructor(x, y) {
        this.x = x;
        this.y = y;
    }
​
    /**
     * Retourne la coordonnée x
     * @return {number} La coordonnée x.
     */
    getX() {
        return this.x;
    }
​
    /**
     * Retourne la coordonnée y
     * @return {number} La coordonnée y.
     */
    getY() {
        return this.y;
    }
​
    /**
     * Convertit en point une chaîne contenant deux nombres séparés par une virgule.
     * @param {string} str - La chaîne contenant les deux nombres séparés par une virgule.
     * @return {Point} Un objet Point.
     */
    static fromString(str) {
        const [x, y] = str.split(',').map(Number);
        return new Point(x, y);
    }
}
```

* **@param {type} nom - description** : Décrit un paramètre de la méthode ou du constructeur, en spécifiant son type et sa description.
* **@return {type} description** : Décrit la valeur de retour de la méthode.

### **Bonne Pratique**

Il est recommandé de documenter chaque fonction, méthode, et classe dans votre code pour améliorer la lisibilité et faciliter la maintenance.

L'utilisation de ces en-têtes normalisés, souvent basés sur [JSDoc](https://jsdoc.app/), permet également une intégration avec des outils de documentation automatique, générant ainsi des documents HTML ou PDF décrivant le code.
