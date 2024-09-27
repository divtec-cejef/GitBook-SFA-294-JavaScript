# Anatomie d'un projet Vuetify

Lors de la création d'un projet Vuetify, il est important de comprendre la structure des fichiers et des dossiers pour bien organiser votre code et faciliter la maintenance.

Voici un aperçu de l'anatomie d'un projet Vuetify typique.

## **Structure Générale d'un Projet Vuetify**

{% code fullWidth="true" %}
```
hello-world/                   # Dossier racine du projet Vuetify
│
├── node_modules/              # Contient les bibliothèques installés avec NPM, dont Vue.js  
│
├── public/                    # Contient les fichiers accessibles publiquement (images, icônes, pdf)
│   └── favicon.ico            
│
├── src/                       # Contient le code source principal de l'application
│   │ 
│   ├── assets/                # Dossier pour les ressources statiques (images, polices, styles CSS, etc.)         
│   │   └── logo.svg             nécessitant un traitement, une optimisation, une compression.
│   │
│   ├── components/            # Composants réutilisables de l'application
│   │   ├── AppFooter.vue      # Composant Vue pour le pied de page de l'application
│   │   └── HelloWorld.vue     # Exemple de composant Vue réutilisable
│   │
│   ├── layouts/               # Contient les différents mise en pages de l'application
│   │   └── default.vue        # Mise en page par défaut de l'application (avec en-tête, pied de page, etc.)
│   │
│   ├── pages/                 # Composants Vue représentant les différentes pages de l'application
│   │   ├── index.vue          # Page principale de l'application
│   │   └── contact.vue        # Page de contact
│   │
│   ├── plugins/               # Dossier pour les plugins utilisés dans l'application
│   │   ├── index.js           # Fichier principal d'initialisation des plugins
│   │   └── vuetify.js         # Configuration de Vuetify pour le projet
│   │
│   ├── router/                # Configuration du routeur Vue (vue-router) pour la navigation entre les pages
│   │   └── index.js           # Fichier de configuration des routes de l'application
│   │
│   ├── stores/                # Contient la gestion d'état globale (Vuex ou Pinia) de l'application
│   │   ├── app.js             # Store principal pour gérer l'état de l'application
│   │   └── index.js           # Fichier d'index pour initialiser les stores
│   │
│   ├── styles/                # Contient les fichiers de styles globaux
│   │   └── settings.scss      # Fichier de styles SCSS pour la configuration de l'application
│   │
│   ├── App.vue                # Composant racine de l'application
│   ├── main.js                # Point d'entrée JavaScript qui initialise Vue et Vuetify
│   └── vite-env.d.ts          # Fichier d'extension de TypeScript pour Vite
│
├── index.html                 # Fichier HTML principal servant de point d'entrée pour l'application
├── jsconfig.json              # Configuration du projet JavaScript
├── package-lock.json          # Verrouillage des dépendances installées
├── package.json               # Fichier de configuration du projet avec les dépendances et scripts
└── vite.config.mjs            # Fichier de configuration pour Vite
```
{% endcode %}

## **Description des Dossiers et Fichiers**

### **Dossier Racine**

* **`package.json`** : Contient les informations sur votre projet et les dépendances nécessaires, comme Vue, Vuetify, et d'autres bibliothèques installées.
* **`.env`** : Permet de configurer les variables d'environnement, comme les API Keys.
* **`vue.config.js`** : Fichier de configuration optionnel pour personnaliser la configuration de Vue CLI.
* **`.gitignore`** : Définit les fichiers et dossiers à ignorer par Git.

### **Dossier `public/`**

* **`index.html`** : Le fichier HTML principal qui sert de point d'entrée de l'application. Le contenu de votre application Vuetify est injecté ici.
* **`favicon.ico`** : Icône du site web affichée dans les onglets du navigateur.

### **Dossier `src/`**

Ce dossier contient la logique et les composants principaux de votre projet.

* **`main.js`** : Fichier d'entrée JavaScript de votre application. Il initialise Vue, Vuetify, et monte l'application sur la page HTML.
* **`App.vue`** : Le composant racine de votre application. C'est ici que votre application commence.

#### **Sous-dossiers de `src/` :**

