# Modifier les attributs

Les attributs standard HTML sont accessible comme propriété de l'objet représentant l'élément HTML. On peut donc y accéder en lecture et écriture en écrivant : `elementHTML.nomAttribut`

{% hint style="warning" %}
Pour modifier les attributs HTML non-standard utiliser `setAttribute()`
{% endhint %}

```markup
<h1>Modifier les attributs d'un élément HTML</h1>

<a id="delemont">Visiter Delémont</a>
<a id="porrentruy">Visiter Porrentruy</a>

<script>
const delemont = document.getElementById("delemont");
delemont.href = "http://www.delemont.ch";
delemont.target = "_blank";

// Avec la méthode setAttribute
const porrentruy = document.getElementById("porrentruy");
porrentruy.setAttribute("href", "http://www.porrentruy.ch");
porrentruy.setAttribute("target", "_blank");
</script>
```

{% embed url="https://codepen.io/fallinov/pen/rNBLQZB?editors=0010" %}



