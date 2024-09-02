---
description: >-
  Crée un mini Pokédex, pour connaitre le nom, le type et le niveau de tes
  Pokémons !
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# 📒 Exercice Mini Pokédex

<div data-full-width="true">

<figure><img src="../.gitbook/assets/exe-mini-pokedex.png" alt=""><figcaption></figcaption></figure>

</div>

## **Objectifs**

* **Manipuler le DOM :** Apprendre à utiliser JavaScript pour ajouter et modifier des éléments HTML sur une page.
* **Utiliser des Boucles :** Savoir parcourir un tableau pour afficher les éléments qu'il contient.
* **Gérer les Événements :** Comprendre comment réagir aux actions de l'utilisateur, comme la recherche ou le filtrage.
* **Travailler avec des Tableaux :** Utiliser des méthodes comme `filter()` et `sort()` pour filtrer et trier les données.
* **Appliquer des Styles Dynamiques :** Apprendre à changer l'apparence des éléments en fonction de leur contenu.
* **Construire une Interface Interactive :** Créer une interface qui s'adapte aux entrées de l'utilisateur, comme le tri et la recherche.
* **Valider les Données :** Vérifier que les données sont correctes avant de les afficher.
* **Utiliser la Documentation :** Encourager l'utilisation de la documentation pour résoudre des problèmes et apprendre de nouvelles fonctionnalités.

***

## Instructions

Pour réaliser cet exercice, copier les fichiers de ce dépôt



### Étape 1 : Afficher une liste simple de Pokémon

**Objectif :** Afficher une liste simple contenant les noms de tous les Pokémon.

#### **Instructions**