* **`assets/`** : Contient les ressources statiques comme les images, les fichiers CSS, ou les polices de caractères.
* **`components/`** : Ce dossier contient les composants réutilisables de l'application. Chaque composant Vue (.vue) correspond à une partie de l'interface utilisateur.
* **`layouts/`** : Contient les dispositions globales de votre application. Par exemple, `DefaultLayout.vue` pourrait définir la barre de navigation et le pied de page.
* **`plugins/`** : Utilisé pour configurer et initialiser les plugins que vous utilisez dans votre projet. Par exemple, `vuetify.js` configure Vuetify et ses options.
* **`router/`** : Contient les fichiers de configuration du routeur Vue (vue-router), ce qui permet de gérer la navigation entre les différentes pages de votre application.
* **`store/`** : Contient les fichiers de gestion d'état de votre application en utilisant Vuex. Cela permet de gérer l'état global de l'application.
* **`views/`** : Contient les composants de vue qui représentent les pages de l'application. Par exemple, `Home.vue` serait la page d'accueil.

## **Conseils pour Organiser Votre Projet Vuetify**

1. **Utilisez des composants réutilisables** : Placez les composants réutilisables (boutons, cartes, formulaires) dans le dossier `components/`.
2. **Divisez votre logique** : Séparez les pages de l'application dans `views/` et les composants spécifiques à ces pages dans `components/`.
3. **Configurez correctement le thème** : Utilisez `plugins/vuetify.js` pour personnaliser les couleurs, polices, et styles de votre projet.

### **Conclusion**

La structure d'un projet Vuetify est conçue pour être modulaire et organisée, **facilitant** ainsi le **développement**, la **maintenance**, et **l'évolutivité** de votre application.

Comprendre cette anatomie vous permettra d'organiser efficacement votre code et de profiter pleinement des fonctionnalités offertes par Vue.js et Vuetify.

## **Déroulement de l'affichage de la page d'accueil**

**1. `index.html` : Le point de départ**

Votre fichier `index.html` est le premier fichier chargé par le navigateur. Voici son contenu :

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8" />
  <link rel="icon" href="/favicon.ico" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Welcome to Vuetify 3</title>
</head>

<body>
  <div id="app"></div> <!-- Conteneur principal de l'application Vue -->
  <script type="module" src="/src/main.js"></script> <!-- Lancement de l'application via main.js -->
</body>

</html>
```

**Ce qui se passe ici :**

* Le navigateur charge `index.html` et crée une structure HTML de base.
* L'élément `<div id="app"></div>` est un conteneur vide qui sera rempli par notre application Vue.
* Le script `<script type="module" src="/src/main.js"></script>` indique au navigateur de démarrer l'application en chargeant `main.js`.

**2. `main.js` : Initialisation de Vue et Vuetify**

Voici le contenu de votre fichier `main.js` :

```javascript
/**
 * main.js
 *
 * Bootstraps Vuetify and other plugins then mounts the App`
 */

// Plugins
import { registerPlugins } from '@/plugins'

// Components
import App from './App.vue'

// Composables
import { createApp } from 'vue'

const app = createApp(App)

registerPlugins(app)

app.mount('#app')
```

**Ce qui se passe ici :**

* `createApp(App)`: Crée une instance de l'application Vue en utilisant `App.vue` comme composant racine.
* `registerPlugins(app)`: Enregistre et configure les plugins nécessaires pour l'application, notamment Vuetify.
* `app.mount('#app')`: Monte l'application Vue dans le conteneur `<div id="app"></div>` défini dans `index.html`.

À ce stade, l'application Vue est initialisée, et le composant `App.vue` est prêt à être affiché.

**3. `App.vue` : Le composant racine**

Bien que je n'aie pas pu accéder directement à votre `App.vue`, il est probable que ce fichier ressemble à ceci :

```vue
<template>
  <v-app> <!-- Composant Vuetify principal qui enveloppe l'application -->
    <router-view /> <!-- Composant de routeur qui affiche la page correspondante à la route actuelle -->
  </v-app>
</template>

<script setup>
// Configuration ou logique spécifique du composant App
</script>
```

**Ce qui se passe ici :**

* `<v-app>` : Composant de base de Vuetify qui enveloppe toute l'application, assurant l'intégration des thèmes et styles.
* `<router-view />` : Place un espace réservé qui affichera le composant correspondant à la route actuelle (par exemple, la page d'accueil).

#### **4. `router/index.js` : Gestion de la navigation avec le** routage basé sur les fichiers

{% embed url="https://uvr.esm.is/guide/file-based-routing.html" %}
Plugin Vue Router pour le routage basé sur les fichiers
{% endembed %}

Votre fichier `index.js` du routeur utilise le système de **routage automatique** de Vue Router. Voici le contenu de ce fichier :

```javascript
/**
 * router/index.ts
 *
 * Automatic routes for `./src/pages/*.vue`
 */

