---
cover: ../.gitbook/assets/vuetify.png
coverY: 0
---

# Introduction à Vue et Vuetify

## **Utilisation de Vuetify dans ce cours**

Dans ce cours, nous allons utiliser [**Vuetify**](https://vuetifyjs.com/), une bibliothèque de composants établie sur [**Material Design**](https://material.io/design) pour Vue.js.&#x20;

Vuetify nous permettra de créer rapidement des interfaces utilisateur élégantes, réactives, et cohérentes, en nous appuyant sur une large collection de composants préconçus (boutons, cartes, formulaires, etc.) que nous pourrons personnaliser et intégrer facilement dans nos applications.

#### Exemple de composant `BUTTON`

{% embed url="https://vuetifyjs.com/en/components/buttons/#usage" %}

<div data-full-width="false">

<figure><img src="../.gitbook/assets/Screenshot 2024-09-24 at 11.36.48.png" alt=""><figcaption><p>Exemple du composant <code>BUTTON</code> et de son utilisation</p></figcaption></figure>

</div>

### **D'autres outils disponibles**

Il existe d'autres bibliothèques et frameworks d'interface utilisateur compatibles avec Vue.js :

* [**BootstrapVue**](https://bootstrap-vue.org/) : Basé sur Bootstrap, il fournit des composants classiques et une mise en page fluide.
* [**Quasar**](https://quasar.dev/) : Un framework complet pour créer des applications web, mobiles, et de bureau.
* [**Element Plus**](https://element-plus.org/) : Offre une grande collection de composants professionnels adaptés aux projets d'envergure.
* [**Ant Design Vue**](https://www.antdv.com/) : Basé sur le design system d'Ant Design, idéal pour les applications d'entreprise.

### **Pourquoi utiliser Vuetify ?**

Vuetify est un excellent choix pour débuter, car il est bien documenté, facile à utiliser, et garantit une cohérence visuelle grâce à Material Design.

Cependant, connaître d'autres outils vous permettra d'adapter vos choix selon les besoins et la nature de vos futurs projets.

## **Utilisation des SFC (Single File Components) et de l'API Composition dans ce cours**

```markup
<script setup>
import { ref } from 'vue'
const greeting = ref('Hello World!')
</script>

<template>
  <p class="greeting">{{ greeting }}</p>
</template>

<style>
.greeting {
  color: red;
  font-weight: bold;
}
</style>
```

Dans ce cours, nous utilisons des **Single File Components (SFC)**, un format de fichier spécial avec l'extension `.vue` qui permet de structurer chaque composant de manière claire et organisée. Les SFC contiennent trois sections principales :

* `<template>` : Contient le balisage HTML du composant.
* `<script>` : Inclut la logique JavaScript du composant.
* `<style>` : Contient les styles CSS spécifiques au composant.

### **API Composition**

<div data-full-width="true">

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption><p>Différence entre l'API option (gauche) et composition (droite)</p></figcaption></figure>

</div>

Nous utilisons également l'**API Composition**, une approche plus moderne et flexible pour structurer la logique d’un composant dans Vue.js 3.&#x20;

**Caractéristiques de l'API Composition :**

* Utilisation de `ref` et `reactive` pour la gestion de la réactivité.
* `setup` ajouter en attribut de la balise `<script>` est la fonction clé où toute la logique du composant est définie.

{% hint style="danger" %}
Pour pouvoir utiliser `ref` et `reactive`, il faudra **les importer au tout début du code** comme présenter à la ligne 3 de l'exemple ci-après.
{% endhint %}

### **Exemple**

{% code lineNumbers="true" %}
```html
<script setup>
import { ref, reactive } from "vue";
// Création d'une valeur réactive avec `ref`
const compteur = ref(0);

// Création d'un objet réactif avec `reactive`
const utilisateur = reactive({
  nom: "Alice",
  age: 25
});

// Fonction pour incrémenter le compteur
function incrementer() {
  compteur.value++; // .value obligatoire pour accéder à la valeur réactive
}
  
// Fonction pour incrémenter l'âge de l'utilisateur
function incrementerAge() {
  utilisateur.age++; // pas de .value pour les objets réactifs
}
</script>

<template>
  <div class="main">
    <p>Compteur: {{ compteur }}</p>
    <button @click="incrementer">Incrémenter le compteur</button>

    <p>Personne: {{ utilisateur.nom }} {{ utilisateur.age }} ans</p>
    <button @click="incrementerAge">Incrémenter l'âge</button>
  </div>
</template>

<style scoped>
.main {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

button {
  color: #4fc08d;
  background: none;
  border: solid 1px;
  border-radius: 2em;
  font: inherit;
  padding: 0.75em 2em;
  transition: all 0.3s;
}

button:hover {
  color: white;
  background: #4fc08d;
}
</style>

```
{% endcode %}

{% embed url="https://codepen.io/fallinov/pen/OJKJaLq" %}

### **Pourquoi cette approche ?**

* **Organisation du code** : L'utilisation des SFC et de l'API Composition facilite la maintenance du code en regroupant la logique liée.
* **Réutilisabilité** : Le code est plus modulaire et réutilisable.
* **Flexibilité** : L'API Composition permet de mieux structurer le code pour les composants complexes, notamment dans les projets plus grands.

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption><p>Découpage et réutilisation des composants Vue</p></figcaption></figure>

Ainsi, les exemples de code présentés dans ce cours sont établis sur ces concepts de **SFC** et de l’**API Composition** pour offrir une approche moderne et efficace du développement avec Vue.js.

{% file src="../.gitbook/assets/Vue-3-Cheat-Sheet.pdf" %}
Cheat Sheet pour Vue 3 SFC et composition API
{% endfile %}

## Méthodes de rendu web

L'objectif de ce chapitre est de vous familiariser avec les différentes techniques de rendu disponibles pour vos projets web utilisant Vue.js. Chaque technique de rendu a été conçue pour répondre à des **besoins spécifiques en matière de performances, de référencement (SEO), et d'expérience utilisateur**. Comme développeurs, il est important de comprendre ces différences afin de **choisir la méthode la plus adaptée à chaque projet**.

Ces différentes techniques existent parce que les applications web ont des exigences variées. Certaines applications nécessitent une indexation optimale par les moteurs de recherche (SEO), tandis que d'autres privilégient la rapidité ou l'interactivité. De plus, selon la nature du contenu (statique ou dynamique), la manière dont les pages sont générées et servies aux utilisateurs peut grandement influencer les performances et l'expérience utilisateur.

Le tableau ci-dessous vous offre une vue d'ensemble des principales méthodes de rendu, leurs avantages, leurs inconvénients, et les contextes dans lesquels elles sont le plus appropriées.

{% hint style="info" %}
Dans ce cours, nous utiliserons la méthode CSR, car elle est la plus simple à mettre en place.
{% endhint %}

<table data-full-width="true"><thead><tr><th width="158">Méthode</th><th width="219">Utilisation</th><th width="308">Résumé</th><th width="71" align="center">SEO</th><th width="140" align="center">Perfs</th><th align="center">Serveur JS</th></tr></thead><tbody><tr><td>CSR</td><td>Applications SPA<br>(Single Page Application)</td><td>Rendu côté client, interactivité après chargement complet du JavaScript.</td><td align="center">❌</td><td align="center">🔴</td><td align="center">❌</td></tr><tr><td>PWA (CSR)</td><td>Expériences mobiles</td><td>Application web hors ligne.</td><td align="center">❌</td><td align="center">🟡</td><td align="center">❌</td></tr><tr><td>SSR</td><td>Applications dynamiques</td><td>Rendu côté serveur.</td><td align="center">✅</td><td align="center">🟠</td><td align="center">✅</td></tr><tr><td>SSG</td><td>Sites à contenu statique</td><td>Pages statiques.</td><td align="center">✅</td><td align="center">🟢</td><td align="center">❌</td></tr><tr><td>ISR</td><td>Contenus semi-dynamiques</td><td>Combinaison SSR/SSG, contenu dynamique, régénération périodique possible.</td><td align="center">✅</td><td align="center">🟢</td><td align="center">✅</td></tr><tr><td>Pre-rendering</td><td>Amélioration de SEO</td><td>Pré-rendu HTML, partiellement dynamique, améliorant chargement initial.</td><td align="center">✅</td><td align="center">🟢</td><td align="center">❌</td></tr></tbody></table>

* **SEO** : Indique si la méthode est favorable au référencement naturel.
* **Perfs (Performances) :** 🟢 : Excellent 🟡 : Moyen 🟠 : Moyenne à mauvaise 🔴 : Mauvais
* **Serveur JS** : Si un serveur JavaScript est requis (✅) ou non (❌).
