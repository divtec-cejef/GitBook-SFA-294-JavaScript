# Valider les saisies utilisateurs

Ci-après un exemple classique de validation de formulaire avec création d'un message d'erreur.

{% code-tabs %}
{% code-tabs-item title="HTML" %}
```markup
<ul class="message"></ul>
<form action="https://kode.ch/getpost/" method="post">
   <ul>
      <li>
         <label for="nom">Votre nom</label>
         <input type="text" id="nom" name="nom">
      </li>
      <li>
         <label for="age">Votre age</label>
         <input type="text" id="age" name="age">
      </li>
      <li>
         <button type="submit">Envoyer</button>
      </li>
   </ul>
</form>
```
{% endcode-tabs-item %}

{% code-tabs-item title="" %}
```javascript
/**
 * Valide le formulaire et retourne un tableau d'erreurs
 * @return {Array} Tableau de messages d'erreur
 */
function validationFormulaire(nom, age) {
   // Initialisation du tableau des erreurs
   let erreurs = [];

   //Supprime les espaces en début et fin de chaine
   nom = nom.trim();
   
   //Converti l'age en entier
   age = parseInt(age);

   // Si le nom vide
   if (nom === "") {
      erreurs.push("Entrez un nom !");
   }

   // Si l'age n'est pas un nombre entier compris entre 0 et 120
   if (Number.isNaN(age) || age < 1 || age > 119) {
      erreurs.push("Entrez un age valide !");
   }

   return erreurs;
}


// Récupération du formulaire et de la liste des messages d'erreurs
const FORMULAIRE = document.querySelector("form");
const UL_MESSAGE = document.querySelector("ul.message");

// Evénement submit => Lors de l'envoi du formulaire
FORMULAIRE.addEventListener("submit", function(event) {
   // Désactive l'envoi du formulaire
   event.preventDefault();
   
   // Récupère les champs nom et age
   const TXT_NOM = document.getElementById("nom");
   const TXT_AGE = document.getElementById("age");
   
   // Supprime les message existants
   UL_MESSAGE.innerHTML = "";
   
   // Validation du formulaire
   let erreurs = validationFormulaire(TXT_NOM.value, TXT_AGE.value);
   
   // Si il y a des erreurs
   if(erreurs.length > 0) { 
      // Parcours les messages d'erreur
      for(message of erreurs) {
         // Ajoute un li au contenu de la liste
         UL_MESSAGE.innerHTML += "<li>" + message + "</li>";
      }
      // Sort de la fonction
      return;
   }

   // Envoie le formulaire
   FORMULAIRE.submit();
});
```
{% endcode-tabs-item %}

{% code-tabs-item title=undefined %}
```css
body {
   font-family: "Trebuchet MS", Helvetica, sans-serif;
}

ul.message {
   color: #ecf0f1;
   background-color: #e74c3c;
}

ul.message li {
   padding: .5em 0;
}

form ul {
   list-style-type: none;
   padding: 0;
}

form ul li {
   padding: 0 0 1em 0;
}

form ul li label {
   display: block;
   font-weight: bold;
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% embed url="https://codepen.io/fallinov/pen/mQBoBp?editors=0010" %}

