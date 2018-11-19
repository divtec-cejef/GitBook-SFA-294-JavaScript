# Modifier le style CSS

## Element.style

La propriété `style` d'un élément représente son attribut HTML `style="color:red;"`.  Elle représente donc la **déclaration de style en-ligne** qui a la **priorité la plus haute** dans la cascade CSS.

Cependant, elle n'est **pas utile pour connaître le style de l'élément** en général, puisqu'elle ne représente que les déclarations CSS définies dans l'attribut style de l'élément, et pas celles qui viennent d'autres règles de style.

> Pour obtenir les valeurs de toutes les propriétés CSS pour un élément, il faut utiliser [`window.getComputedStyle(element)`](modifier-le-style-css.md#window-getcomputedstyle-element).

Pour ajouter ou modifier une déclaration CSS dans l'attribut style d'un élément on écrira

```javascript
Element.style.propriétéCSS = "valeur"
```

En JavaScript deux règles importantes concernant le CSS :

* les **valeurs sont toujours des chaines de caractères** `Element.style.padding = "4px"`. 
* les traits d'union `-` des **propriétés CSS composées de plusieurs mots-clés** comme `border-color`, sont remplacés par une **camélisation** `borderColor`.

![Cam&#xE9;lisation des propri&#xE9;t&#xE9;s CSS](../../.gitbook/assets/image%20%281%29.png)

Ci-après, quelques exemples de déclaration CSS et leur équivalence en JavaScript:

| Déclaration CSS | JavaScript |
| :--- | :--- |
| `color: #2ecc71;` | `Element.style.color = "#2ecc71";` |
| `font-size: 2em;` | `Element.style.fontSize = "2em";` |
| `background-color: red;` | `Element.style.backgroundColor = "red";` |
| `border-top-width : 2px;` | `Element.style.borderTopWidth = "2px";` |
| `color: #333;` | `Element.style.color = "#333";` |

### Exemple

```javascript
let intros = document.getElementsByClassName("intro");

for (let i = 0; i < intros.length; i = i + 1) {
    intros[i].style.fontSize = '1.5em';
    intros[i].style.backgroundColor = 'lime';
}
```

## window.getComputedStyle\(element\)

La méthode `window.getComputedStyle()` retourne un objet contenant la valeur calculée finale de toutes les propriétés CSS d'un élément.

{% hint style="danger" %}
L'objet retourné est en **lecture seule**.
{% endhint %}

### Exemple

```javascript
// Récupère #intro
const INTRO = document.getElementById('intro');
// Récupère le style CSS de #intro
let styleINTRO = window.getComputedStyle(INTRO);
// Affiche la valeur de la propriété CSS top de #intro
console.log( styleINTRO.getPropertyValue('top') );
```

{% embed url="https://codepen.io/fallinov/pen/EdMxzL?editors=0011" %}



