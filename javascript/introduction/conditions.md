# Conditions

En JavaScript, les conditions permettent d'exécuter du code en fonction de certaines situations. Voici les structures de conditions les plus courantes.

## Structure `if...else`

La structure `if...else` permet d'exécuter un bloc de code si une condition est vraie, et un autre bloc si elle est fausse.

```javascript
javascriptCopy codelet a = 1;
let b = 2;

if (a < b) {
  console.log('Juste !');
} else {
  console.log('Faux !');
}
```

## Structure `if...else if`

Lorsque vous avez plusieurs conditions à tester successivement, vous pouvez utiliser la structure `if...else if`. Elle permet de tester plusieurs conditions dans un seul bloc de code :

```javascript
javascriptCopy codelet a = 1;
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

### Utilisation de `if` avec `return`

Dans certaines situations, il est préférable d'utiliser des `if` avec `return` pour simplifier la logique et éviter des `else` imbriqués :

```javascript
javascriptCopy codefunction comparerValeurs(a, b, c) {
  if (a > b) {
    return 'A est plus grand que B';
  }
  if (a > c) {
    return 'Mais A est plus grand que C';
  }
  return 'A est le plus petit';
}

console.log(comparerValeurs(1, 2, 3)); // "A est le plus petit"
```

## L'Opérateur Conditionnel (Ternaire)

L'opérateur conditionnel (ternaire) est une façon compacte d'écrire des conditions. C'est le seul opérateur JavaScript qui prend trois opérandes : une condition, une expression à exécuter si la condition est vraie, et une autre si elle est fausse.

```javascript
javascriptCopy codelet solde = 200;
let typeSolde = (solde < 0) ? "Négatif" : "Positif"; // "Positif"
```

Le ternaire est souvent utilisé pour des conditions simples :

```javascript
javascriptCopy codefunction prixEntree(estMembre) {
  return estMembre ? "$2.00" : "$10.00";
}

console.log(prixEntree(true));  // "$2.00"
console.log(prixEntree(false)); // "$10.00"
```

## Sélections avec `switch`

La structure `switch` permet de comparer une même valeur à plusieurs cas possibles et d'exécuter du code en fonction du cas correspondant.

```javascript
javascriptCopy codelet fruit = 'Bananes';

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

### Exemple de `switch` avec `return`

Dans une fonction, vous pouvez utiliser `switch` avec `return` pour simplifier la structure :

```javascript
javascriptCopy codefunction prixFruit(fruit) {
  switch (fruit) {
    case 'Oranges':
      return 'Les oranges sont à 2.55€ le kilo';
    case 'Mangues':
    case 'Bananes':
      return 'Les mangues et bananes sont à 7.70€ le kilo';
    default:
      return 'Désolé, nous ne vendons pas de ' + fruit + ' !';
  }
}

console.log(prixFruit('Bananes')); // "Les mangues et bananes sont à 7.70€ le kilo"
```

Utiliser `return` dans un `switch` permet de sortir de la fonction immédiatement après avoir trouvé le cas correspondant.

***

## Conclusion

Les conditions en JavaScript offrent une grande flexibilité pour diriger le flux d'exécution du programme. Utiliser des `if` avec `return` au lieu de `if...else` en cascade peut rendre le code plus clair et plus facile à maintenir. Cependant, le `if...else if` reste un outil précieux lorsqu'il s'agit de tester plusieurs conditions successives. Le `switch` est utile pour les comparaisons multiples, et l'opérateur ternaire est une manière concise de gérer des conditions simples.
