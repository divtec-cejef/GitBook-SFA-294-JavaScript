# Opérateurs

JavaScript propose une variété d'opérateurs qui permettent d'effectuer des calculs, de manipuler des chaînes de caractères, de comparer des valeurs et de gérer l'affectation de valeurs.

## Opérateurs Numériques

Les opérateurs numériques en JavaScript incluent :

* **Addition (`+`)**
* **Soustraction (`-`)**
* **Multiplication (`*`)**
* **Division (`/`)**
* **Modulo (`%`)** : Renvoie le reste de la division de deux nombres.

## Opérateurs d'Affectation

Les valeurs sont affectées à l'aide de l'opérateur `=`. Il existe également des opérateurs d'affectation combinés, qui effectuent une opération et affectent la valeur en une seule étape :

```javascript
x += 5; // Équivaut à x = x + 5;
x -= 3; // Équivaut à x = x - 3;
```

### Incrémentation et Décrémentation

Vous pouvez utiliser les opérateurs `++` et `--` pour incrémenter ou décrémenter une valeur de 1. Ces opérateurs peuvent être utilisés en préfixe ou en suffixe, mais leur comportement diffère :

* **Suffixe (`x++`)** : L'opération est effectuée après l'affectation.
* **Préfixe (`++x`)** : L'opération est effectuée avant l'affectation.

#### **Exemples :**

```javascript
let x = 10;
let y = 0;

y = x++; // y = 10, x = 11 (opérateur suffixe)
y = ++x; // y = 11, x = 11 (opérateur préfixe)
```

## Opérateur de Concaténation de Chaînes

L'opérateur `+` est également utilisé pour concaténer des chaînes de caractères :

```javascript
"coucou" + " monde"; // "coucou monde"
```

Lorsque vous additionnez une chaîne à un nombre, JavaScript convertit automatiquement les valeurs en chaînes :

```javascript
"3" + 4 + 5; // "345"
3 + 4 + "5"; // "75"
```

**Astuce :** Ajouter une chaîne vide à une valeur est une méthode rapide pour la convertir en chaîne.

### Chaînes de Caractères sur Plusieurs Lignes

Pour créer des chaînes de caractères sur plusieurs lignes, vous pouvez les concaténer :

```javascript
let texteYoda = "La peur est le chemin vers le côté obscur : " +
                "la peur mène à la colère, " +
                "la colère mène à la haine, " +
                "la haine mène à la souffrance.";
```

Depuis ECMAScript 6 (ES6), il est recommandé d'utiliser les **Template Literals** pour une syntaxe plus propre :

```javascript
let texteYoda = `La peur est le chemin vers le côté obscur :
                la peur mène à la colère,
                la colère mène à la haine,
                la haine mène à la souffrance.`;
```

## Opérateurs de Comparaison

Les comparaisons en JavaScript utilisent des opérateurs tels que :

* **Inférieur (`<`)**
* **Supérieur (`>`)**
* **Inférieur ou égal (`<=`)**
* **Supérieur ou égal (`>=`)**

Ces opérateurs fonctionnent à la fois pour les chaînes et les nombres.

### Égalité

L'égalité en JavaScript peut être délicate. L'opérateur `==` (double égal) effectue une conversion de type pour comparer les valeurs, ce qui peut parfois mener à des résultats inattendus :

```javascript
123 == "123"; // true
1 == true;    // true
```

Pour éviter ces conversions automatiques, utilisez l'opérateur `===` (triple égal), qui compare à la fois les valeurs et les types :

```javascript
123 === "123"; // false
true === true; // true
```

### Inégalité

Les opérateurs `!=` et `!==` existent également pour vérifier l'inégalité. Le premier effectue une conversion de type comme `==`, tandis que le second compare les types et les valeurs.

***

## Conclusion

Les opérateurs en JavaScript offrent une grande flexibilité pour effectuer des calculs, manipuler des chaînes de caractères et comparer des valeurs. Il est important de comprendre comment ils fonctionnent, en particulier les différences entre les opérateurs d'égalité `==` et `===`, pour éviter des erreurs subtiles dans votre code.

