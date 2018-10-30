# Conversions

## Convertir des nombres en chaines de caractères

### String\(\)

La méthode globale `String()` permet de convertir des nombres en chaines.

```javascript
let total = 123.56;
String(total); // "123.56"
String(123); // "123"
String(100 + 23); // "123"
```

### .toString\(\)

Autre solution utiliser la méthode `.toString()`.

```javascript
let total = 123.56;
total.toString(); // "123.56"
123.toString(); // "123"
(100 + 23).toString(); // "123"
```

### Opérateur + concaténation

En utilisant l'opérateur `+` de concaténation, il suffit d'ajouter une chaine au nombre.

```javascript
let total = 123.56;
total + ""; // "123.56"
100 + "123"; // "100123"
100 + 23 + ""; //"123"
50 + " CHF"; // "50 CHF"
```

## Convertir une chaîne de caractères en nombre

Il existe deux méthodes :

* `parseInt(string, base)`
* `parseFloat(string)`

```javascript
// Conversion nombre entier en base 10
parseInt("35", 10); // 35

// Conversion en base 2
parseInt("01010",2); // 10

// Conversion nombre entier (en base 10 si pas de deuxième paramètre)
parseInt("22 ans"); // 22

// Conversion nombre entier
parseInt("33.1045"); //33

// Conversion en nombre flottant
parseFloat("33.1045"); //33.1045

// Conversion en nombre flottant
parseFloat("33,1045"); //33 - la virgule n'est pas prise en compte
```

> Une bonne pratique pour `parseInt()` est de toujours inclure l'argument qui indique dans quelle base numérique le résultat doit être renvoyé \(base 2, base 10...\).

### Opérateur + unaire

Une autre méthode pour récupérer un nombre à partir d'une chaîne de caractères consiste à utiliser l'opérateur `+`.

```javascript
+"1.1" = 1.1 // fonctionne seulement avec le + unaire
```

### Not A Number

TODO - ...

