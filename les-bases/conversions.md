## Conversions

### Convertir des nombres en chaines de caractères

The global method **String()** can convert numbers to strings.

It can be used on any type of numbers, literals, variables, or expressions:

#### Example

  String(x)         // returns a string from a number variable x
  String(123)       // returns a string from a number literal 123
  String(100 + 23)  // returns a string from a number from an expression 

### Convertir une chaîne de caractères en nombre

Il existe deux méthodes :

- `parseInt(string, base)`
- `parseFloat(string)`

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

> Une bonne pratique pour `parseInt()` est de toujours inclure l'argument qui indique dans quelle base numérique le résultat doit être renvoyé (base 2, base 10...). 



#### L'opérateur + unaire

Une autre méthode pour récupérer un nombre à partir d'une chaîne de caractères consiste à utiliser l'opérateur `+`.

```javascript
"1.1" + "1.1" = "1.11.1"
+"1.1" = 1.1 // fonctionne seulement avec le + unaire
```



#### Not A Number

TODO - ...