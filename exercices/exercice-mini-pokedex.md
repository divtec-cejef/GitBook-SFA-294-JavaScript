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



### Étape 1 : Afficher une Liste Simple de Pokémon

**Objectif :** Afficher une liste simple contenant les noms de tous les Pokémon.

**Instructions :**

1. Dans le fichier `script.js`, ajoute une fonction qui remplace le contenu du conteneur `.pokemon-container` par une liste des noms de Pokémon.
2. Utilise une boucle pour parcourir le tableau `pokemons` et pour chaque Pokémon, crée un élément `<p>` contenant son nom.
3. Affiche chaque nom de Pokémon en utilisant `innerHTML`.

**Exemple de Résultat Attendu :**

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

**Ressources Utiles :**

* [#instruction-for...of](../javascript/introduction/tableaux.md#instruction-for...of "mention")
* [#innerhtml](../javascript/dom-introduction/dom-modifier-texte.md#innerhtml "mention")
* [Documentation MDN sur les Boucles `for`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/Boucles\_et\_it%C3%A9rations#for\_statement)
* [Documentation MDN sur `innerHTML`](https://developer.mozilla.org/fr/docs/Web/API/Element/innerHTML)

***

#### Étape 2 : Afficher une Liste de Pokémon avec leur Type

**Objectif :** Afficher les noms des Pokémon avec leurs types respectifs.

**Instructions :**

1. Modifie la fonction précédemment créée pour afficher non seulement le nom de chaque Pokémon, mais aussi son type.
2. Pour chaque Pokémon, affiche son nom suivi de ses types, séparés par une virgule si le Pokémon a plusieurs types.
3. Utilise la méthode `join()` pour convertir les types en une chaîne de caractères.

**Exemple de Résultat Attendu :**

La page doit afficher la liste des Pokémon avec leurs types :

```html
<div class="pokemon-container">
    <p>Pikachu - Type: Électrique</p>
    <p>Bulbizarre - Type: Plante, Poison</p>
    <p>Salamèche - Type: Feu</p>
    <p>Carapuce - Type: Eau</p>
    <p>Rondoudou - Type: Normal, Fée</p>
    <!-- Les autres Pokémon -->
</div>
```

**Ressources Utiles :**

* [Documentation MDN sur `Array.prototype.join()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets\_globaux/Array/join)
* [Documentation MDN sur la Manipulation de Chaînes](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/Manipuler\_les\_cha%C3%AEnes\_de\_caract%C3%A8res)

***

#### Étape 3 : Créer des Cartes de Pokémon

**Objectif :** Afficher chaque Pokémon sous forme de carte avec son nom, type, niveau, et image.

**Instructions :**

1. Modifie la fonction pour remplacer chaque élément `<p>` par un élément `<div>` avec la classe `pokemon-card`.
2. Chaque carte doit inclure l'image du Pokémon, son nom, ses types, et son niveau.
3. Utilise `innerHTML` pour construire chaque carte et l'ajouter au conteneur.

**Exemple de Résultat Attendu :**

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

**Ressources Utiles :**

* [Documentation MDN sur la Manipulation du DOM](https://developer.mozilla.org/fr/docs/Web/API/Document\_Object\_Model/Introduction)
* [Documentation MDN sur les Éléments HTML](https://developer.mozilla.org/fr/docs/Web/HTML/Element/div)

***

#### Étape 4 : Ajouter des Couleurs de Fond pour les Types de Pokémon

**Objectif :** Appliquer une couleur de fond à chaque carte Pokémon en fonction de ses types.

**Instructions :**

1. Modifie la fonction pour que la couleur de fond de chaque carte soit déterminée par les types du Pokémon.
2. Si un Pokémon a deux types, utilise un dégradé de couleurs pour la carte.
3. Utilise l'objet `typeColors` pour récupérer les couleurs associées à chaque type.

**Exemple de Résultat Attendu :**

Chaque carte Pokémon a un fond coloré correspondant à ses types :

```html
<div class="pokemon-container">
    <div class="pokemon-card" style="background: #FFD700;">
        <img src="images/pikachu.png" alt="Pikachu">
        <h2>Pikachu</h2>
        <p>Type: Électrique</p>
        <p>Niveau: 35</p>
    </div>
    <div class="pokemon-card" style="background: linear-gradient(to right, #78C850 50%, #A040A0 50%);">
        <img src="images/bulbizarre.png" alt="Bulbizarre">
        <h2>Bulbizarre</h2>
        <p>Type: Plante, Poison</p>
        <p>Niveau: 15</p>
    </div>
    <!-- Les autres Pokémon -->
</div>
```

**Ressources Utiles :**

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
