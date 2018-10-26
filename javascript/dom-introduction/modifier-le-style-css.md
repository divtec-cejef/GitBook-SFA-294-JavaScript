---
description: en construction...
---

# Modifier le style CSS

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

\`\`



