---
layout: editorial
---

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
│   │       └── [nom].vue      # Page de détail d'un Pokemon avec paramètre '/pokemons/pikachu' 
│   │                          #  'pikachu' sera la valeur du paramètre 'nom'
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

La structure d'un projet Vuetify est conçue pour être modulaire et organisée, **facilitant** ainsi le **développement**, la **maintenance** et **l'évolutivité** de votre application.

Comprendre cette anatomie vous permettra d'organiser efficacement votre code et de profiter pleinement des fonctionnalités offertes par Vue.js et Vuetify.

## **Déroulement du chargement d'une application Vue avec Vuetify**

<div data-full-width="false">

<figure><img src="../.gitbook/assets/Chargement projet Vuetify v4.png" alt="Schéma du chargement d&#x27;une application Vue classique avec Vuetify" width="563"><figcaption><p>Schéma du chargement d'une application Vue classique avec Vuetify</p></figcaption></figure>

</div>

<details>

<summary>Étape 1 : Chargement de <code>index.html</code></summary>

Le processus de démarrage de l'application commence par le chargement du fichier `index.html` par le navigateur.

Ce fichier contient la structure de base de la page, dont l'élément  `<div id="app">` où l'application Vue sera montée.

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

</details>

<details>

<summary>Étape 2 : Chargement de <code>src/main.js</code></summary>

Ensuite, le navigateur charge le fichier `main.js`, qui est le point d'entrée principal de l'application Vue.

Ce fichier conduit l'initialisation de l'application en chargeant :

1. Vue → étape 3
2. les plugins (Composants Vuetify, Thème Vuetify, Pinia et Vue Router) → étape 4
3. le composant racine `App.vue` → étape 5

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

</details>

<details>

<summary>Étape 3 : Chargement de Vue</summary>

À ce stade, la bibliothèque Vue elle-même est chargée. C'est le cœur de votre application qui permet de créer des composants réactifs et de gérer les fonctionnalités de Vue.

L'instance Vue est initialisée dans `src/main.js` avec la fonction `createApp()` .&#x20;

</details>

<details>

<summary>Étape 4 : Chargement des outils, plugins et configurations</summary>

Lors de cette étape, les principaux plugins et configurations de l'application sont chargés :

* **Thèmes** : Vuetify applique le [thème](https://vuetifyjs.com/en/features/theme/#theme-configuration) sélectionné (light ou dark) et les [styles globaux](https://vuetifyjs.com/en/styles/colors/#colors) à l'application. La configuration ce fait dans `src/plugins/vuetify.js`.
* **Composants Vuetify** : Vuetify charge l'ensemble de [ses composants](https://vuetifyjs.com/en/components/all/#components) prêts à être utilisés dans l'application.
* **Pinia** : Le magasin, store en anglais,  de gestion d'état de l'application est initialisé pour gérer les données globales. C'est ce magasin qui s'occupera de faire les appels aux API si nécessaire. \
  Site officiel : [https://pinia.vuejs.org/](https://pinia.vuejs.org/)
* **Vue Router** : La configuration de Vue Router est chargée pour permettre la navigation entre les différentes pages de l'application. \
  Site officiel : [https://router.vuejs.org/](https://router.vuejs.org/)
* **Routage automatique :** Vuetify utilise une librairie qui permet la création automatique des routes de l'application en s'établissant sur la structure et le nom des fichiers et dossier du dossier `src/pages/`. \
  Site officiel : [https://uvr.esm.is/guide/file-based-routing.html](https://uvr.esm.is/guide/file-based-routing.html)

Toutes ces initialisations sont réalisées dans le fichier `src/plugins/index.js`.

</details>

<details>

<summary>Étape 5 : Montage du composant <code>App.vue</code></summary>

Une fois tous les plugins et éléments de configuration chargés `App.vue` est monté sur l'élément `<div id="app">` dans `index.html`.&#x20;

Cela signifie que `App.vue` prend le contrôle de l'application et agit comme conteneur principal pour le reste des composants et de l'application.

Comme c'est le premier composant de notre application, on l'appelle le **composant "root"**, **composant** **racine** en français.

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

</details>

<details>

<summary>Étape 6 : Vue Router détermine le composant à charger en fonction de l'URI</summary>

À ce stade, Vue Router vérifie l'URI de l'application (par exemple, `/bulbi`) et détermine quel composant Vue doit être chargé pour cette route.&#x20;

C'est grâce à la configuration des routes que Vue Router sait quel composant est associé à chaque chemin.

Dans ce projet, il détermine le composant à chargé en se basant sur le nom des fichiers et dossier du dossier `src/pages/` grâce à la librairie [Unplugin Vue Router](https://uvr.esm.is/guide/file-based-routing.html).

```
src/pages/
├── index.vue
├── about.vue
└── users/
    ├── index.vue
    └── [id].vue
```

La structure ci-dessus génèrera les routes suivantes :

* `/`: ->  `index.vue`&#x20;
* `/about`: ->  `about.vue`&#x20;
* `/users`: ->  `users/index.vue`&#x20;
*   `/users/77`: ->   `users/[id].vue`   crée un paramètre `id` qui recevra la valeur de l'URI soit  `77` dans cet exemple





</details>

<details>

<summary>Étape 7 : Retour du composant correspondant à la route par Vue Router</summary>

Vue Router renvoie le composant correspondant à la route actuelle (par exemple, `bulbi.vue` pour la route `/bulbi`).

Ce composant est ensuite prêt à être affiché à l'intérieur de l'application.

</details>

<details>

<summary>Étape 8 : Chargement du composant retourné par Vue Router</summary>

Le composant correspondant à la route active (`bulbi.vue` dans cet exemple) est alors chargé et rendu dans la balise `<router-view>` du composant `App.vue`.&#x20;

</details>

<details>

<summary>Étape 9 : Récupération des données dans Pinia</summary>

Une fois que le composant `bulbi.vue` est monté, il récupère les données dont il a besoin à partir du store Pinia.

Par exemple, toutes les données du Pokémon Bulbizarre :  &#x20;

```javascript
{ 
    name: 'Bulbizarre',
    type: 'Plante,Poison',
    level: 15,
    img: 'bulbizarre.png' 
}
```

</details>

<details>

<summary>Étape 10 : Récupération des composants Vuetify</summary>

Le composant `bulbi.vue` utilise les composants Vuetify (`v-btn`, `v-card`, `v-img`, etc.) pour construire l'interface utilisateur, user interface (UI) en anglais.&#x20;

Ces composants sont stylisés et configurés selon le thème Vuetify chargé précédemment.

[Voir tous les composants Vuetify](https://vuetifyjs.com/en/components/all/#containment)

Exemple d'utilisation du composant `v-btn`&#x20;

```markup
<v-btn @click="capturer">
  Capturer Bulbizarre
</v-btn>
```

</details>

<details>

<summary>Étape 11 : Application complète rendue et interactivité assurée</summary>

Enfin, l'application Vue.js est entièrement montée, configurée et rendue dans le navigateur.

L'utilisateur peut interagir avec l'application, naviguer entre les différentes pages grâce à **Vue Router**, utiliser les **composants Vuetify**, et voir les données gérées par **Pinia** en **temps réel**.

</details>
