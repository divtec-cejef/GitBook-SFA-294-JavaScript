# Number

L'objet `Number` est une enveloppe autour du type primitif numérique, permettant de manipuler les nombres comme des objets. Bien que vous puissiez utiliser le constructeur `Number()` pour créer un objet, l'utilisation directe des valeurs numériques primitives est généralement préférable.

## Création d'un Objet Number

```
const a = new Number('123'); // Crée un objet Number
const b = Number('123'); // Convertit directement en valeur primitive
​
console.log(a === 123); // false, car 'a' est un objet
console.log(b === 123); // true, car 'b' est une valeur primitive
```

## Propriétés Utiles de `Number`

* **`Number.EPSILON`** : Plus petit intervalle entre deux valeurs distinctes.
* **`Number.MAX_SAFE_INTEGER` / `Number.MIN_SAFE_INTEGER`** : Limites des entiers sécurisés en JavaScript.
* **`Number.MAX_VALUE` / `Number.MIN_VALUE`** : Valeurs numérique maximum et minimum.
* **`Number.NaN`** : Représente une valeur "Not-a-Number".
* **`Number.POSITIVE_INFINITY` / `Number.NEGATIVE_INFINITY`** : Représentent l'infini.

## Méthodes Importantes de `Number`

* **`Number.isNaN()`** : Vérifie si une valeur est `NaN`.
* **`Number.isFinite()`** : Vérifie si une valeur est un nombre fini.
* **`Number.isInteger()`** : Vérifie si une valeur est un entier.
* **`Number.isSafeInteger()`** : Vérifie si une valeur est un entier sûr.
* **`Number.parseFloat()` / `Number.parseInt()`** : Convertit une chaîne en nombre flottant ou entier.
* **`Number.prototype.toFixed()`** : Formate un nombre avec un nombre fixe de décimales.
* **`Number.prototype.toString()`** : Convertit un nombre en chaîne de caractères.

```
let nombre = 2.345789;
console.log(nombre.toFixed(2)); // "2.35"
```

## Utilisation de `Number.NaN`

`Number.NaN` représente une valeur "Not-a-Number" utilisée pour indiquer qu'une opération mathématique n'a pas abouti à un nombre valide.

### Exemples

#### Division par une valeur non numérique

```javascript
let result = 0 / "string";
console.log(result); // NaN
```

#### Conversion invalide

```javascript
let invalidNumber = Number("abc");
console.log(invalidNumber); // NaN
```

#### Utilisation avec `isNaN()`

```javascript
let value = "text" / 2;
if (Number.isNaN(value)) {
  console.log("La valeur n'est pas un nombre.");
}
```

Dans ces exemples, `Number.NaN` est utilisé pour détecter et gérer les situations avec lesquelles les opérations arithmétiques ne produisent pas de résultats valides.

## Différence avec l'Objet `Math`

L'objet `Number` est souvent utilisé en complément de l'objet `Math`, qui offre des méthodes pour effectuer des calculs mathématiques complexes (par exemple, `Math.sqrt()` pour la racine carrée). `Number` se concentre davantage sur la gestion des types et des conversions numériques

