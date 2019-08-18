# Envoyer des formulaires

## Envoyer et réinitialiser un formulaire

Pour envoyer un formulaire on utilise la méthode `submit()` et `reset()` pour le réinitialiser.

```javascript
// Récupère le 1er formulaire du document
const formulaire = document.querySelector('form');

// Envoyer un formulaire
formulaire.submit();

// Réinitialiser un formulaire
formulaire.reset();
```

## Événement `submit` 

L'événement `submit` permet de déclencher une fonction lors de l'**envoi du formulaire**.

```javascript
const formulaire = document.querySelector('form');

formulaire.addEventListener('submit', function(){
   console.log("Formulaire envoyé !");
});
```

Une foix la fonction terminée le formulaire sera envoyé.

### Stopper l'envoi du formulaire

Si l'on veut désactiver, stopper l'envoi du formulaire il faut utiliser la méthode `preventDefault()` de l'événement.

```javascript
const formulaire = document.querySelector('form');

// Ne pas oublier d'ajouter un paramètre à la fonction pour récupérer l'événment.
formulaire.addEventListener('submit', function(event){
   event.preventDefault(); // Stoppe l'envoi du formulaire
   console.log("Formulaire envoyé !");
});
```

## Exemple

```markup
<form action="https://kode.ch/getpost/" method="post">
   <label for="nom">Votre nom</label>
   <input type="text" id="nom" name="nom">
   <button>Envoyer</button>
</form>

<script>
// 1er formulaire du document
const formulaire = document.querySelector("form");
// Champ texte nom
const inputNom = document.getElementById("nom");
// Evénement submit => Lors de l'envoi du formulaire
formulaire.addEventListener("submit", function(event) {
   // Désactive l'envoi du formulaire
   event.preventDefault();

   // Si utilisateur n'a pas saisi de nom
   if (inputNom.value === "") {
      alert("Entrez votre nom !");
      return; // Sors de la fonction
   }

   // Envoie le formulaire
   formulaire.submit();
});

</script>
```

{% embed url="https://codepen.io/fallinov/pen/yQPywX?editors=0010" %}

