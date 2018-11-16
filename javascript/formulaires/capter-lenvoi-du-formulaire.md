# Actions des formulaires

## Envoyer et réinitialiser un formulaire

Pour envoyer un formulaire on utilise la méthode `submit()` et `reset()` pour le réinitialiser.

```javascript
// Récupère le 1er formulaire du document
const FORMULAIRE = document.querySelector('form');

// Envoyer un formulaire
FORMULAIRE.submit();

// Réinitialiser un formulaire
FORMULAIRE.reset();
```

## Événements `submit` 

L'événement `submit` permet de déclencher une fonction lors de l'envoi du formulaire.

```javascript
const FORMULAIRE = document.querySelector('form');

FORMULAIRE.addEventListener('submit', function(){
   console.log("Formulaire envoyé !");
});
```

Une foix la fonction terminée le formulaire sera envoyé.

### Stopper l'envoi du formulaire

Si l'on veut désactiver, stopper l'envoi du formulaire il faut utiliser la méthode `preventDefault()` de l'événement.

```javascript
const FORMULAIRE = document.querySelector('form');

FORMULAIRE.addEventListener('submit', function(event){
   event.preventDefault(); // Stoppe l'envoi du formulaire
   console.log("Formulaire envoyé !");
});
```

## Exemple

{% code-tabs %}
{% code-tabs-item title="index.html" %}
```markup
<form action="https://kode.ch/getpost/" method="post">
   <label for="nom">Votre nom</label>
   <input type="text" id="nom" name="nom">
   <button>Envoyer</button>
</form>
```
{% endcode-tabs-item %}

{% code-tabs-item title="main.js" %}
```javascript
// 1er formulaire du document
const FORMULAIRE = document.querySelector('form');
// Champ texte nom
const TXT_NOM = document.getElementById('nom');

// Evénement submit => Lors de l'envoi du formulaire
FORMULAIRE.addEventListener('submit', function(event){
   // Désactive l'envoi du formulaire
   event.preventDefault();
   
   // Si utilisateur n'a pas saisi de nom
   if(TXT_NOM.value === "") {
      alert("Entrez votre nom !");
      return; // Sors de la fonction
   }
   
   // Envoie le formulaire
   FORMULAIRE.submit(); 
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% embed url="https://codepen.io/fallinov/pen/mQwoYY?editors=1011" %}



