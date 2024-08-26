# Conversions

En JavaScript, il est souvent nécessaire de convertir des nombres en chaînes de caractères et inversement. Voici les différentes méthodes disponibles pour ces conversions.

## Convertir des Nombres en Chaînes de Caractères

### Utiliser la Méthode Globale `String()`

La méthode globale `String()` permet de convertir un nombre en chaîne de caractères.

```javascript
let total = 123.56;
console.log(String(total)); // "123.56"
console.log(String(123)); // "123"
console.log(String(100 + 23)); // "123"
```

### Utiliser la Méthode `.toString()`

Une autre solution consiste à utiliser la méthode `.toString()` directement sur le nombre.

```javascript
let total = 123.56;
console.log(total.toString()); // "123.56"
console.log((123).toString()); // "123"
console.log((100 + 23).toString()); // "123"
```

### Utiliser l'Opérateur `+` pour la Concaténation

Avec l'opérateur `+` de concaténation, vous pouvez convertir un nombre en chaîne simplement en lui ajoutant une chaîne vide.

```javascript
let total = 123.56;
console.log(total + ""); // "123.56"
console.log(100 + "123"); // "100123"
console.log(100 + 23 + ""); // "123"
console.log(50 + " CHF"); // "50 CHF"
```

## Convertir une Chaîne de Caractères en Nombre

### Utiliser `parseInt(string, base)`

La méthode `parseInt()` convertit une chaîne en nombre entier. Le deuxième paramètre optionnel (`base`) permet de préciser la base numérique (base 10, base 2, etc.).

```javascript
// Conversion nombre entier en base 10
console.log(parseInt("35", 10)); // 35
​
// Conversion en base 2
console.log(parseInt("01010", 2)); // 10
​
// Conversion nombre entier (en base 10 si pas de deuxième paramètre)
console.log(parseInt("22 ans", 10)); // 22
​
// Conversion nombre entier
console.log(parseInt("33.1045", 10)); // 33
```

**Bonne Pratique :** Toujours inclure l'argument de base numérique pour éviter les ambiguïtés.

### Utiliser `parseFloat(string)`

La méthode `parseFloat()` convertit une chaîne en nombre flottant (décimal).

```javascript
// Conversion en nombre flottant
console.log(parseFloat("33.1045")); // 33.1045
​
// Conversion en nombre flottant, mais la virgule n'est pas prise en compte
console.log(parseFloat("33,1045")); // 33
```

### Utiliser l'Opérateur `+` Unaire

Une autre méthode pour convertir une chaîne en nombre consiste à utiliser l'opérateur `+` unaire. Il convertit une chaîne en nombre si possible.

```javascript
console.log(+"1.1"); // 1.1
console.log(+"123"); // 123
console.log(+"12.34abc"); // NaN, car "abc" n'est pas un nombre
```

### Not A Number (NaN)

`NaN` signifie "Not a Number" et est une valeur spéciale utilisée pour représenter un résultat qui n'est pas un nombre. Cette section est à compléter pour expliquer en détail le concept et son utilisation.

