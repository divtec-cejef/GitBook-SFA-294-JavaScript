# Types de données

## Les différents types de données

JavaScript reconnaît plusieurs types de données, dont certains sont dits "primitifs" car ils ne sont pas des objets et sont immuables. Le terme **immuable** signifie "qui ne peut pas être modifié après sa création".

Il existe également un type complexe, `Object`, qui englobe plusieurs structures de données plus complexes.

### Types **primitifs**

* `boolean` pour les booléen : `true` et `false`.
* `null` Représente une valeur nulle intentionnelle. En d'autres termes, `null` est utilisé pour indiquer l'absence volontaire d'un objet ou d'une valeur.
* `undefined` Représente une valeur non définie. Une variable déclarée, mais non initialisée, reçoit la valeur `undefined` par défaut.
* `number` pour les nombres entiers ou décimaux. Par exemple : `42` ou `3.14159`.
* `string` pour les chaînes de caractères. Par exemple : `"Coucou"`
* `symbol` Introduit avec ECMAScript 2015 (ES6), ce type est utilisé pour créer des valeurs uniques et immuables, souvent utilisées comme clés pour les propriétés d'objets.
* `bigint` : Ajouté avec ECMAScript 2020, ce type permet de représenter des nombres entiers plus grands que ceux que le type `number` peut représenter. `9007199254740991n`

### **Type Complexe : `Object`**

Les éléments ci-après sont tous de type `Object`

* **`Function`** : Représente des fonctions en JavaScript, qui sont elles-mêmes des objets.
* **`Array`** : Représente des tableaux, qui sont des collections ordonnées de valeurs.
* **`Date`** : Représente des dates et heures.
* **`RegExp`** : Représente des expressions régulières utilisées pour correspondre à des motifs dans des chaînes de caractères.

```javascript
let tableau = [];
let objet = {};
let date = new Date();
let regex = /ab+c/;
```

## Tester le type d'une variable

En JavaScript, il est possible de tester le type d'une variable en utilisant l'opérateur `typeof`, qui renvoie une chaîne indiquant le type de son opérande.

```javascript
let nombre = 1;
let chaine = 'some Text';
let bools = true;
let tableau = [];
let objet = {};
let pasUnNombre = NaN;
let vide = null;
let nonDefini;

console.log(typeof nombre);  // 'number'
console.log(typeof chaine);  // 'string'
console.log(typeof bools);   // 'boolean'
console.log(typeof tableau); // 'object' -- les tableaux sont de type objet
console.log(typeof objet);   // 'object'
console.log(typeof pasUnNombre); // 'number' -- bien que NaN signifie "Not-a-Number", son type est 'number'
console.log(typeof vide); // 'object' -- malgré que null soit un type primitif, typeof renvoie 'object'
console.log(typeof nonDefini); // 'undefined'

```

### Exemple de test de type

```javascript
let message = "Bonjour le monde";

if (typeof message === "string") {
    alert("C’est une chaîne");
} else {
    alert("Ce n’est pas une chaîne !");
}
```

### Astuces

#### **Comment savoir si une variable contient un tableau ?**

Utilisez la méthode `Array.isArray()` pour tester si une variable est un tableau :

```javascript
javascriptCopy codelet tableau = ['je', 'suis', 'un', 'tableau'];

if (Array.isArray(tableau)) {
    alert("C'est un tableau !");
} else {
    alert("Ce n'est PAS un tableau !");
}
```

#### **Comment s'assurer qu'une variable est du type `number` et que c'est un nombre valide ?**

Utilisez la fonction `isNaN()` pour vérifier qu'une valeur n'est pas `NaN` (Not-a-Number) :

```javascript
javascriptCopy codelet age = NaN;

if (typeof age === 'number' && !isNaN(age)) {
    alert("C'est un nombre !");
} else {
    alert("Ce n'est PAS un nombre !");
}
```
