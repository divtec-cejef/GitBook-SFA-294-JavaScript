---
description: >-
  Un objet String est utilisé afin de représenter et de manipuler une chaîne de
  caractères.
---

# String

Les chaînes de caractères sont utiles pour stocker des données qui peuvent être représentées sous forme de texte. Parmi les opérations les plus utilisées pour manipuler les chaînes de caractères, on a : la vérification de leur longueur avec [`length`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/String/length), la construction et la concaténation avec [les opérateurs `+` et `+=`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/Expressions\_and\_Operators#string\_operators), la recherche de sous-chaîne avec les méthodes [`includes()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/String/includes) ou [`indexOf()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/String/indexOf) ou encore l'extraction de sous-chaînes avec la méthode [`substring()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/String/substring).

### Créer des chaînes de caractères <a href="#creer_des_chaines_de_caracteres" id="creer_des_chaines_de_caracteres"></a>

Il est possible de créer des chaînes de caractères comme des valeurs primitives ou comme des objets avec le constructeur [`String()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/String/String) :

```
const string1 = "Une chaîne de caractères primitive";
const string2 = 'Là encore une valeur de chaîne de caractères primitive';
const string3 = `Et ici aussi`;
```

```
const string4 = new String("Un objet String");
```

Les valeurs littérales pour les chaînes de caractères peuvent être indiquées avec des **simples quotes (')**, **des doubles quotes (")** ou encore par **des accents graves (\`)**.&#x20;

Cette dernière forme permet de définir un [littéral de gabarit de chaîne de caractères](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Template\_literals) avec lequel on pourra interpoler des expressions dans une chaîne de caractères.

```javascript
let age = 35;
let maChaine = `texte`;

maChaine = `ligne de texte 1
 ligne de texte 2
 ligne de texte 3`;

maChaine = `Le capitaine a ${age} ans`;
```

### Accéder à un caractère <a href="#acceder_a_un_caractere" id="acceder_a_un_caractere"></a>

Il existe deux façons d'accéder à un caractère dans une chaîne. La première façon consiste à utiliser la méthode [`charAt()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/String/charAt) :

```
return 'chat'.charAt(2); // renvoie "a"
```

La seconde méthode, introduite avec ECMAScript 5, est de manipuler la chaîne comme un tableau, où les caractères sont les éléments du tableau et ont un indice correspondant à leur position :

```
return 'chat'[2]; // renvoie "a"
```

En utilisant la seconde notation, il est impossible de supprimer ou d'affecter une valeur à ces propriétés. En effet, les propriétés concernées ne sont ni accessibles en écriture ni configurables. Pour plus d'informations, voir la page de [`Object.defineProperty()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Object/defineProperty).

### Comparer des chaînes de caractères <a href="#comparer_des_chaines_de_caracteres" id="comparer_des_chaines_de_caracteres"></a>

Les développeurs C utilisent la fonction `strcmp()` pour comparer des chaînes de caractères. En JavaScript, il est possible d'utiliser [les opérateurs inférieur et supérieur ](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Operators):

```
let a = "a";
let b = "b";
if (a < b) { // true
  console.log(a + " est inférieure à " + b);
} else if (a > b) {
  console.log(a + " est supérieure à " + b);
} else {
  console.log(a + " et " + b + " sont égales.");
}
```

On peut obtenir un résultat semblable avec la méthode [`localeCompare()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/String/localeCompare) qui permet de prendre en compte la locale utilisée et qui est héritée par toutes les instances de `String`.

On notera que `a == b` compare les chaînes de caractères `a` et `b` de façon sensible à la casse. Si on souhaite comparer des chaînes sans être sensible à la casse, on pourra utiliser une fonction semblable à :

```
function isEqual(str1, str2) {
  return str1.toUpperCase() === str2.toUpperCase()
}
```

On utilise ici une conversion en majuscules plutôt qu'en minuscules, car cela cause certains problèmes de conversion pour certains caractères UTF-8.

### Échappement des caractères <a href="#echappement_des_caracteres" id="echappement_des_caracteres"></a>

En dehors des caractères classiques, des caractères spéciaux peuvent être encodés grâce à l'échappement :

| Code | Résultat               |
| ---- | ---------------------- |
| `\0` | Caractère nul          |
| `\'` | simple quote           |
| `\"` | double quote           |
| `\\` | barre oblique inversée |
| `\n` | nouvelle ligne         |
| `\r` | retour chariot         |
| `\v` | tabulation verticale   |
| `\t` | tabulation             |
| `\b` | retour arrière         |
| `\f` | saut de page           |
