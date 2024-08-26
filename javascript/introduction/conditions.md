# Conditions

JavaScript propose plusieurs structures conditionnelles qui permettent de contrôler le flux d'exécution de votre programme en fonction de certaines conditions.

## Structure `if...else`

La structure `if...else` permet d'exécuter un bloc de code si une condition est vraie, et un autre bloc si elle est fausse.

### **Exemple :**

```javascript
let a = 1;
let b = 2;

if (a < b) {
  console.log('Juste !');
} else {
  console.log('Faux !');
}
```

Dans cet exemple, puisque `a` est inférieur à `b`, le message `'Juste !'` sera affiché dans la console.

## Structures `if...else if...else`

Pour gérer plusieurs conditions, vous pouvez utiliser une série de `if...else if...else`. Cela aide à tester plusieurs conditions séquentiellement jusqu'à ce que l'une d'elles soit vraie.

### **Exemple :**

```javascript
let a = 1;
let b = 2;
let c = 3;

if (a > b) {
  console.log('A est plus grand que B');
} else if (a > c) {
  console.log('Mais A est plus grand que C');
} else {
  console.log('A est le plus petit');
}
```

Dans cet exemple, aucune des conditions `a > b` ou `a > c` n'est vraie, donc le message `'A est le plus petit'` sera affiché.

## L'opérateur ternaire

L'opérateur ternaire est le seul opérateur conditionnel en JavaScript qui comporte trois opérandes. Il est souvent utilisé comme raccourci pour les déclarations `if...else`.

### **Syntaxe :**

```javascript
condition ? expressionSiVrai : expressionSiFaux;
```

### **Exemples :**

*   **Initialisation avec condition :**

    ```javascript
    let solde = 200;
    let typeSolde = (solde < 0) ? "Négatif" : "Positif"; // "Positif"
    ```
*   **Fonction utilisant l'opérateur ternaire :**

    ```javascript
    // Si estMembre est vrai, retourne "$2.00", sinon "$10.00"
    function prixEntree(estMembre) {
      return (estMembre ? "$2.00" : "$10.00");
    }
    ```

## Sélection avec `switch`

La structure `switch` permet de sélectionner une parmi plusieurs branches possibles en fonction de la valeur d'une expression. Elle est utile lorsque vous avez plusieurs conditions basées sur la même variable.

### **Exemple :**

```javascript
let fruit = 'Bananes';

switch (fruit) {
  case 'Oranges':
    console.log('Les oranges sont à 2.55€ le kilo');
    break;
  case 'Mangues':
  case 'Bananes':
    console.log('Les mangues et bananes sont à 7.70€ le kilo');
    break;
  default:
    console.log('Désolé, nous ne vendons pas de ' + fruit + ' !');
}
```

**Résultat :** `'Les mangues et bananes sont à 7.70€ le kilo'`

**Explications :**

* Le `switch` évalue la valeur de `fruit`.
* Si `fruit` est `'Oranges'`, il affiche le message correspondant.
* Si `fruit` est `'Mangues'` ou `'Bananes'`, il affiche le message pour les mangues et bananes.
* Si aucune des conditions précédentes n'est remplie, le `default` est exécuté, affichant un message d'excuse.

**Note :** L'instruction `break` est utilisée pour sortir du `switch` une fois qu'un cas a été exécuté. Sans `break`, l'exécution continuerait dans les cas suivants (comportement appelé "fall-through").

## Conclusion

Les structures conditionnelles en JavaScript, telles que `if...else`, les opérateurs ternaires et les instructions `switch`, offrent une grande flexibilité pour contrôler le flux de votre programme en fonction des différentes situations. Comprendre leur fonctionnement et savoir quand les utiliser est essentiel pour écrire un code efficace et maintenable.

