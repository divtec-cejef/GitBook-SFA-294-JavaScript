# String

En JavaScript, un objet `String` est utilisé pour représenter et manipuler une chaîne de caractères. Les chaînes de caractères sont fondamentales pour stocker et gérer des données textuelles. Elles permettent une variété d'opérations, comme la vérification de la longueur, la concaténation, la recherche de sous-chaînes, et l'extraction de portions spécifiques.

## Créer des Chaînes de Caractères

Il est possible de créer des chaînes de caractères soit comme des valeurs primitives, soit comme des objets à l'aide du constructeur `String()` :

```javascript
const string1 = "Une chaîne de caractères primitive";
const string2 = 'Là encore une valeur de chaîne de caractères primitive';
const string3 = `Et ici aussi`;
const string4 = new String("Un objet String");
```

* **Littéraux de chaînes** : Les valeurs littérales de chaînes peuvent être délimitées par des simples quotes (`'`), des doubles quotes (`"`), ou des accents graves (\`\`).
* **Objet String** : La création d'une chaîne en tant qu'objet (`new String("texte")`) est rarement nécessaire et peut être évitée dans la plupart des cas.

### Template Literals (Littéraux de Gabarits)

Introduits avec ECMAScript 2015 (ES6), les **template literals** permettent d'interpoler des expressions dans une chaîne de caractères, de manière plus lisible et plus puissante que la concaténation traditionnelle :

```javascript
let age = 35;
let maChaine = `Le capitaine a ${age} ans`;
​
maChaine = `ligne de texte 1
ligne de texte 2
ligne de texte 3`;
```

* **Interpolation** : L'expression `${expression}` permet d'insérer dynamiquement des valeurs dans la chaîne de caractères.
* **Multilignes** : Les template literals permettent également de créer des chaînes de caractères sur plusieurs lignes sans utiliser de caractère d'échappement.

## Accéder à un Caractère

Il existe deux façons d'accéder à un caractère spécifique dans une chaîne de caractères :

1.  **Méthode `charAt()`** :

    ```javascript
    return 'chat'.charAt(2); // renvoie "a"
    ```

    Cette méthode retourne le caractère à la position spécifiée (ici, à l'index 2).
2.  **Accès via la notation par indices** :

    ```javascript
    return 'chat'[2]; // renvoie "a"
    ```

    Cette notation traite la chaîne comme un tableau, où chaque caractère est un élément du tableau.

**Note :** En utilisant la notation par indices, les caractères de la chaîne sont en lecture seule. Il est impossible de les modifier ou de les supprimer directement par cette méthode.

## Comparer des Chaînes de Caractères

En JavaScript, il est possible de comparer des chaînes de caractères en utilisant les opérateurs de comparaison `<`, `>`, `<=`, `>=` :

```javascript
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

Pour une comparaison plus fine, prenant en compte la locale, vous pouvez utiliser la méthode `localeCompare()` :

```javascript
if (a.localeCompare(b) < 0) {
  console.log(a + " est inférieure à " + b);
} else if (a.localeCompare(b) > 0) {
  console.log(a + " est supérieure à " + b);
} else {
  console.log(a + " et " + b + " sont égales.");
}
```

### **Comparaison Insensible à la Casse**&#x20;

Pour comparer des chaînes de caractères sans tenir compte de la casse, vous pouvez convertir les chaînes en majuscules ou minuscules :

```javascript
function isEqual(str1, str2) {
  return str1.toUpperCase() === str2.toUpperCase();
}
```

Il est généralement préférable de convertir en majuscules pour éviter certains problèmes de conversion liés aux caractères UTF-8.

## Échappement des Caractères

Pour inclure des caractères spéciaux dans une chaîne de caractères, vous pouvez utiliser des séquences d'échappement&#x20;

| Code | Résultat               |
| ---- | ---------------------- |
| `\0` | Caractère nul          |
| `\'` | Simple quote           |
| `\"` | Double quote           |
| `\\` | Barre oblique inversée |
| `\n` | Nouvelle ligne         |
| `\r` | Retour chariot         |
| `\v` | Tabulation verticale   |
| `\t` | Tabulation             |
| `\b` | Retour arrière         |
| `\f` | Saut de page           |

## Manipulation de Chaînes

### Extraire des chaînes :  `slice()`, `substring()` et `split()`

*   **Méthode `slice()`** : Pour extraire une section d'une chaîne de caractères.

    ```javascript
    let texte = "Hello, World!";
    let partie = texte.slice(0, 5); // "Hello"
    ```
* **Méthode `substring()`** : Similaire à `slice()`, mais sans accepter d'index négatifs.
*   **Méthode `split()`** : Pour diviser une chaîne de caractères en un tableau de sous-chaînes, en fonction d'un séparateur.

    ```javascript
    let texte = "apple,banana,pear";
    let fruits = texte.split(","); // ["apple", "banana", "pear"]
    ```

### Manipulation de la Casse

*   **Méthode `toUpperCase()`** : Convertit une chaîne en majuscules.

    ```javascript
    let texte = "hello";
    console.log(texte.toUpperCase()); // "HELLO"
    ```
*   **Méthode `toLowerCase()`** : Convertit une chaîne en minuscules.

    ```javascript
    let texte = "HELLO";
    console.log(texte.toLowerCase()); // "hello"
    ```

### Recherche de Sous-chaînes

*   **Méthode `includes()`** : Pour vérifier si une chaîne contient une sous-chaîne donnée.

    ```javascript
    let phrase = "Bonjour le monde";
    console.log(phrase.includes("le")); // true
    ```
*   **Méthode `indexOf()`** : Pour trouver l'index de la première occurrence d'une sous-chaîne.

    ```javascript
    let texte = "Hello, World!";
    console.log(texte.indexOf("World")); // 7
    ```
*   **Méthode `startsWith()` et `endsWith()`** : Pour vérifier si une chaîne commence ou se termine par une sous-chaîne spécifique.

    ```javascript
    let texte = "Hello, World!";
    console.log(texte.startsWith("Hello")); // true
    console.log(texte.endsWith("!")); // true
    ```

### Substitution de Sous-chaînes

*   **Méthode `replace()`** : Pour remplacer une sous-chaîne par une autre.

    ```javascript
    let texte = "Hello, World!";
    let nouveauTexte = texte.replace("World", "Everyone");
    console.log(nouveauTexte); // "Hello, Everyone!"
    ```
*   **Méthode `replaceAll()`** : Introduit avec ECMAScript 2021, cette méthode remplace toutes les occurrences d'une sous-chaîne par une autre.

    ```javascript
    let texte = "banane, banane, banane";
    let nouveauTexte = texte.replaceAll("banane", "pomme");
    console.log(nouveauTexte); // "pomme, pomme, pomme"
    ```

### Trimming — supprimer les espaces

*   **Méthode `trim()`** : Pour enlever les espaces blancs **au début et à la fin** d'une chaîne.

    ```
    let texte = "   Hello, World!   ";
    ```

\
