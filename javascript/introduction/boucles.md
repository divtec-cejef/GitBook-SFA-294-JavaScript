# Boucles

## While

```javascript
let i = 0;
while (i < 4) {
  console.log(i);
  i += 1 // Eviter l'utilisation de "i++". Préférer "++i" ou "i += 1"
}

// 0 
// 1
// 2
// 3
```

## Do...while

```javascript
let i = 0;
do {
  console.log(i);
  i += 1 // Eviter l'utilisation de "i++". Préférer "++i" ou "i += 1"
} while (i < 4)

// 0 
// 1
// 2
// 3
```

## For

```javascript
//Eviter l'utilisation de "i++". Préférer "++i" ou "i += 1"
for (let i = 0; i < 4; ++i) { 
   console.log(i);
}

// 0 
// 1
// 2
// 3
```

## For..of

L'instruction `for...of` permet de créer une boucle qui parcourt un objet itérable \(Array, Map, Set, String, TypedArray, etc.\) et qui permet d'exécuter une ou plusieurs instructions pour la valeur de chaque propriété.

```javascript
let animaux = [ '🐔', '🐷', '🐑', '🐇'];

for (let animal of animaux) {
  console.log(animal);
}

// 🐔
// 🐷
// 🐑
// 🐇
```

## For...in

L'instruction `for...in` permet d'itérer sur les propriétés d'un objet.

```javascript
//Création d'un objet personne
let personne = {
   nom: "Dinateur",
   prenom: "Laure",
   age: 33
};
//Parcours et affiche le nom et la valeur des propriétés de personne
for (let prop in personne) {
   console.log(prop + " => " + personne[prop]);
}

// nom => Dinateur
// prenom => Laure
// age => 33
```

