# Supprimer, remplacer et cloner

## Supprimer un élément

test

### Supprimer un fils

```markup
<div>
    <h1>Un Titre</h1>
    <p>Petit paragraphe<p>
</div>

<script>
// Récupération de la 1re div du document
const DIV = document.querySelector("div");
// Récupération du 1er <p> de la DIV
const P1 = DIV.querySelector("p");
// Suppression du 1er paragraphe
DIV.removeChild(P1);
</script>
```

{% embed url="https://codepen.io/fallinov/pen/NOJedR" caption="" %}

## Remplacer un élément

```markup
<div>
   <h1>Un Titre</h1>
   <p>Petit paragraphe<p>
</div>

<script>
// Récupération de la 1re div du document
const DIV = document.querySelector("div");
// Récupération du 1er <p> de la DIV
const ANCIEN_PARA = DIV.querySelector("p");
// Création d'un nouveau <p>
const NOUVEAU_PARA = document.createElement("p");
// Modification du texte du nouveau <p>
NOUVEAU_PARA.innerText = 'Nouveau paragraphe';
// Remplace l'ancien <p> par le nouveau
DIV.replaceChild(NOUVEAU_PARA, ANCIEN_PARA);
</script>
```

{% embed url="https://codepen.io/fallinov/pen/xyBmYm" caption="" %}

## Cloner un élément

```markup
<ul id="liste1">
   <li>Fromage</li>
   <li>Thé</li>
</ul>

<ul id="liste2">
   <li>Eau</li>
   <li>Sucre</li>
</ul>

<script>
// Récupération du dernier fils de #liste1 <li>Thé</li>
const DERNIER_FILS_LISTE1 = document.querySelector("#liste1 :last-child");
// Clone, copie, le dernier fils et son contenu, sa descendance
const CLONE = DERNIER_FILS_LISTE1.cloneNode(true);
// Ajoute le clone à la fin de #liste1
document.getElementById("liste2").appendChild(CLONE);
</script>
```

{% embed url="https://codepen.io/fallinov/pen/LgaMja?editors=1111" caption="" %}

