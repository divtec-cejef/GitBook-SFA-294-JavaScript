# Objets

## **Pourquoi utiliser des Objets en programmation ?**

Les objets sont essentiels en programmation pour organiser et structurer des données de manière claire et cohérente. Ils permettent de représenter des entités complexes en regroupant plusieurs propriétés sous une même entité. Voici quelques raisons pour lesquelles les objets sont utilisés :

1. **Regrouper des informations** : les objets permettent de stocker des données liées entre elles dans une seule structure, rendant le code plus lisible et plus facile à maintenir.
2. **Modéliser des entités réelles** : les objets sont parfaits pour représenter des entités du monde réel, comme un utilisateur, un produit ou une voiture, en associant des caractéristiques spécifiques à chacune.
3. **Réutilisabilité** : Une fois qu'un objet est défini, il peut être utilisé, manipulé et étendu de manière flexible à travers tout le programme.

En JavaScript, les objets sont des structures de données essentielles qui permettent de regrouper des informations sous la forme de paires clés-valeur.

Ils sont particulièrement utiles pour modéliser des entités complexes, comme un utilisateur, un produit ou une configuration.

## Résumé de la création et manipulation d'objets

```javascript
// 1. Création d'un objet simple en utilisant la notation littérale
const voiture = {
    marque: "Toyota",           // Propriété 'marque' de l'objet
    modele: "Corolla",          // Propriété 'modele' de l'objet
    annee: 2020,                // Propriété 'annee' de l'objet
    estElectrique: false,       // Propriété 'estElectrique' de l'objet

    // 2. Ajout d'une méthode à l'objet
    afficherDetails: function() {
        console.log(`${this.marque} ${this.modele}, ${this.annee} - Électrique: ${this.estElectrique}`);
        // 'this' fait référence à l'objet 'voiture'
    }
};

// 3. Accès aux propriétés de l'objet
console.log(voiture.marque);        // Affiche "Toyota"
console.log(voiture["modele"]);     // Affiche "Corolla"

// 4. Modification des propriétés de l'objet
voiture.annee = 2021;               // Change l'année de 2020 à 2021

// 5. Ajout d'une nouvelle propriété à l'objet
voiture.couleur = "Rouge";          // Ajoute une nouvelle propriété 'couleur'

// 6. Utilisation de la méthode de l'objet
voiture.afficherDetails();          // Affiche "Toyota Corolla, 2021 - Électrique: false"

// 7. Suppression d'une propriété de l'objet
delete voiture.estElectrique;       // Supprime la propriété 'estElectrique'

```

***

## **Création d'un Objet**

Il existe plusieurs façons de créer un objet en JavaScript, mais la méthode la plus courante est d'utiliser la notation littérale.

### Exemple

```javascript
const utilisateur = {
    nom: "Jean",
    age: 30,
    email: "jean@example.com",
    estActif: true
};
```

