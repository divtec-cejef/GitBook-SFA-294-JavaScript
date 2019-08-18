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
 * Valide le nom et l'âge d'une personne et retourne un tableau d'erreurs
 * @return {Array} Tableau de messages d'erreur
 */
function validerPersonne(nom, age) {
   // Initialisation du tableau des erreurs
   const erreurs = [];

   //Supprime les espaces en début et fin de chaine
   nom = nom.trim();

   //Converti l'age en entier
   age = parseInt(age);

   // Si le nom vide
   if (nom === "") {
      erreurs.push("Entrez un nom !");
   }

   // Si l'âge n'est pas un nombre entier compris entre 0 et 120
   if (Number.isNaN(age) || age < 1 || age > 119) {
      erreurs.push("Entrez un age valide !");
   }

   return erreurs;
}

/**
 * Ajoute le contenu d'un tableau à la fin d'une liste HTML
 * @param {HTMLElement} eleListe - Liste HTML (ol ou ul) à remplir
 * @param {Array} erreurs - tableau de String
 */
function ajouterFinListe(eleListe, erreurs) {
   // Parcours les messages d'erreur
   for (message of erreurs) {
      // Ajoute un li au contenu de la liste
      eleListe.innerHTML += "<li>" + message.toString() + "</li>";
   }
}

// Récupération du formulaire et de la liste message
const eleFormulaire = document.querySelector("form");
const eleMessage = document.querySelector("ul.message");

// Evénement submit => Lors de l'envoi du formulaire
eleFormulaire.addEventListener("submit", function(event) {
   // Désactive l'envoi du formulaire
   event.preventDefault();

   // Récupère les champs nom et age
   const txtNom = document.getElementById("nom");
   const txtAge = document.getElementById("age");

   // Supprime les anciens messages d'erreur
   eleMessage.innerHTML = "";

   // Validation des données
   let erreurs = validerPersonne(txtNom.value, txtAge.value);

   // Si il y a des erreurs
   if (erreurs.length > 0) {
      // Ajoute les erreurs à la fin de ul.message
      ajouterFinListe(eleMessage, erreurs);
   } else {
      // Envoi du formulaire
      eleFormulaire.submit();
   }
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

