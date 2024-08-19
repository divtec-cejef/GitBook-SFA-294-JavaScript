# Récupérer et modifier la valeur des champs

## Champs de saisie

### Propriété `value`

Pour récupérer ou modifier la valeur entrée par le visiteur dans un champs de saisie texte (`input`,  `password`,`textarea`, `hidden` , `email`) on utilise la propriété `.value`.

```javascript
let texte = monElement.value;
monElement.value = "toto";
```

## Liste déroulantes

### Propriété `value`

Pour récupérer la valeur de l'option sélectionnée d'une liste,  on utilise  la propriété `.value`.

```javascript
monElementSelect.value;
```

### Selecteur CSS :checked

Le sélecteur  `:checked` vous permet de récupérer l'**option actuellement sélectionnée** avec `querySelector` **.**&#x20;

Exemple récupérer le contenu texte de l'option `selected` :&#x20;

```markup
<select name="pays" id="pays">
   <option value="">-- Sélectionnez un pays --</option>
   <option value="FR">France</option>
   <option selected value="IT">Italie</option>
   <option value="CH">Suisse</option>
</select>

<script>
const liste = document.getElementById("pays");
const optionSelectionnee = liste.querySelector("option:checked");

console.log(optionSelectionnee.innerText); // Italie
</script>
```

### Evénement `change`

L'événement `change` est souvent associé aux listes. Il se déclenche lorsque le visiteur sélectionne une autre option dans la liste.

```javascript
monElementListe.addEventListener("change", function() {...});
```

### Exemple

```markup
<select name="pays" id="pays">
   <option selected value="">-- Sélectionnez un pays --</option>
   <option value="FR">France</option>
   <option value="IT">Italie</option>
   <option value="CH">Suisse</option>
</select>

<div>
   Code du pays : <span class="code"></span>
</div>

<script>
// Récupère la liste déroulante #pays et le span .code
const listePays = document.getElementById("pays");
const codeSelectionne = document.querySelector("span.code");

// Sur changement de la valeur de la liste déroulante
listePays.addEventListener("change", function() {
   // Récupère la valeur de l'option sélectionnée
   let codePays = listePays.value;
   // Modifie le contenu texte du span .code
   codeSelectionne.innerText = codePays;
});
</script>
```

{% embed url="https://codepen.io/fallinov/pen/jQaPVL?editors=1000" %}

## Cases à cocher

### Propriété checked

&#x20;La propriété `checked` vous permet de savoir si une case est cochée `true` ou non `false`

```javascript
monElement.checked; // Retourne true ou false
```

### Exemple

```markup
<form action="https://kode.ch/getpost/" method="post">
   <input type="checkbox" id="copie" name="copie">
   <label for="copie">Recevoir une copie</label>
   <button>Envoyer</button>
</form>

<script>
// 1er formulaire du document
const formulaire = document.querySelector("form");
// Case à cocher "copie"
const chkCopie = document.getElementById("copie");

// Evénement submit => Lors de l'envoi du formulaire
formulaire.addEventListener("submit", function(event) {
   // Si utilisateur n'a pas saisi de nom
   if (chkCopie.checked === true) {
      alert("Message envoyé AVEC copie !");
   } else {
      alert("Message envoyé SANS copie !");
   }
});
</script>
```

{% embed url="https://codepen.io/fallinov/pen/zMPGvL?editors=0010" %}

## Groupe de cases à cocher

Pour récupérer les cases cochées d'un groupe, la meilleure méthode est d'utiliser `querySelector` et la puissance des sélecteurs CSS, pour récupérer toutes les cases cochées  `:checked` du groupe `[name="nomGroupe"]` .

```javascript
let casesCochées = document.querySelectorAll(
      'input[name="groupeCases[]"]:checked'
   );
```

{% hint style="warning" %}
La variable qui contient le résultat du `querySelectorAll()`n'est pas "dynamique", les nouvelles cases cochées ne s'y ajouteront pas automatiquement.

Il ne faut donc rappeler `querySelectorAll()` pour mettre à jour le contenu de la variable.
{% endhint %}

### Exemple

```markup
<form action="https://kode.ch/getpost/" method="post">
   <input type="checkbox" name="couleurs[]" id="rouge" value="rouge">
   <label for="rouge">Rouge</label>

   <input type="checkbox" name="couleurs[]" id="vert" value="vert">
   <label for="vert">Vert</label>

   <input type="checkbox" name="couleurs[]" id="bleu" value="bleu">
   <label for="bleu">Bleu</label>

   <button>Envoyer</button>
</form>

<script>
// 1er formulaire du document
const formulaire = document.querySelector("form");

// Evénement submit => Lors de l'envoi du formulaire
formulaire.addEventListener("submit", function(event) {
   event.preventDefault();

   // Cases cochée dans le groupe couleurs[]
   const couleursCochées = document.querySelectorAll(
      'input[name="couleurs[]"]:checked'
   );

   //Récupère la valeur des éléments cochés
   for (let couleur of couleursCochées) {
      alert(couleur.value);
   }
});
</script>
```

{% embed url="https://codepen.io/fallinov/pen/eQeNYV?editors=0011" %}

## Groupe de boutons radios

Pour récupérer la valeur du radio sélectionné dans un groupe, la meilleure méthode est d'utiliser `querySelector` et la puissance des sélecteurs CSS, pour récupérer le premier radio coché  `:checked` du groupe `[name="nomGroupe"]` .

```javascript
// Récupère la valeur du radio coché dans le groupe "couleur"
document.querySelector('[name="couleur"]:checked').value;
```

### Exemple

```markup
<form action="https://kode.ch/getpost/" method="post">
   <input type="radio" name="genre" id="h" value="Homme">
   <label for="h">Homme</label>

   <input type="radio" name="genre" id="f" value="Femme">
   <label for="f">Femme</label>

   <button>Envoyer</button>
</form>

<script>
// 1er formulaire du document
const formulaire = document.querySelector("form");

// Evénement submit => Lors de l'envoi du formulaire
formulaire.addEventListener("submit", function(event) {
   // Désactive l'envoi du formulaire
   event.preventDefault();

   // Radio coché dans le groupe genre
   const genre = document.querySelector('[name="genre"]:checked');

   // Test si un genre est coché
   if (genre === null) {
      alert("Sélectionner un genre !");
      return;
   }

   alert(genre.value);
});
</script>
```

{% embed url="https://codepen.io/fallinov/pen/aQzRPy?editors=0010" %}
