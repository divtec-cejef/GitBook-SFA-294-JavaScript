---
description: >-
  Un objet String est utilisé afin de représenter et de manipuler une chaîne de
  caractères.
---

# String

### Description <a href="#description" id="description"></a>

Les chaînes de caractères sont utiles pour stocker des données qui peuvent être représentées sous forme de texte. Parmi les opérations les plus utilisées pour manipuler les chaînes de caractères, on a : la vérification de leur longueur avec [`length`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/String/length), la construction et la concaténation avec [les opérateurs `+` et `+=`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/Expressions\_and\_Operators#string\_operators), la recherche de sous-chaîne avec les méthodes [`includes()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/String/includes) ou [`indexOf()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/String/indexOf) ou encore l'extraction de sous-chaînes avec la méthode [`substring()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/String/substring).

#### [Créer des chaînes de caractères](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/String#cr%C3%A9er\_des\_cha%C3%AEnes\_de\_caract%C3%A8res) <a href="#creer_des_chaines_de_caracteres" id="creer_des_chaines_de_caracteres"></a>

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
