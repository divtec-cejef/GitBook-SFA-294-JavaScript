## Conditions

### `if... else`

```javascript
// If Else
let a = 1;
let b = 2;

if (a < b) {
  console.log('Juste !');
} else {
  console.log('Faux !');
}


// Multi If Else 
let a = 1;
let b = 2;
let c = 3;

if (a > b) {
  console.log('A plus grand que B');
} else if (a > c) {
  console.log('Mais A est plus grand que C');
} else {
  console.log('A est le plus petit');
}
```



### L'opérateur (ternaire) conditionnel

L'**opérateur (ternaire) conditionnel** est le seul opérateur JavaScript qui comporte trois opérandes.

Cet opérateur est fréquemment utilisé comme raccourci pour la déclaration `if… else`

```javascript
//Initialisation avec condition
let solde = 200;
let typeSolde = (solde < 0) ? "Négatif" : "Positif"; //"Positif"

//Si estMembre est vrai alors retourne 2$ sinon 10$
function prixEntree(estMembre) {
  return (estMembre ? "$2.00" : "$10.00");
}
```



### Sélections avec `switch`

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

// Résultat : 'Les mangues et bananes sont à 7.70€ le kilo'
```

