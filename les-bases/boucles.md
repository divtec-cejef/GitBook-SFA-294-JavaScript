# Boucles

## While

```javascript
let i = 0;
while (i < 10) {
  console.log(i);
  i += 1 // Eviter l'utilisation de "i++". Préférer "++i" ou "i += 1"
}
```

## Do...while

```javascript
let i = 0;
do {
  console.log(i);
  i += 1 // Eviter l'utilisation de "i++". Préférer "++i" ou "i += 1"
} while (i < 10)
```

## For

```javascript
//Eviter l'utilisation de "i++". Préférer "++i" ou "i += 1"
for (let i = 0; i < 10; ++i) { 
   console.log(i);
}
```

## For...in

L'**instruction for...in** permet d'itérer sur les propriétés d'un objet.

```javascript
//Création d'un objet personne
let personne = {nom: "Dinateur", prenom: "Laure", age: 33};

//Parcours et affiche le nom et la valeur des propriétés de personne
for (let prop in personne) {
    console.log(prop + ' => ' + personne[prop])
}

/* Résultat :
    nom => Dinateur
    prenom => Laure
    age => 33
*/
```

