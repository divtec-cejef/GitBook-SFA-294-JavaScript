# Commentaires

```javascript
// Ceci est une ligne de commentaires

/*
Ceci est un bloc 
de commentaires
*/
```

## Entête de document

```javascript
/**
 * @author Steve Fallet <steve.fallet@divtec.ch>
 * @version 1.6 (Version actuelle)
 * @since 2018-03-31 (Date de création)
 */
```

## Entête de fonction

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

## Entête de classe

```javascript
/** Classe représentant un point. */
class Point {
    /**
     * Crée un point.
     * @param {number} x - coordonnée x.
     * @param {number} y - coordonnée y.
     */
    constructor(x, y) {
        // ...
    }

    /**
     * Retourne la coordonée x
     * @return {number} La coordonée x.
     */
    getX() {
        // ...
    }

    /**
     * Retourne la coordonée y
     * @return {number} La coordonée y.
     */
    getY() {
        // ...
    }

    /**
     * Converti en point une chaine contenant deux nombres séparés par un virgule.  
     * @param {string} str - La chaine contenant les deux nombres séparés par une virgule.
     * @return {Point} Un objet Point.
     */
    static fromString(str) {
        // ...
    }
}
```

