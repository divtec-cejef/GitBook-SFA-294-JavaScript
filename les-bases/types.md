# Types de données

* Six types de données **primitifs** :   
  * `boolean` pour les booléen : `true` et `false`.
  * `null` pour les valeurs nulles \(au sens informatique\).
  * `undefined` pour les valeurs indéfinies.
  * `number` pour les nombres entiers ou décimaux. Par exemple : `42` ou `3.14159`.
  * `string` pour les chaînes de caractères. Par exemple : `"Coucou"`
  * `symbol` pour les symboles, apparus avec ECMAScript 2015 \(ES6\). Ce  type est utilisé pour représenter des données immuables et uniques.
* et un type pour les **objets** `Object`, comme par exmple :
  * `Function`
  * `Array`
  * `Date`
  * `RegExp`

## Tester le type d'une variable

Les variables peuvent contenir tous types de données à tous moments. Il est donc important de pouvoir tester le type du contenu d'une variable.

L'opérateur `typeof` renvoie une chaîne qui indique le type de son opérande.

```javascript
let nombre = 1;
let chaine = 'some Text';
let bools = true;
let tableau = [];
let objet = {};
let pasUnNombre = NaN; //NaN (Not A Number) est une valeur utilisée pour représenter une quantité qui n'est pas un nombre
let vide = null;
let nonDefini;

typeof nombre;  // 'number'
typeof chaine;  // 'string'
typeof bools;   // 'boolean'
typeof tableau; // 'object' -- les tableaux sont de type objet.
typeof objet; // 'object'
typeof pasUnNombre; // 'number' -- Et oui NaN fait partie de l'objet Number.
typeof nonDefini; // 'undefined'
```

### Exemple de test de type

```javascript
let message = "Bonjour le monde";

if(typeof message === "string"){
    alert("c’est une chaine");
} else {
    alert("ce n’est pas une chaine !");
}
```

### Astuces

#### Comment savoir si une variable contient un tableau ?

Réponse, on teste si l'objet possède une propriété `length`.

```javascript
let tableau = ['je','suis','un','tableau'];

// Si est un objet et possède un propriété length
if(typeof tableau === 'object' && tableau.hasOwnProperty('length')) {
    alert("C'est un tableau !");
} else {
    alert("Ce n'est PAS un tableau !");
}
```

#### Comment s'assurer qu'une variable est du type number et que c'est un nombre ?

Réponse, utiliser la fonction `isNaN()` qui retourne `true` si la valeur passée en paramètre n'est pas un nombre.

```javascript
let age = NaN;

// Si est de type number et est un nombre valide
if(typeof age === 'number' && !isNaN(age)) {
    alert("C'est un nombre !");
} else {
    alert("Ce n'est PAS un nombre !");
}
```

