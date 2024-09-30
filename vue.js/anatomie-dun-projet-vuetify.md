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
│                              #  ne nécesssitant PAS de traitements
├── src/                       # Contient le code source principal de l'application
│   │ 
│   ├── assets/                # Dossier pour les ressources statiques (images, polices, styles CSS, etc.)         
│   │                          #  nécessitant un traitement (regroupement, optimisation, compression, etc.)
│   │
│   ├── components/            # Composants réutilisables de l'application
│   │   ├── AppFooter.vue
│   │   ├── AppHeader.vue
│   │   ├── PokemonListe.vue              
│   │   └── PokemonFiche.vue
│   │
│   ├── layouts/               # Contient les différents mise en pages de l'application
│   │   ├── default.vue
│   │   ├── fullWidth.vue
│   │   └── sideBarLeft.vue        
│   │
│   ├── pages/                 # Composants Vue représentant les différentes pages de l'application
│   │   ├── index.vue          # Page principale de l'application '/'
│   │   ├── contact.vue        # Page de contact '/contact'
│   │   ├── [...path].vue      # Page d'erreur pour les pages introuvable
│   │   └── pokemons/          
│   │       ├── index.vue      # Page d'acceuil des Pokemons '/pokemons'
│   │       └── [id].vue       # Page de détail d'un Pokemon avec paramètre '/pokemons/pikachu' 
│   │                          #  'pikachu' sera la valeur du paramètre
│   │
│   ├── plugins/               # Dossier pour les plugins utilisés dans l'application
│   │
│   ├── router/                # Configuration du routeur Vue (vue-router) pour la navigation entre les pages
│   │   └── index.js           # Fichier de configuration des routes de l'application
│   │
│   ├── stores/                # Contient la gestion d'état globale, le magasins (Vuex ou Pinia)
│   │   ├── app.js             # Store principal pour gérer l'état de l'application
│   │   └── index.js           # Fichier d'index pour initialiser les stores
│   │
│   ├── styles/                # Contient les fichiers de styles globaux
│   │   └── settings.scss      # Fichier de styles SCSS pour la configuration de l'application
│   │
│   ├── App.vue                # Composant racine de l'application
│   └── main.js                # Point d'entrée JavaScript qui initialise Vue et Vuetify
│
├── index.html                 # Fichier HTML principal servant de point d'entrée pour l'application
├── jsconfig.json              # Configuration du projet JavaScript
├── package-lock.json          # Verrouillage des dépendances installées
├── package.json               # Fichier de configuration du projet avec les dépendances et scripts
└── vite.config.mjs            # Fichier de configuration pour Vite
```
{% endcode %}

## **Conseils pour Organiser Votre Projet Vuetify**

1. **Utilisez des composants réutilisables** : placez les composants réutilisables (entête et pieds de pages, boutons, cartes, listes, formulaires, etc.) dans le dossier `components/`.&#x20;
2. **Divisez votre logique** : séparez les pages de l'application dans `views/` et les composants spécifiques à ces pages dans `components/`.
3. **Explorer** [**les composants Vuetify** ](https://vuetifyjs.com/en/components/all/#components)**avant de créer un composant :** ne pas réinventer la roue et parcourir les composants Vuetify avant de créer vos propres composants.
4. **Configurez correctement le** [**thème Vuetify**](https://vuetifyjs.com/en/features/theme/) : utilisez `plugins/vuetify.js` pour personnaliser les couleurs, polices, et styles de votre projet.

{% embed url="https://vuetifyjs.com/en/components/all/#components" %}
Les composants Vuetify
{% endembed %}

{% embed url="https://vuetifyjs.com/en/features/theme/#theme-configuration" %}
Configurer le thème Vuetify
{% endembed %}

### **Conclusion**

La structure d'un projet Vuetify est conçue pour être modulaire et organisée, **facilitant** ainsi le **développement**, la **maintenance**, et **l'évolutivité** de votre application.

Comprendre cette anatomie vous permettra d'organiser efficacement votre code et de profiter pleinement des fonctionnalités offertes par Vue.js et Vuetify.

## **Déroulement du chargement d'une application Vue avec Vuetify**

<div data-full-width="true">

<figure><img src="../.gitbook/assets/Chargement projet Vuetify.png" alt=""><figcaption><p>Schéma du chargement d'une application Vue classique avec Vuetify</p></figcaption></figure>

</div>

<details>

<summary>Étape 1 : Chargement de <code>index.html</code></summary>

Le processus de démarrage de l'application commence avec le chargement du fichier `index.html` par le navigateur. Ce fichier contient la structure de base de la page, y compris le conteneur `<div id="app">` où l'application Vue.js sera montée.

</details>

<details>

<summary>Étape 2 : Chargement de <code>main.js</code></summary>

Ensuite, le navigateur charge le fichier `main.js`, qui est le point d'entrée principal de l'application Vue. Ce fichier gère l'initialisation de l'application en important Vue, les plugins, et le composant racine `App.vue`.



</details>

<details>

<summary>Étape 3 : Chargement de Vue</summary>

À ce stade, la bibliothèque Vue.js elle-même est chargée. C'est le cœur de votre application qui permet de créer des composants réactifs et de gérer les fonctionnalités de Vue. L'instance Vue est initialisée à partir de la fonction `createApp()`.



</details>

<details>

<summary>Étape 4 : Chargement des éléments de configuration (Thèmes, Vuetify et ses composants, Pinia, Vue Router)</summary>

Lors de cette étape, les principaux plugins et configurations de l'application sont chargés :

* **Thèmes** : Vuetify applique les thèmes et les styles globaux à l'application.
* **Composants Vuetify** : Vuetify charge l'ensemble de ses composants prêts à être utilisés dans l'application.
* **Pinia** : Le store de gestion d'état de l'application est initialisé pour gérer les données globales.
* **Vue Router** : La configuration de Vue Router est chargée pour permettre la navigation entre les différentes pages de l'application.

</details>

<details>

<summary>Étape 5 : Montage du composant <code>App.vue</code></summary>

Une fois tous les plugins et éléments de configuration chargés, le composant racine `App.vue` est monté sur l'élément `<div id="app">` dans `index.html`. Cela signifie que `App.vue` prend le contrôle de l'application et agit comme conteneur principal pour le reste des composants.

</details>

<details>

<summary>Étape 6 : Vue Router détermine le composant à charger en fonction de l'URI</summary>

À ce stade, Vue Router vérifie l'URI de l'application (par exemple, `/bulbi`) et détermine quel composant Vue doit être chargé pour cette route. C'est grâce à la configuration des routes définie précédemment que Vue Router sait quel composant est associé à chaque chemin.

</details>

<details>

<summary>Étape 7 : Retour du composant correspondant à la route par Vue Router</summary>

Vue Router renvoie le composant correspondant à la route actuelle (par exemple, `bulbi.vue` pour la route `/bulbi`). Ce composant est ensuite prêt à être affiché à l'intérieur de l'application.

</details>

<details>

<summary>Étape 8 : Chargement du composant retourné par Vue Router</summary>

Le composant correspondant à la route active (`bulbi.vue` dans cet exemple) est alors chargé et rendu dans la balise `<router-view>` du composant `App.vue`. C'est à ce moment que l'utilisateur voit le contenu de la page correspondant à la route actuelle.

</details>

<details>

<summary>Étape 9 : Récupération des données dans Pinia</summary>

Une fois que le composant `bulbi.vue` est monté, il récupère les données dont il a besoin à partir du store Pinia. Ces données peuvent inclure des informations partagées entre différents composants de l'application, ce qui permet à `bulbi.vue` de disposer de l'état global ou spécifique nécessaire à son affichage.



</details>

<details>

<summary>Étape 10 : Récupération des composants Vuetify</summary>

Le composant `bulbi.vue` utilise les composants Vuetify (`v-btn`, `v-card`, `v-img`, etc.) pour construire l'interface utilisateur. Ces composants sont stylisés et configurés selon le thème Vuetify qui a été chargé précédemment.

</details>

<details>

<summary>Étape 11 : Application complète rendue et interactivité assurée</summary>

Enfin, l'application Vue.js est entièrement montée, configurée, et rendue dans le navigateur. L'utilisateur peut interagir avec l'application, naviguer entre les différentes pages grâce à Vue Router, utiliser les composants Vuetify, et voir les données gérées par Pinia en temps réel

</details>



### Étape 1 : Chargemt

**1. `index.html` Le point de départ**

Votre fichier `index.html` est le premier fichier chargé par le navigateur.

<pre class="language-html" data-title="index.html" data-line-numbers data-full-width="true"><code class="lang-html">&#x3C;!DOCTYPE html>
&#x3C;html lang="en">

&#x3C;head>
  &#x3C;meta charset="UTF-8" />
  &#x3C;link rel="icon" href="/favicon.ico" />
  &#x3C;meta name="viewport" content="width=device-width, initial-scale=1.0" />
  &#x3C;title>Welcome to Vuetify 3&#x3C;/title>
&#x3C;/head>

&#x3C;body>
<strong>  &#x3C;div id="app">&#x3C;/div> &#x3C;!-- Conteneur principal de l'application Vue -->
</strong>  &#x3C;script type="module" src="/src/main.js">&#x3C;/script> &#x3C;!-- Lancement de l'application via src/main.js -->
&#x3C;/body>

&#x3C;/html>
</code></pre>

#### **Ce qui se passe ici**

* Le navigateur charge `index.html` et crée une structure HTML de base.
* L'élément `<div id="app"></div>` est un conteneur vide qui sera rempli par notre application Vue.
* Le script `<script type="module" src="/src/main.js"></script>` indique au navigateur de démarrer l'application en chargeant `main.js`.

### &#x20;**2. `src/main.js` Initialisation de Vue et Vuetify**

Voici le contenu de votre fichier `main.js` qui est chargé à la `ligne 13` de `index.html`

{% code title="src/main.js" lineNumbers="true" fullWidth="true" %}
```javascript
/**
 * main.js
 *
 * Bootstraps Vuetify and other plugins then mounts the App`
 */