* **Clés** : `nom`, `age`, `email`, `estActif` (chaque clé représente une propriété de l'objet).
* **Valeurs** : `"Jean"`, `30`, `"jean@example.com"`, `true` (chaque valeur est associée à une clé).

### Utilisation d'un constructeur

En JavaScript, un constructeur est une fonction spéciale utilisée pour créer et initialiser des objets lorsqu'ils sont instanciés avec le mot-clé `new`. Un constructeur permet de définir un modèle pour un type d'objet et d'initialiser ses propriétés et méthodes.

```javascript
function Voiture(marque, modele, annee, estElectrique) {
    this.marque = marque;
    this.modele = modele;
    this.annee = annee;
    this.estElectrique = estElectrique;

    this.afficherDetails = function() {
        console.log(`${this.marque} ${this.modele}, ${this.annee} - Électrique: ${this.estElectrique}`);
    };
}

const maVoiture = new Voiture("Tesla", "Model S", 2022, true);
maVoiture.afficherDetails(); // "Tesla Model S, 2022 - Électrique: true"
```

**`this.marque = marque;`** : `this` fait référence à l'objet nouvellement créé. Chaque propriété est initialisée avec les arguments passés lors de l'instanciation.

**`this.afficherDetails = function() { ... }`** : Ajoute une méthode `afficherDetails` à chaque instance créée par le constructeur.

**`new Voiture(...)`** crée un nouvel objet `maVoiture` avec les propriétés définies dans le constructeur.

***

## **Accès aux Propriétés d'un Objet**

Il existe deux façons d'accéder aux propriétés d'un objet :&#x20;

* la notation par point `utilisateur.nom`
* la notation par crochets. `utilisateur["nom"]`

**Exemple : Accès aux Propriétés**

```javascript
// Notation par point
console.log(utilisateur.nom); // "Jean"

// Notation par crochets
console.log(utilisateur["email"]); // "jean@example.com"
```

* **Notation par point** : Simple et couramment utilisée pour accéder à une propriété dont le nom est connu.
* **Notation par crochets** : Utile lorsque le nom de la propriété est dynamique ou contient des caractères spéciaux.

### Utilisation de la Notation par Crochets

La notation par crochets en JavaScript est particulièrement utile dans deux situations : lorsque le nom de la propriété est dynamique (c'est-à-dire qu'il est déterminé à l'exécution) ou lorsqu'il contient des caractères spéciaux qui ne sont pas valides pour la notation par point.

#### **Nom de propriété dynamique**

Supposons que vous ayez un objet `utilisateur` et que vous souhaitez accéder à une propriété dont le nom est stocké dans une variable.

```javascript
const utilisateur = {
    nom: "Jean",
    age: 30,
    email: "jean@example.com"
};

const propriete = "email";

console.log(utilisateur[propriete]); // "jean@example.com"
```

* Ici, la variable `propriete` contient la chaîne `"email"`.
* Grâce à `utilisateur[propriete]`, vous accédez dynamiquement à la propriété `email` de l'objet `utilisateur`.

#### **Propriété avec des caractères spéciaux**

Certaines propriétés peuvent contenir des caractères spéciaux ou des espaces, ce qui rend la notation par point inapplicable.

```javascript
const utilisateur = {
    "nom complet": "Jean Dupont",
    "âge": 30,
    "adresse-email": "jean.dupont@example.com"
};

console.log(utilisateur["nom complet"]); // "Jean Dupont"
console.log(utilisateur["adresse-email"]); // "jean.dupont@example.com"
```

* Les propriétés `"nom complet"` et `"adresse-email"` contiennent des espaces et des tirets, ce qui empêche l'utilisation de la notation par point.
* La notation par crochets permet d'accéder à ces propriétés facilement.

***

## **Modification des propriétés d'un Objet**

Les propriétés d'un objet peuvent être modifiées après sa création.

**Exemple : Modification d'une Propriété**

```javascript
utilisateur.age = 31; // Met à jour l'âge
utilisateur["email"] = "jean.dupont@example.com"; // Met à jour l'email
```

***

## **Ajout de Nouvelles Propriétés**

Vous pouvez ajouter de nouvelles propriétés à un objet à tout moment.

```javascript
utilisateur.adresse = "123 Rue de Paris"; // Ajoute une nouvelle propriété 'adresse'
utilisateur["telephone"] = "0102030405"; // Ajoute une nouvelle propriété 'telephone'
```

Une propriété ajoutée après la création de l'objet est accessible de la même manière que les propriétés définies initialement.

***

## **Suppression de Propriétés**

La suppression d'une propriété d'un objet se fait avec l'opérateur `delete`.

```javascript
delete utilisateur.estActif; // Supprime la propriété 'estActif'
```

Après suppression, la propriété n'est plus accessible et est considérée comme `undefined`.

***

## **Parcourir les Propriétés d'un Objet**

Il est possible de parcourir toutes les propriétés d'un objet avec une boucle `for...in`.

<pre class="language-javascript"><code class="lang-javascript">for (let cle in utilisateur) {
    console.log(cle + ": " + utilisateur[cle]);
}

<strong>// nom: Jean
</strong>// age: 31
// email: jean.dupont@example.com
// adresse: 123 Rue de Paris
// telephone: 0102030405le for...in permet d'itérer sur toutes les propriétés énumérables d'un objet.
</code></pre>