// Composables
import { createRouter, createWebHistory } from 'vue-router/auto'
import { setupLayouts } from 'virtual:generated-layouts'
import { routes } from 'vue-router/auto-routes'

const router = createRouter({
  history: createWebHistory(import.meta.env.BASE_URL),
  routes: setupLayouts(routes),
})

// Workaround for https://github.com/vitejs/vite/issues/11804
router.onError((err, to) => {
  if (err?.message?.includes?.('Failed to fetch dynamically imported module')) {
    if (!localStorage.getItem('vuetify:dynamic-reload')) {
      console.log('Reloading page to fix dynamic import error')
      localStorage.setItem('vuetify:dynamic-reload', 'true')
      location.assign(to.fullPath)
    } else {
      console.error('Dynamic import error, reloading page did not fix it', err)
    }
  } else {
    console.error(err)
  }
})

router.isReady().then(() => {
  localStorage.removeItem('vuetify:dynamic-reload')
})

export default router
```

#### **Ce qui se passe ici :**

1. **Routage automatique avec `vue-router/auto`** :
   * `import { createRouter, createWebHistory } from 'vue-router/auto'`: La bibliothèque `vue-router/auto` permet un routage automatique, en générant les routes à partir des fichiers `.vue` situés dans votre projet.
   * `import { routes } from 'vue-router/auto-routes'`: Cela importe automatiquement les routes basées sur la structure de vos fichiers dans `src/pages/`.
2. **Configuration des routes** :
   * `createRouter(...)` crée une instance du routeur Vue.
   * `history: createWebHistory(import.meta.env.BASE_URL)`: Utilise l'historique de navigation HTML5 pour gérer les URLs sans le `#` (hash) dans les routes.
   * `routes: setupLayouts(routes)`: La fonction `setupLayouts` configure les layouts pour les routes automatiquement générées.
3. **Le fichier `index.vue`** :
   * Le routage automatique détecte votre fichier `index.vue` situé dans le dossier `pages/` et l’associe automatiquement à la route `/`.
   * Cela signifie que la page d'accueil (`/`) de votre application est automatiquement liée au composant `index.vue`.
4. **Gestion des erreurs de chargement dynamique** :
   * Le routeur inclut un gestionnaire d'erreurs (`router.onError`) pour résoudre les problèmes de chargement des modules dynamiques. S'il y a une erreur de chargement, la page se recharge pour tenter de résoudre le problème.

**En résumé :** Le routage de votre application est configuré automatiquement en se basant sur la structure des fichiers `.vue` dans votre projet. Le fichier `index.vue` situé dans `src/pages/` est automatiquement associé à la route `/`, ce qui en fait la page d'accueil de votre application. Ce système de routage automatique permet de simplifier la gestion des routes, sans avoir besoin de les définir manuellement.

**5. `pages/index.vue` : Affichage de la page d'accueil**

Enfin, votre `index.vue` dans le dossier `pages/` définit le contenu de la page d'accueil. Voici son contenu :

```vue
<template>
  <div class="home">
    <h1>Bienvenue sur la page d'accueil</h1>
    <p>Ceci est une application Vuetify avec une page d'accueil dynamique !</p>
  </div>
</template>

<script setup>
// Aucun code spécifique n'est nécessaire ici pour cet exemple de page d'accueil
</script>

<style scoped>
.home {
  padding: 20px;
  text-align: center;
}
</style>
```

**Ce qui se passe ici :**

* Le composant `index.vue` affiche un titre et un paragraphe de bienvenue.
* Ce contenu est affiché dans `<router-view />` de `App.vue`, qui à son tour est injecté dans `index.html`.

#### **Récapitulatif du cheminement et de l'ordre d'exécution :**

1. **Chargement de `index.html`** : Le navigateur charge la structure HTML de base et l'élément `<div id="app"></div>`.
2. **Exécution de `main.js`** : Vue est initialisé, Vuetify est configuré, et `App.vue` est monté à l'intérieur de `#app`.
3. **Affichage de `App.vue`** : `App.vue` contient `<router-view />` qui attend que le routeur définisse la page à afficher.
4. **Configuration du routeur (`router/index.js`)** : Le routeur détermine que la route `/` correspond à `pages/index.vue`.
5. **Affichage de `pages/index.vue`** : La page d'accueil est chargée et affichée dans `<router-view />`.

Votre projet est maintenant configuré pour afficher la page d'accueil en utilisant Vuetify, Vue Router, et les composants définis dans vos fichiers.