// Importation des plugins enregistrés pour l'application
import { registerPlugins } from '@/plugins'

// Importation du composant racine de l'application Vue (App.vue)
import App from './App.vue'

// Importation de la fonction createApp de Vue.js pour créer une nouvelle instance de l'application
import { createApp } from 'vue'

// Création de l'instance principale de l'application Vue avec le composant App comme composant racine
const app = createApp(App)

// Enregistrement des plugins nécessaires pour l'application, comme Vuetify ou d'autres bibliothèques tierces
registerPlugins(app)

// Montage de l'application Vue sur l'élément DOM avec l'ID "app" pour rendre l'application dans la page HTML
app.mount('#app')
```
{% endcode %}

#### **Ce qui se passe ici**

* `createApp(App)`: Crée une instance de l'application Vue en utilisant `App.vue` comme composant racine (le premier composant de l'application).
* `registerPlugins(app)`: Enregistre et configure les plugins nécessaires pour l'application, notamment Vuetify. Les plugins sont définis dans `src/plugins/index.js`
* `app.mount('#app')`: Monte l'application Vue dans le conteneur `<div id="app"></div>` défini à la `ligne 12` de `index.html`.

À ce stade, l'application Vue est initialisée, et le composant `App.vue` est prêt à être affiché.

### **3. `src/App.vue` : Le composant racine**

C'est le premier composant de notre application, on l'appelle le **composant "root"**, composant racine en français.

{% code title="src/App.vue" lineNumbers="true" fullWidth="true" %}
```markup
<template>
  <v-app> <!-- Composant racine de l'application Vuetify. Applique les styles et fonctionnalités globales de Vuetify -->
    <v-main> <!-- Le contenu principal de la page -->
      <router-view /> <!-- Composant de Vue Router qui affiche le contenu de la route actuelle, permettant le rendu dynamique des pages -->
    </v-main>
  </v-app>
</template>

<script setup>
 
</script>
```
{% endcode %}

#### **Ce qui se passe ici**

* `<v-app>` : Composant de base de Vuetify qui enveloppe toute l'application, assurant l'intégration des thèmes et styles.
* `<router-view />` : Place un espace réservé qui affichera le composant correspondant à la route actuelle (par exemple, la page d'accueil).

### **4. `router/index.js` : Gestion de la navigation avec le** routage basé sur les fichiers

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

### **5. `pages/index.vue` : Affichage de la page d'accueil**

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
