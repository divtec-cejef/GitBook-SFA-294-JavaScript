# Récupérer la valeur des champs

## Champs de saisie

### Propriété `value`

Pour récupérer la valeur entrée par le visiteur dans un champs de saisie texte \(`input`, `textarea`\), on utilise la propriété `.value`.

```javascript
monElement.value;
```

## Liste déroulantes

### Propriété `value`

Pour récupérer la valeur de l'option sélectionnée d'une liste,  on utilise  la propriété `.value`.

```javascript
monElementSelect.value;
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

Code du pays : <span class="code"></span>

<script>
// Récupère la liste déroulante #pays et le span .code
const LIS_PAYS = document.getElementById("pays");
const DIV_CODE = document.querySelector("span.code");

// Sur changement de la valeur de la liste déroulante
LIS_PAYS.addEventListener("change", function() {
   // Récupère la valeur de l'option sélectionnée
   let codePays = LIS_PAYS.value;
   // Modifie le contenu texte du span .code   
   DIV_CODE.innerText = codePays;
});
</script>
```

## Cases à cocher

### Propriété checked

 La propritété `checked` vous permet de savoir si une case est cochée `true` ou non `false`

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
const FORMULAIRE = document.querySelector('form');
// Case à cocher "copie"
const CHK_COPIE = document.getElementById('copie');

// Evénement submit => Lors de l'envoi du formulaire
FORMULAIRE.addEventListener('submit', function(event){ 
   // Si utilisateur n'a pas saisi de nom
   if(CHK_COPIE.checked === true) {
      alert("Vous recevrez un copie !");
   }
});
</script>
```

{% embed url="https://codepen.io/fallinov/pen/mQwoYY?editors=1001" %}

## Groupe de cases à cocher



## Groupe de boutons radios

Pour récupérer la valeur de l'élément sélectionné dans un groupe de bouton radio, il faut savoir quel bouton du groupe est coché.

### Propriété checked

