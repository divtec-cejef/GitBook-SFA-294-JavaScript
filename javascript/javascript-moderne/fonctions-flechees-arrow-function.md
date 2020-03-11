# Fonctions fléchées \(Arrow Function\)

## Les bases

Les fonctions fléchées ont été introduites dans ES6. Elles permettent d'écrire un de fonction de manière raccourcie :

```javascript
// Fonction régulière
hello = function() {
  return "Hello World!";
}

// Avec une fonction fléchée
hello = () => {
  return "Hello World!";
}

// On peut faire encore plus court ! 
// Si la fonction ne comporte qu'une seule déclaration et renvoie une valeur,
// vous pouvez supprimer les parenthèses et le mot-clé return :
hello = () => "Hello World!";

// Même chose avec un paramètre
hello = (val) => "Hello " + val; 

// Si il n'y a qu'un seul paramètre, on peut aussi supprimer les parenthèses
hello = val => "Hello " + val;
```

## Qu'en est-il de `this` !

Le traitement de `this` n'est pas le même dans les fonctions de fléchées que dans les fonctions régulières.

{% hint style="danger" %}
En bref, les fonctions fléchées n'injecte pas l'objet `this`, donc ne l'utilisez pas !
{% endhint %}

Dans les **fonctions régulières**, `this` représente l'**objet qui appelle la fonction**, qui peut être la fenêtre, le document, un bouton ou autre.

Dans les **fonctions fléchées**, `this` représente toujours l'**objet qui a créé la fonction fléchée**, s'il y en a eu un**.**

Comme le présente l'exemple ci-après, l'objet `this` est `undefined` dans la fonction fléchée.

```javascript
// Fonction régulière, this représente l'objet qui a appelé la fonction
hello1 = function() {
  alert(this.id)
}
document.getElementById("btn1").addEventListener("click", hello1);
// Résultat: btn2

// Fonction fléchée, this n'existe pas
hello2 = () => {
 alert(this.id)
}
document.getElementById("btn2").addEventListener("click", hello2);
// Résultat: undefined
```

{% embed url="https://codepen.io/fallinov/embed/VwLQPyj?height=300&theme-id=26660&default-tab=js,result" %}



