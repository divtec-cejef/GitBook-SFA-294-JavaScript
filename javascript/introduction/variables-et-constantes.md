# Variables et constantes

## Conventions

* Nom des variables en **camelCase** :  `nomClient`
* Noms des constantes en **MAJUSCULE** avec mots clés séparés par un souligné : `AGE_MAX`
* Une variable doit porter un **nom représentatif de ce qu'elle contient**

{% hint style="danger" %}
JavaScript est **sensible à la casse** : `NomDeFamille` ≠ `nomdefamille`&#x20;
{% endhint %}

## Déclarer des variables et constantes

```javascript
// Variables
var personneNom = "Dinateur";
let personneAge = 22;

// Constantes
const URL = "http://kode.ch";
const AGE_MAX = 65;
const langues = ['FR','EN'];
const personne = { age: 20 };
```

{% hint style="success" %}
#### Bonne pratique

Écrire en :

* **majuscule** les constantes contenant des **valeurs** : `const MAX = 33;`&#x20;
* **minuscule** les constantes contenant des **références**  : `const ids = [12, 44];`&#x20;
{% endhint %}

{% hint style="info" %}
Les variables JavaScript ne sont **pas typées** !

On peut initialiser une variable avec un entier puis lui affecter une chaîne de caractères sans déclencher d’erreur.
{% endhint %}

{% content-ref url="types.md" %}
[types.md](types.md)
{% endcontent-ref %}

## Variables avec `var` ou `let` ⁣ ?

Il existe deux instructions pour déclarer des variables depuis la sixième édition du standard ECMAScript (ES6 en abrégé).

* `let` permet de déclarer une **variable dont la portée est celle du bloc courant**.
* `var` quant à lui, permet de définir une **variable globale ou locale à une** **fonction** (sans distinction des blocs utilisés dans la fonction).

```javascript
// Avec var
function varTest() {
  var x = 1;
  if (true) {
    var x = 2;  // c'est la même variable !
    console.log(x);  // 2
  }
  console.log(x);  // 2
}

// Avec let
function letTest() {
  let x = 1;
  if (true) {
    let x = 2;  // c'est une variable différente
    console.log(x);  // 2
  }
  console.log(x);  // 1
}
```

#### **Conclusion**

Utilisez `let` de préférence à `var` pour éviter les pièges liés à la portée des variables. Réservez `const` pour les valeurs qui ne doivent pas être réassignées, en respectant les conventions de nommage pour maintenir un code clair et lisible.
