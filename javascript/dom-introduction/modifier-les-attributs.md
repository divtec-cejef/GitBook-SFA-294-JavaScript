# Modifier les attributs

```javascript
let colmar = document.getElementById("colmar");
colmar.href   = 'http://www.colmar.fr';
colmar.target = '_blank';

// Avec la méthode setAttribute
colmar.setAttribute('href', 'http://www.colmar.fr');
colmar.setAttribute('target', '_blank');
```

{% hint style="warning" %}
Pour modifier les attributs HTML non-standard utiliser `setAttribute()`
{% endhint %}



