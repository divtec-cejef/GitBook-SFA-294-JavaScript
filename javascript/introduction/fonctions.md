# Fonctions

* Bloc de code conçu pour effectuer une tâche particulière.
* Est exécuté quand "quelque chose" l'invoque \(l'appelle\).
* Seul moyen de créer un nouvelle portée en JavaScript avant ES6
* En JS, les fonctions sont la base de toutes interactions

## Créer et appeler un fonction

Si on ne spécifie pas de valeur de retour à une fonction, elle retournera `undefined`.

```javascript
function nomFonction() {...}

function ditBonjour() {
    console.log("Bonjour !");
}

ditBonjour(); // undefined
// Dans la console : "Bonjour !"
```

### Paramètres

```javascript
function nomFonction(p1,p2,...) {...}

function ditBonjour(nom, titre) {
console.log("Bonjour " + titre + " " + nom + "!");
}

ditBonjour("James", "Monsieur"); // undefined
// Dans la console : "Bonjour Monsieur James!"
```

### Valeur par défaut des paramètres

Avant ES6, on ne pouvait pas définir de valeur par défaut.

```javascript
function ditBonjour(nom, titre) {
    if (titre === undefined) {
        titre = "Prince";
    }
    
    console.log("Bonjour " + titre + " " + nom + "!");
}

ditBonjour("James"); // undefined

// Dans la console : "Bonjour Prince James!"
```

Si vous travailler avec ES6, le lien suivant peut vous intéresser :

{% page-ref page="../javascript-moderne/parametres-par-default.md" %}

## Retourner une valeur

```javascript
function ditBonjour(nom, titre) {
    if (titre === undefined) {
        titre = "Prince";
    }
    
    return "Bonjour " + titre + " " + nom + "!";
}

ditBonjour("James"); // "Bonjour Prince James!"

```

## Sortir d'une fonction 

En utilisant un `return`on peut forcer la sortie d'un fonction. Tout le code de la fonction situer après le `return` ne sera donc pas exécuté.

```javascript
function ditBonjour(nom, titre) {
    if (titre === undefined){
    return; // Sort, stoppe, la fonction
    }
   
    return "Bonjour " + titre + " " + nom + "!";
}

ditBonjour("James"); //undefined
```

## Fonctions anonymes

En JavaScript, les fonctions sont des objets, on peut donc stocker des fonctions dans une variable.

```javascript
var maFonction = function() {
    return "Bonjour de ma fonction";
}
maFonction(); // "Bonjour de ma fonction"
```

{% hint style="info" %}
Utiliser un max les fonctions avec des noms, cela vous facilitera la vie lors du débogage.

Si une fonction anonyme déclenche une erreur, dans la console vous aurez comme information :  
  
 _Erreur déclenchée par "anonymous function"_  
  
 … oui mais laquelle ???
{% endhint %}

## Fonction “IIFE” Immediately Invoked Function Expression

En plaçant tout votre code dans une "IFFE", cela empêchera vos variables d'entrez en collision avec d'autres scripts. C'est une bonne pratique à respecter si vous utiliser des librairies JS externes.

```javascript
(function () {
    // Placer tout le code de votre application ici...
    console.log("Auto-exécution");
})();
```

