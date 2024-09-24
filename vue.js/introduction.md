# Introduction

## **Utilisation des SFC (Single File Components) et de l'API Composition dans ce cours**

Dans ce cours, nous utilisons des **Single File Components (SFC)**, un format de fichier spécial avec l'extension `.vue` qui permet de structurer chaque composant de manière claire et organisée. Les SFC contiennent trois sections principales :

* `<template>` : Contient le balisage HTML du composant.
* `<script>` : Inclut la logique JavaScript du composant.
* `<style>` : Contient les styles CSS spécifiques au composant.

### **API Composition**

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
// Importation de ref et réactive 
import { ref, reactive } from "vue";

// Création d'une variable réactive avec `ref`
const compteur = ref(0);

// Création d'un objet réactif avec `reactive`
const utilisateur = reactive({
  nom: "Alice",
  age: 25
});

// Fonction pour incrémenter l'âge de l'utilisateur
function incrementerAge() {
  utilisateur.age++;
}
</script>

<template>
  <div class="main">
    <p>Compteur: {{ compteur }}</p>
    <button @click="compteur++">Incrémenter le compteur</button>

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

Ainsi, les exemples de code présentés dans ce cours sont établis sur ces concepts de **SFC** et de l’**API Composition** pour offrir une approche moderne et efficace du développement avec Vue.js.
