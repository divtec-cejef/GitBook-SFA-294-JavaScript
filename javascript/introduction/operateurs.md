# Opérateurs

Les opérateurs numériques en JavaScript sont `+`, `-`, `*`, `/` et `%` \(opérateur de reste\).

Les valeurs sont affectées à l'aide de `=` et il existe également des opérateurs d'affectation combinés comme `+=` et `-=`.

```javascript
// Les deux instructions suivantes sont équivalentes
x += 5;
x = x + 5;
```

Vous pouvez utiliser `++` et `--` respectivement pour incrémenter et pour décrémenter. Ils peuvent être utilisés comme opérateurs préfixes ou suffixes.

{% hint style="danger" %}
Attention, utiliser `++` et `--` en suffixe ou en préfixe ne fonctionne pas de la même manière.
{% endhint %}

En **suffixe**, l'opération s’effectuera **après l'affectation** :

```javascript
let x = 10;
let y = 0;

y = x++; // y = 10 et x = 11
```

En **préfixe**, l'opération s’effectuera **avant l'affectation** :

```javascript
let x = 10;
let y = 0;

y = ++x; // y = 11 et x = 11
```

## Opérateur de concaténation de chaines

L'opérateur `+` permet également de concaténer des chaînes :

```javascript
"coucou" + " monde" // "coucou monde"
```

Si vous additionnez une chaîne à un nombre \(ou une autre valeur\), tout est d'abord converti en une chaîne. Ceci pourrait vous surprendre :

```javascript
"3" + 4 + 5; // "345"
3 + 4 + "5"; // "75"
```

> L'ajout d'une chaîne vide à quelque chose est une manière utile de la convertir en une chaîne.

###  Chaines de caractères sur plusieurs lignes

Le plus simple est de créer plusieurs chaines de caractères et de le concaténer.

```javascript
let texteYoda = "La peur est le chemin vers le côté obscur : " +
                "la peur mène à la colère, " +
                "la colère mène à la haine, " +
                "la haine mène à la souffrance.";

// "La peur est le chemin vers le côté obscur : la peur mène à la colère, la colère mène à la haine, la haine mène à la souffrance."
```

Autre solution depuis ES6, utiliser les [Template Literals](../javascript-moderne/template-literals.md).

## Opérateurs de comparaison

Les **comparaisons** en JavaScript se font à l'aide des opérateurs `<`, `>`, `<=` et `>=`. Ceux-ci fonctionnent tant pour les chaînes que pour les nombres.

L'égalité est un peu moins évidente. L'opérateur double égal effectue une équivalence si vous lui donnez des types différents, ce qui donne parfois des résultats intéressants :

```javascript
123 == "123"; // true
1 == true;    // true
```

Pour éviter les calculs d'équivalences de types, **utilisez l'opérateur triple égal** :

```javascript
123 === "123"; //false
true === true; // true
```

Les opérateurs `!=` et `!==` existent également.

