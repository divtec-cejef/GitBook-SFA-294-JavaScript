# Paramètres par défaut

```javascript
let produit = function(nom = 'Sabre laser', prix = 220) {
    console.log(nom + " & " + prix);
};

produit(undefined, 200); // Sabre laser & 200
```



