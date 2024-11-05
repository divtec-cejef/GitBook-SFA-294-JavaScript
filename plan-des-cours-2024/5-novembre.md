# 📅 5 novembre

## 🚀 Objectifs du jour

1. **Corriger les cinq premières étapes** de l'exercice [Pokédex Vuetify](../exercices/exercice-pokedex-vuetify.md).
2. **Finaliser l'exercice** en ajoutant les fonctionnalités restantes.
3. **Introduction aux APIs** : se connecter à une API pour obtenir des informations sur les Pokémon.
4. **Adaptation des composants** de l'exercice [Pokédex Vuetify](../exercices/exercice-pokedex-vuetify.md) pour traiter les données de l'API.

***

## 🔄 Correction de l'exercice "Pokédex Vuetify"

1. **Revue des cinq premières étapes** :
   * Vérification des composants créés (pages et liens de navigation).
   * Validation de la navigation entre les pages et des éléments de style.
   * Test des interactions, comme la gestion des favoris et l'affichage de la carte.
2. **Correction collective** :
   * Identification d'éventuelles erreurs rencontrées lors des étapes précédentes.
   * Revue de code et bonnes pratiques pour optimiser l'application.

***

## 🛠 Finalisation de l'exercice "Pokédex Vuetify"

*   **Achèvement des fonctionnalités** :

    * Assurez-vous que toutes les pages et les éléments (recherche, favoris, carte, etc.) sont opérationnels.



***

## 🌐 Introduction aux APIs

1. **Mise en place d'une API locale avec Docker et Directus :**&#x20;
   * Cloner et suivre les consignes de ce dépôt :[https://github.com/fallinov/2024-SFA-Pokemon-Directus](https://github.com/fallinov/2024-SFA-Pokemon-Directus)&#x20;
2. **Présentation des APIs** :
   * Expliquer l'importance des APIs pour obtenir des données dynamiques.
   * Présentation de l'API et des structure des réponses.
3. **Connexion de l'exercice à l'API** :
   * Utilisation de `axios`  pour faire des appels API.
   * Modification du magasin Pinia pour récupérer les types et les Pokémons via l'API

***

## 🔄 Adaptation des composants au format des données de l'API

* Adapter les propriétés et le rendu pour afficher la liste des Pokémons
  * Renommer les données avec leur nouvelle dénomination `pokemon.name =>  pokemon.nom`
  * Remplacer les couleurs de types par des images
  * Ajuster le composant de recherche pour fonctionner avec les données API.
* Adapter la fiche de détail d'un Pokémon
  * Même chose que pour la liste
  * Ajout des statistiques (HP, ATTACK, DEFENSE, SPEED, SPECIAL ATTACK, SPECIAL DEFENSE)

***

## ✅ Devoirs

* Finaliser l'adaptation des composants à l'API.

## 📒 Supports de cours supplémentaires

1. [Vuetify Documentation (EN)](https://vuetifyjs.com/en/getting-started/installation/)
2. [Vue Mastey - Intro to Vue 3 (EN)](https://www.vuemastery.com/courses/intro-to-vue-3/intro-to-vue3)
3. [Vue.js Documentation (FR)](https://fr.vuejs.org/guide/introduction)
4. [OpenClassrooms : Introduction à Vue.js (FR)](https://openclassrooms.com/fr/courses/6390311-creez-une-application-web-avec-vue-js)