1. Dans le fichier `script.js`, ajoute créer une [fonction](../javascript/introduction/fonctions.md#creer-et-appeler-un-fonction) `displayPokemons` qui remplace le contenu du conteneur `.pokemon-container` par une liste des noms de Pokémon.
2. Utilise une [boucle](../javascript/introduction/boucles.md) pour parcourir le [tableau](../javascript/introduction/tableaux.md) `pokemons` et pour chaque Pokémon, crée un élément `<p>` contenant son nom.
3. Ajoute chaque nom de Pokémon avec [`innerHTML`](../javascript/dom-introduction/dom-modifier-texte.md#innerhtml).
4. Pensez à vider, réinitialiser, le contenu du conteneur `.pokemon-container` avant de créer la liste.
5. Utiliser les [_template literals_](../javascript/introduction/string.md#template-literals-litteraux-de-gabarits) pour créer des chaines de caractères dynamiques.
6. Pensez à appeler votre fonction pour la tester :smile:

#### **Exemple de résultat attendu**

La page doit simplement afficher les noms de Pokémon comme suit :

```html
<div class="pokemon-container">
    <p>Pikachu</p>
    <p>Bulbizarre</p>
    <p>Salamèche</p>
    <p>Carapuce</p>
    <p>Rondoudou</p>
    <!-- Les autres Pokémon -->
</div>
```

#### **Ressources utiles**

* [#creer-et-appeler-un-fonction](../javascript/introduction/fonctions.md#creer-et-appeler-un-fonction "mention")
* [#instruction-for...of](../javascript/introduction/tableaux.md#instruction-for...of "mention")
* [#template-literals-litteraux-de-gabarits](../javascript/introduction/string.md#template-literals-litteraux-de-gabarits "mention")
* [#innerhtml](../javascript/dom-introduction/dom-modifier-texte.md#innerhtml "mention")

***

### Étape 2 : Afficher une liste de Pokémon avec leur type

**Objectif :** Afficher les noms des Pokémon avec leurs types respectifs.

{% hint style="info" %}
Un Pokémon possède au **minimum un type** et au **maximum deux**.
{% endhint %}

#### **Instructions**

1. Modifie la fonction précédemment créée pour afficher le nom de chaque Pokémon, et son type.
2.  Pour chaque Pokémon, affiche son nom suivi de ses types dans un élément `<small>,` en n'oubliant pas les espaces s'il y a plusieurs types.

    ```html
    <p>Bulbizarre <small>Plante</small> <small>Poison</small></p>
    ```
3. Utilise la méthode `split()` pour convertir la chaine de caractères des types d'un Pokémon en tableau.

#### **Exemple de résultat attendu**

La page doit afficher la liste des Pokémon avec leurs types :

```html
<div class="pokemon-container">
    <p>Pikachu <small>Électrique</small></p>
    <p>Bulbizarre <small>Plante</small> <small>Poison</small></p>
    <p>Salamèche <small>Feu</small></p>
    <p>Carapuce <small>Eau</small></p>
    <p>Rondoudou <small>Normal</small> <small>Fée</small></p>
    <!-- Les autres Pokémon -->
</div>
```

**Ressources utiles :**

* [#extraire-des-chaines-slice-substring-et-split](../javascript/introduction/string.md#extraire-des-chaines-slice-substring-et-split "mention")

***

### Étape 3 : Créer des cartes de Pokémon

**Objectif :** Afficher chaque Pokémon sous forme de carte avec son nom, type, niveau, et image.

#### **Instructions**

1. Modifie la fonction pour remplacer chaque élément `<p>` par un élément `<div>` avec la classe `pokemon-card`.
2. Chaque carte doit inclure l'image du Pokémon, son nom, ses types et son niveau.
3. Utilise `innerHTML` pour construire chaque carte et l'ajouter au conteneur.

#### **Exemple de résultat attendu**

Chaque Pokémon est affiché dans une carte avec ses détails :

```html
<div class="pokemon-container">
    <div class="pokemon-card">
        <img src="images/pikachu.png" alt="Pikachu">
        <h2>Pikachu</h2>
        <p>Type: Électrique</p>
        <p>Niveau: 35</p>
    </div>
    <div class="pokemon-card">
        <img src="images/bulbizarre.png" alt="Bulbizarre">
        <h2>Bulbizarre</h2>
        <p>Type: Plante, Poison</p>
        <p>Niveau: 15</p>
    </div>
    <!-- Les autres Pokémon -->
</div>
```

#### **Ressources utiles**

* [Documentation MDN sur la Manipulation du DOM](https://developer.mozilla.org/fr/docs/Web/API/Document\_Object\_Model/Introduction)
* [Documentation MDN sur les Éléments HTML](https://developer.mozilla.org/fr/docs/Web/HTML/Element/div)

***

### Étape 4 : Couleurs de fond en fonction du type

**Objectif :** Appliquer une couleur de fond à chaque carte Pokémon par rapport à ses types.

#### **Instructions**

1. Modifie la fonction pour que la couleur de fond de chaque carte soit déterminée par les types du Pokémon.
2. Si un Pokémon a deux types, utilise un dégradé de couleurs pour la carte.
3. Utilise l'objet `typeColors` pour récupérer les couleurs associées à chaque type.

#### **Exemple de résultat attendu**&#x20;

Chaque carte Pokémon a un fond coloré correspondant à ses types :

```html
<div class="pokemon-container">
    <!-- Exemple de Pokemon avec un seul type -->
    <div class="pokemon-card" style="background: #FFD700;">
        <img src="images/pikachu.png" alt="Pikachu">
        <h2>Pikachu</h2>
        <p>Type: Électrique</p>
        <p>Niveau: 35</p>
    </div>
    
    <!-- Exemple de Pokemon avec deux types -->
    <div class="pokemon-card" style="background: linear-gradient(to right, #78C850 50%, #A040A0 50%);">
        <img src="images/bulbizarre.png" alt="Bulbizarre">
        <h2>Bulbizarre</h2>
        <p>Type: Plante, Poison</p>
        <p>Niveau: 15</p>
    </div>
    <!-- Les autres Pokémon -->
</div>
```

#### **Ressources utiles**

* [#extraire-des-chaines-slice-substring-et-split](../javascript/introduction/string.md#extraire-des-chaines-slice-substring-et-split "mention")
* [Documentation MDN sur les Objets en JavaScript](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/Working\_with\_Objects)
* [Documentation MDN sur les Dégradés CSS](https://developer.mozilla.org/fr/docs/Web/CSS/gradient)

***

#### Étape 5 : Ajout des Fonctionnalités de Recherche et de Tri

**Objectif :** Ajouter la fonctionnalité de recherche et de tri pour filtrer les Pokémon affichés.

**Instructions :**

1. Ajoute des gestionnaires d'événements pour capturer les changements dans le champ de recherche et les listes déroulantes de filtrage et de tri.
2. Implémente une fonction pour filtrer les Pokémon en fonction du nom recherché et du type sélectionné.
3. Trie les résultats en fonction du critère sélectionné (nom ou niveau, dans l'ordre croissant ou décroissant).

**Exemple de Résultat Attendu :**

*   **Recherche "Pikachu"** : Seule la carte de Pikachu doit s'afficher.

    ```html
    <div class="pokemon-container">
        <div class="pokemon-card" style="background: #FFD700;">
            <img src="images/pikachu.png" alt="Pikachu">
            <h2>Pikachu</h2>
            <p>Type: Électrique</p>
            <p>Niveau: 35</p>
        </div>
    </div>
    ```
*   **Filtrage par Type "Feu"** : Les Pokémon de type Feu comme Salamèche et Dracaufeu doivent s'afficher.

    ```html
    <div class="pokemon-container">
        <div class="pokemon-card" style="background: #F08030;">
            <img src="images/salameche.png" alt="Salamèche">
            <h2>Salamèche</h2>
            <p>Type: Feu</p>
            <p>Niveau: 20</p>
        </div>
        <div class="pokemon-card" style="background: linear-gradient(to right, #F08030 50%, #A890F0 50%);">
            <img src="images/dracaufeu.png" alt="Dracaufeu">
            <h2>Dracaufeu</h2>
            <p>Type: Feu, Vol</p>
            <p>Niveau: 50</p>
        </div>
    </div>
    ```

**Ressources Utiles :**

* [Documentation MDN sur `addEventListener`](https://developer.mozilla.org/fr/docs/Web/API/EventTarget/addEventListener)
* [Documentation MDN sur `Array.prototype.filter()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets\_globaux/Array/filter)
* [Documentation MDN sur `Array.prototype.sort()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets\_globaux/Array/sort)

***

#### Conclusion

Ces étapes vous guident à travers la création d'un Pokedex interactif en JavaScript. Chaque étape introduit des concepts clés du développement web, avec des exemples de résultats attendus sous forme de code HTML pour vous aider à vérifier votre travail. Utilisez la documentation officielle pour approfondir votre compréhension des concepts abordés.



***

## **Challenges supplémentaires**



## :dodo: La solution du prof

{% embed url="https://fallinov.github.io/2024-SFA-JS-EXE-PokeCount/" fullWidth="false" %}
Le site du prof
{% endembed %}

{% embed url="https://github.com/fallinov/2024-SFA-JS-EXE-PokeCount" %}
Le code du prof
{% endembed %}
