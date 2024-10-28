---
description: Crée un Pokédex avec les composants Vuetify
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

# 📒 Exercice Pokédex Vuetify

## Introduction

Cet exercice consiste à créer une application Pokédex avec **Vue.js** et **Vuetify**. Vous allez apprendre à construire une interface utilisateur interactive avec des composants **Vuetify**, à gérer l'état de l'application avec **Pinia**, et à intégrer des fonctionnalités telles que la recherche et la gestion des favoris pour les Pokémon.

L'application finale inclura les fonctionnalités suivantes :

* **Liste des Pokémon avec recherche** : une page permettant de visualiser une liste détaillée des Pokémon disponibles avec un champ de recherche permettant de trouver des Pokémon par leur nom.
* **Gestion des favoris** : Possibilité d'ajouter des Pokémon à une liste de favoris, avec stockage local pour les conserver entre les sessions.
* **Affichage détaillé** : une page dédiée à chaque Pokémon avec ses informations détaillées.
* **FAQ** : Une page avec quelques FAQ sur les Pokémons.
* **Monde Pokémon :** une page simple présentant une carte du monde Pokémon, avec quelques textes.

Voici un exemple de solution : [https://kode.ch/pokedex/](https://kode.ch/pokedex/)

## Mise en place

1. **Cloner le dépôt de l'exercice** et l'ouvrir dans WebStorm.
2.  **Installer les dépendances** : ouvrez un terminal à la racine du projet et exécutez la commande suivante pour installer toutes les dépendances nécessaires :

    ```sh
    npm install
    ```
3.  **Lancer le serveur de développement** : une fois les dépendances installées, lancez le serveur de développement avec la commande :

    ```sh
    npm run serve
    ```
4. **Accéder à l'application dans le navigateur** : après avoir démarré le serveur, vous verrez une URL (généralement `http://localhost:3000`) dans le terminal. Ouvrez cette URL dans votre navigateur pour afficher l'application de départ.

Vous devriez apercevoir le résultat suivant :



## Présentation du projet de départ

### Structure du projet

Voici une vue d'ensemble des différents dossiers et fichiers du projet :

* **public/** : Contient le fichier `index.html`, qui est le point d'entrée statique de l'application.
  * **images/** : Contient les images des différents Pokémon
* **src/** : Le dossier principal qui contient tout le code source de l'application
  * **assets/** : Contient les ressources statiques comme les images, les icônes, le logo du site, etc.
  * **components/** : Contient les composants Vue réutilisables de l'application. C'est ici que vous pourrez créer vos composants.
  * **store/** : Contient la configuration initiale du magasin Pinia pour la gestion de l'état global de l'application.
    * **pokemons.js** : Fichier qui gère l'état des données des Pokémon, incluant leur liste, leurs détails, et les actions associées.
  * **views/** : Contient les différentes vues (ou pages) de l'application. Voici les fichiers présents dans le code de départ :
    * **index.vue** : Page principale du projet.
    * **\[...path].vue** : S'affiche&#x20;
  * **App.vue** : Composant racine de l'application
  * **main.js** : Point d'entrée JavaScript de l'application. Il initialise Vue, intègre Vuetify, Pinia, et le routeur.

### Layout de base

Le composant principal **App.vue** est composé de trois sections principales :

* **\<menu-principal>** : Charge le composant components/AppHeader.vue qui contient l'entête du site
* **\<v-main>** : Contient le composant `<router-view>`, qui affiche dynamiquement les pages en fonction de la route sélectionnée.
* **\<v-footer>** : un pied de page contenant simplement le copyright

### Magasin Pinia

## Travail à réaliser

### **Étape 1 - Créer les pages**

Créer les quatre pages avec comme contenu un unique titre principal `<h1>`.&#x20;

Voici le nom des fichiers et les titres à utiliser pour ces pages à créer dans le dossier `src/pages/` de l'application.

* `index.vue` - `Pokédex : page d'accueil`
* `Favoris.vue` - `Mes Pokémons Favoris`
* `FAQ.vue` - `Foire Aux Questions (FAQ)`
* `KantoMap.vue` - `Monde Pokémon`

#### Tester les pages

Les **routes** (url) sont **automatiquement créées** en fonction du nom des fichiers contenus dans le dossier `src/pages/` de l'application.

Assurez-vous que vos pages sont bien accessibles :&#x20;

* `index.vue` - [http://localhost:3000/](http://localhost:3000/)
* `Favoris.vue` - [http://localhost:3000/favoris](http://localhost:3000/favoris)
* `FAQ.vue` - [http://localhost:3000/faq](http://localhost:3000/faq)
* `KantoMap.vue` - [http://localhost:3000/kantomap](http://localhost:3000/kantomap)



### **Étape 2 - Créer** les liens du menu de navigation

Le menu de navigation est implémenté dans le composant `AppHeader.vue`, qui est inclus dans le composant principal `App.vue`.&#x20;

```markup
<template>
  <v-app-bar flat>
    <v-container class="d-flex align-start align-center">
      <v-avatar
        class="mr-4 pa-0 cursor-pointer"
        image="@/assets/pokeball.svg"
        size="64"
        @click="$router.push('/')"
      />
      <v-toolbar-title>Pokedex</v-toolbar-title>
      <v-btn
        v-for="link in menuItems"
        :key="link.title"
        :icon="link.icon"
        :to="link.path"
      />
    </v-container>
  </v-app-bar>
</template>

<script setup>
  import { ref } from 'vue'

  const menuItems = ref([
    { title: 'Accueil', path: '/', icon: 'mdi-pokeball' },
  ])
</script>
```

Ce menu utilise le composant `v-app-bar` de Vuetify pour créer une barre de navigation en haut de la page. Voici les éléments principaux du code :

* `v-avatar` : Affiche un avatar représentant une Pokéball qui, lorsqu'on clique dessus, redirige vers la page d'accueil.
* `v-toolbar-title` : Affiche le titre "Pokédex".
* `v-btn` : La directive `v-for` crée un bouton de navigation pour chaque élément du tableau `menuItems`.&#x20;

Dans le code de départ, il n'y a qu'un seul élément nommé "Accueil" avec une icône de Pokéball.

Pour ajouter un lien au menu, il suffit d'ajouter un élément au tableau `menuItems`.

#### Trouver et utiliser des icônes

Ce projet utilise les _Material Design Icons._ Pour utiliser l'une de ces icônes, il suffit d'utiliser le préfixe `mdi-` suivi du nom de l'icône. Par exemple, l'icône nommée `account` devient `mdi-account.`

Vous trouverez la liste des icônes sur ce site :&#x20;

{% embed url="https://pictogrammers.com/library/mdi/" %}

### **Étape 3 - Créer le contenu de la page "Mon Pokémon"**

Inclure un titre, une image cliquable qui s'ouvre dans une pop-up, et un texte comprenant un sous-titre et un paragraphe descriptif.

### **Étape 4 - Créer le contenu de la page "Vos questions"**

Utiliser un composant Vuetify approprié pour réaliser une page de FAQ. Les questions doivent être listées et afficher leur réponse au clic.

### **Étape 5 - Créer le contenu de la page "Pokédex"**

Lister les Pokémon avec les informations suivantes : une image, le nom, le type, le niveau, et une icône pour les ajouter en favori. Ajouter également un champ de recherche pour trouver un Pokémon en tapant son nom. Pour les avancés, appliquer une couleur de fond correspondant au type de chaque Pokémon.

### **Étape 6 - Créer le contenu de la page "Favoris"**

Afficher tous les Pokémon ajoutés en favori, en utilisant le stockage local (localStorage) pour conserver ces favoris en complément du store Vuex.



## :dodo: La solution du prof
