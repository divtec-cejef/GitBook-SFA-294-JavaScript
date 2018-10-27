# Modifier le style CSS

La propriété `style` d'un élément représente son attribut HTML `style="..."`.  Elle représente donc la **déclaration de style en-ligne** qui a la **priorité la plus haute** dans la cascade CSS.

Cependant, elle n'est **pas utile pour connaître le style de l'élément** en général, puisqu'elle ne représente que les déclarations CSS définies dans l'attribut style de l'élément, et pas celles qui viennent d'autres règles de style.

{% hint style="info" %}
Pour obtenir les valeurs de toutes les propriétés CSS pour un élément, il faut utiliser [`window.getComputedStyle`](https://developer.mozilla.org/fr/DOM/window.getComputedStyle).
{% endhint %}



```javascript
let intros = document.getElementsByClassName("intro");

for (let i = 0; i < intros.length; i = i + 1) {
    intros[i].style.fontSize = '1.5em';
    intros[i].style.backgroundColor = 'lime';
}
```

{% hint style="info" %}
Les “-” des propriétés CSS composées de plusieurs mots-clés, sont remplacés par une camélisation :

`border-color => borderColor  
font-size => fontSize`
{% endhint %}

### window.getComputedStyle\(element\)

La méthode `window.getComputedStyle()` retourne un objet contenant la valeur calculée finale de toutes les propriétés CSS d'un élément. L'objet retourné est en **lecture seule**.

```javascript
// Récupère #intro
const INTRO = document.getElementById('intro');
// Récupère le style CSS de #intro
let styleINTRO = window.getComputedStyle(INTRO);
// Affiche la valeur de la propriété CSS top de #intro
console.log( styleINTRO.getPropertyValue('top') );
```

{% embed url="https://codepen.io/fallinov/pen/EdMxzL?editors=1111" caption="Pen getComputedStyle " %}



