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

# 📕 Exercice Pokédex Vuetify

<div data-full-width="true">

<figure><img src="../.gitbook/assets/Capture d’écran 2024-10-29 à 15.26.44.png" alt=""><figcaption></figcaption></figure>

</div>

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

<figure><img src="../.gitbook/assets/pokedex-vuetify-start.png" alt=""><figcaption></figcaption></figure>

## Présentation du projet de départ

### Structure du projet

Voici une vue d'ensemble des différents dossiers et fichiers du projet :

* **public/** : Contient le fichier `index.html`, qui est le point d'entrée statique de l'application.
  * **images/** : Contient les **images des Pokémons**
* **src/** : Le dossier principal qui contient tout le code source de l'application
  * **assets/** : Contient les ressources statiques comme les images, les icônes, le **logo du site**, etc.
  * **components/** : Contient les composants Vue réutilisables de l'application. C'est ici que vous pourrez créer vos composants.
  * **pages/** : Contient les différentes vues (ou pages) de l'application. Voici les fichiers présents dans le code de départ :
    * **index.vue** : Page principale du projet.
    * **\[...path].vue** : Page chargé lorsque la route est incorrecte, souvent utilisé pour afficher une page "404 - Non trouvée".
  * **stores/** : Contient la configuration initiale du magasin Pinia pour la gestion de l'état global de l'application.
    * **pokemons.js** : Fichier qui gère l'état des données des Pokémon, incluant leur liste, leurs détails, et les actions associées.
  * **App.vue** : Composant racine de l'application
  * **main.js** : Point d'entrée JavaScript de l'application appelé par index.html. Il initialise Vue, intègre Vuetify, Pinia, et Vue Router.

### Affichage (layout) de base

Le composant principal **App.vue** est composé de trois sections principales :

* **\<app-header>** : Charge le composant `components/AppHeader.vue` qui contient l'entête du site (logo et menu de navigation).
* **\<v-main>** : Contenu principal de la page qui contient le composant `<router-view>`, qui affiche dynamiquement les pages en fonction de la route active.
* **\<v-footer>** : Pied de page du site contenant un simple copyright

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

{% code title="AppHeader.vue" lineNumbers="true" %}
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
  const menuItems = [
    { title: 'Accueil', path: '/', icon: 'mdi-pokeball' },
    // Ajouter ici les autres liens du menu.
    // Vous trouverez des icônes sur https://pictogrammers.com/library/mdi/
    // N'oubliez pas d'ajouter le préfixe 'mdi-' devant le nom de l'icône.
  ]
</script>
```
{% endcode %}



Ce menu utilise le composant `v-app-bar` de Vuetify pour créer une barre de navigation en haut de la page. Voici les éléments principaux du code :

* `v-avatar` : Affiche un avatar représentant une Pokéball qui, lorsqu'on clique dessus, redirige vers la page d'accueil.
* `v-toolbar-title` : Affiche le titre "Pokédex".
* `v-btn` : La directive `v-for` crée un bouton de navigation pour chaque élément du tableau `menuItems` défini dans le `<script>` du composant.

Dans le code de départ, il n'y a qu'un seul élément nommé "Accueil" avec une icône de Pokéball.

Pour ajouter un lien au menu, il suffit d'ajouter un élément au tableau `menuItems`.

#### Trouver et utiliser des icônes

Ce projet utilise les _Material Design Icons._ Pour utiliser l'une de ces icônes, il suffit d'utiliser le préfixe `mdi-` suivi du nom de l'icône. Par exemple, l'icône nommée `account` devient `mdi-account.`

Vous trouverez la liste des icônes sur ce site :&#x20;

{% embed url="https://pictogrammers.com/library/mdi/" %}

### **Étape 3 - Créer le contenu de la page "**Le Monde Pokémon**"**

#### Image

Ajouter l'image du monde Pokémon qui se trouve dans `public/images/pokemon-map.png` en utilisant un composant `v-img.`  Utiliser la valeur suivante pour la source de l'image dans le code du template HTML  `src="/images/pokemon-map.png"`.

{% embed url="https://vuetifyjs.com/en/components/images/" %}
Documentation du composant Image de Vuetify
{% endembed %}

#### Texte

Ajouter le texte ci-après dans un composant `v-card.`

{% embed url="https://vuetifyjs.com/en/components/cards/#cards" %}
Documentation du composant Card de Vuetify
{% endembed %}

```markup
<h2>Un univers fascinant à découvrir</h2>
<p>Le monde Pokémon est un vaste et merveilleux univers peuplé de créatures extraordinaires appelées Pokémon. Cette carte représente les différentes régions que les dresseurs peuvent explorer, chacune offrant ses propres défis, Pokémon uniques et aventures palpitantes.</p>

<h2>Des régions diversifiées</h2>
<p>De Kanto à Galar, en passant par Johto, Hoenn, Sinnoh, Unova, Kalos et Alola, chaque région du monde Pokémon possède sa propre identité, sa culture et son écosystème unique. Les paysages varient des montagnes enneigées aux îles tropicales, offrant une diversité incroyable d'habitats pour les différentes espèces de Pokémon.</p>

<h2>Un monde en constante évolution</h2>
<p>Le monde Pokémon est en perpétuelle expansion, avec de nouvelles régions, de nouvelles espèces de Pokémon et de nouvelles aventures qui sont régulièrement découvertes. Cette carte n'est qu'un aperçu d'un univers riche et en constante évolution, prêt à être exploré par les dresseurs audacieux.</p>

<h2>Un appel à l'aventure</h2>
<p>Que vous soyez un dresseur débutant ou expérimenté, le monde Pokémon vous invite à partir à l'aventure. Capturez de nouveaux Pokémon, affrontez des champions d'arènes, déjouez les plans des équipes malveillantes et devenez peut-être le prochain Maître Pokémon. L'aventure commence ici, sur cette carte, mais où vous mènera-t-elle ?</p>
```

#### Popup pour l'image

Faire en sorte que l'image s'affiche dans une boite de dialogue lorsqu'on clique dessus en utilisant le composant `v-dialog`.&#x20;

{% hint style="success" %}
Explorer les codes des différentes démos de la documentation Vuetify pour trouver l'exemple qui ressemble le plus à votre objectif.
{% endhint %}

{% embed url="https://vuetifyjs.com/en/components/dialogs/#dialogs" %}
Documentation du composant Dialog de Vuetify
{% endembed %}

### **Étape 4 - Créer le contenu de la page "Vos questions"**

Utiliser un composant Vuetify approprié, hé oui c'est à vous de trouver 😜, pour réaliser une page de FAQ. Les questions doivent être listées et afficher leur réponse au clic.

{% embed url="https://vuetifyjs.com/en/components/all/#containment" %}
La liste de tous les composants Vuetify
{% endembed %}

### **Étape 5 - Créer le contenu de la page "Pokédex"**

#### Objectifs :&#x20;

* [ ] Récupérer le magasin Pina des Pokémons et ses données
* [ ] Parcourir le tableau des Pokémons et afficher au minimum les données suivantes&#x20;
  * Nom
  * Image. Elles sont dans `public/images/`  comme pour la carte du monde.
  * Type
  * Niveau
* [ ] Mettre la bonne couleur aux types en changeant la couleur du texte ou de l'arrière-plan.
* [ ] Créer un bouton permettant d'ajouter un Pokémon aux favoris
* [ ] Créer un champ de recherche permettant la recherche d'un Pokémon par son nom

Vous êtes libre de présenter cette liste comme vous le désirez avec les composants Vuetify de votre choix.

Pour créer cette page, vous aurez besoin d'accéder au **magasin Pinia des Pokémons** qui se trouve dans `src/stores/pokemonStore.js`. C'est dans ce magasin que sont stockés tous les Pokémons.

Pour **apprendre à utiliser Pinia**, lire le chapitre suivant :

{% content-ref url="../vue.js/magasin-pinia.md" %}
[magasin-pinia.md](../vue.js/magasin-pinia.md)
{% endcontent-ref %}

### **Étape 6 - Créer le contenu de la page "Favoris"**

La page des favoris ressemble beaucoup à la page d'accueil. Afin de ne pas répéter le code, créer un composant `src/components/PokemonCard.vue`  qui contiendra le code d'une carte Pokémon.

Utiliser ensuite ce composant pour afficher les cartes sur la page d'accueil et sur la carte des favoris.

Modifier l'action `toggleFavorite` du magasin en utilisant le stockage local (localStorage) pour conserver ces favoris en complément du store Pinia.

### **Étape 7 - Créer la fiche de détail d'un Pokémon**

Lorsque l'on clique sur la carte d'un Pokémon, cela va ouvrir sa fiche de détail.

Par exemple pour Carapuce, la route (URL) qui correspond à la fiche de détail sera la suivante [http://localhost:3000/pokemon/4](http://localhost:3000/pokemon/4).&#x20;

En lisant cette route, on comprend que cela va afficher le Pokémon avec l'identifiant `4`.

Cette valeur est appelée un **paramètre d'URL** ou **paramètre de route dynamique** et sera différente pour chaque Pokémon.

Voici comment créer une route dynamique et récupérer la valeur du paramètre.

**Créer la page de détail avec un paramètre id**

1. Dans `src/pages/`, créer un dossier `pokemon/`&#x20;
2. Dans le dossier `pokemon/`, créez un nouveau fichier nommé `[id].vue` \
   `[id]` indique la création d'un paramètre de route `id`

#### **Récupérer le paramètre de la route**

Grâce à la syntaxe `[id].vue`, Vue Router transmet automatiquement la valeur dans la route (URL) au composant. \
\
Pour récupérer ce paramètre, dans le fichier `[id].vue` utilisez `useRoute()`  et `route.params` pour récupérer la valeur du paramètre `id` et l'afficher à l'écran.

Ajouter le code suivant à votre fichier `[id].vue`

{% code title="src/pages/pokemon/[id].vue" lineNumbers="true" %}
```markup
<template>
  <div>
    <h1>Détails du Pokémon</h1>
    <p>Identifiant du Pokémon : {{ pokemonId }}</p>
  </div>
</template>

<script setup>
import { useRoute } from 'vue-router';

const route = useRoute();
const pokemonId = route.params.id;
</script>
```
{% endcode %}

Tester le bon fonctionnement du paramètre avec ces différentes URL

* [http://localhost:3000/pokemon/4](http://localhost:3000/pokemon/4)
* [http://localhost:3000/pokemon/102](http://localhost:3000/pokemon/102)
* [http://localhost:3000/pokemon/carapuce](http://localhost:3000/pokemon/carapuce)

#### Créer un lien dynamique avec paramètres&#x20;

Ajouter maintenant un lien dynamique à votre carte Pokémon pour qu'il ouvre la bonne fiche de détail.

```javascript
<router-link :to="`/pokemon/${pokemon.id}`"> ... </router-link>
// si vous utiliser une v-card
<v-card :to="`/pokemon/${pokemon.id}`"> ... </v-card>
```

Il ne vous reste plus qu'à vous connecter au magasin Pina et récupérer **toutes** les données du Pokémon et à les afficher avec un peu de style et de fantaisie.
