## Objets

### Ajouter, modifier des propriétés

```javascript
// Créer un nouvel objet
let personne = {};

// Ajouter un propriété
personne.prenom = 'Laure';
personne['nom'] = 'Dinateur'; //Autre syntaxe pour l'ajout

// Accéder à une propriété
personne.prenom; // Laure
personne.nom; // Dinateur

// Supprimer une propriété
delete personne.nom;
```

