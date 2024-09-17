# 📅 17 septembre — Leçons 13 à 15

## 🚀 Objectifs du jour

* **Finaliser l'exercice Mini Pokédex**
* **Découverte de Vue.js** : Comprendre les bases de ce framework JavaScript moderne pour créer des interfaces interactives.
* **Mise en place d'une application simple avec Vue.js**

## 📒 Exercice Mini Pokédex

1. **Présentation du code final avec Vue.js** :
   * Introduction à l'utilisation de Vue.js via un CDN (Content Delivery Network).
   * Explication des concepts de base : réactivité, `ref()`, `computed()`, `v-model`, et directives comme `v-if`, `v-for`.
   * Mise en place des fonctions pour capturer et sauvegarder les Pokémon, et afficher le total des captures.
2. **Présentation du projet final** :
   * **Fichier HTML** : Liaison des composants Vue.js avec la structure HTML de l'application.
   * **Fichier JavaScript** : Utilisation de la **Composition API** pour créer une logique réactive sans installer Vue CLI.
   * **Fichier CSS** : Stylisation de l'interface avec des effets dynamiques pour les boutons et les éléments interactifs.

## 🛠 Intro à Vue.js — dépôt de la démo

1. **Créer le dépôt GitHub via GitHub Classroom** : Utilise ce [lien](https://classroom.github.com/a/z9Q4FRir) pour cloner le dépôt de départ avec l'intégration de Vue.js sans Vue CLI.
2. **Cloner le dépôt avec WebStorm** :
   * Utilise l'URL de ton dépôt pour cloner le projet dans WebStorm.
3. **Structure des fichiers à cloner** :
   * **index.html** : Contient la structure HTML avec l'intégration de Vue.js via un CDN.
   * **script.js** : Contient le code JavaScript qui gère la réactivité de l'application avec la **Composition API** de Vue.js.
   * **style.css** : Fichier CSS qui stylise l'interface avec des transitions et des animations pour améliorer l'expérience utilisateur.

### 🖥 Intro à Vue.js — concepts de base

1. **Vue.js via CDN**
   * Utilisation de Vue.js sans Vue CLI, directement à partir d'un CDN (Content Delivery Network).
   * Avantages : Simplicité d'installation et d'utilisation dans de petits projets sans environnement de développement complexe.
   * [Documentation CDN Vue.js](https://vuejs.org/guide/quick-start.html#using-vue-from-cdn)
2. **Composition API**
   * Introduction à la **Composition API** de Vue.js pour créer des composants réactifs.
   * Utilisation de `setup()` pour initialiser les données réactives et définir les fonctions.
   * [Composition API Vue.js](https://vuejs.org/guide/extras/composition-api-faq.html#what-is-the-composition-api)
3. **Réactivité avec** `ref()`
   * Création de données réactives avec `ref()`, permettant de suivre les changements de valeurs dans l'interface utilisateur.
   * Exemple : Gestion du compteur de Pokémon capturés avec `ref()`.
   * [Réactivité avec ref()](https://vuejs.org/api/reactivity-core.html#ref)
4. **Directives Vue.js**
   * `v-model` : Liaison bidirectionnelle des données entre l'interface et la logique JavaScript (liaison des champs de saisie à des données réactives).
     * [Directive v-model](https://vuejs.org/guide/essentials/forms.html#basic-usage)
   * `v-if` **/** `v-else` : Affichage conditionnel d'éléments en fonction de l'état des données réactives.
     * [Directive v-if](https://vuejs.org/guide/essentials/conditional.html#if)
   * `v-for` : Boucle pour afficher dynamiquement des listes d'éléments en fonction d'un tableau de données (ex. : liste des Pokémon capturés).
     * [Directive v-for](https://vuejs.org/guide/essentials/list.html#v-for)
5. **Propriétés calculées avec** `computed()`
   * Introduction à `computed()` pour créer des propriétés dérivées, qui sont recalculées automatiquement lorsqu'une dépendance change.
   * Exemple : Calculer le total des Pokémon capturés à partir d'une liste de captures.
   * [Propriétés calculées avec computed()](https://vuejs.org/guide/essentials/computed.html)
6. **Gestion d'événements**
   * `@click` : Gestion des clics sur les boutons pour déclencher des fonctions spécifiques (ex. : capturer ou sauvegarder des Pokémon).
   * Exemple : Utilisation de `@click` pour déclencher la capture de Pokémon ou la sauvegarde dans la liste.
   * [Gestion des événements avec Vue.js](https://vuejs.org/guide/essentials/event-handling.html)
7. **Directives de style dynamique**
   * `v-bind:class` : Application dynamique de classes CSS en fonction de l'état des données réactives (ex. : changement de style du bouton en fonction de la nécessité de sauvegarder).
   * Exemple : Utilisation de la classe "chaud" pour alerter l'utilisateur quand une sauvegarde est nécessaire.
   * [v-bind:class pour classes dynamiques](https://vuejs.org/guide/essentials/class-and-style.html#binding-html-classes)
8. **Liaison des événements et manipulation du DOM**
   * Gestion du DOM directement via Vue.js, sans utiliser de manipulateurs DOM comme `document.querySelector`.
   * Suppression d'éléments dynamiquement en double-cliquant (ex. : suppression d'une capture dans la liste avec `@dblclick`).
   * [Manipulation du DOM avec Vue.js](https://vuejs.org/guide/essentials/event-handling.html#inline-handlers)
9. **Affichage conditionnel**
   * `v-show` : Afficher un élément dans le DOM sans le retirer, en fonction d'une condition réactive (ex. : affichage d'un message de sauvegarde nécessaire).
     * [Directive v-show](https://vuejs.org/guide/essentials/conditional.html#v-show)
   * `v-if` : Retirer complètement un élément du DOM si la condition n'est pas remplie.
     * [Directive v-if](https://vuejs.org/guide/essentials/conditional.html#if)
10. **Cycle de vie du composant :** `onMounted()`
    * Le **cycle de vie des composants** Vue.js permet d'exécuter du code à différents moments de la vie d'un composant (création, mise à jour, destruction).
    * `onMounted()` est un hook du cycle de vie utilisé pour exécuter du code après que le composant est monté dans le DOM.
    * **Utilisation dans le projet :** Utiliser `onMounted()` pour charger les données de captures sauvegardées dans le **localStorage** lorsque l'application démarre.
      * Exemple : Charger les captures de Pokémon depuis le localStorage et les afficher dans l'application.
    * [Cycle de vie des composants](https://vuejs.org/guide/essentials/lifecycle.html#lifecycle-hooks)

### ✅ Devoirs

1. Faire le tutoriel [Vue Mastey - Intro to Vue 3 (EN)](https://www.vuemastery.com/courses/intro-to-vue-3/intro-to-vue3)

### 📒 Supports de cours supplémentaires

1. [Vue Mastey - Intro to Vue 3 (EN)](https://www.vuemastery.com/courses/intro-to-vue-3/intro-to-vue3)
2. [Vue.js Documentation (FR)](https://fr.vuejs.org/guide/introduction)
3. [OpenClassrooms : Introduction à Vue.js (FR)](https://openclassrooms.com/fr/courses/6390311-creez-une-application-web-avec-vue-js)
