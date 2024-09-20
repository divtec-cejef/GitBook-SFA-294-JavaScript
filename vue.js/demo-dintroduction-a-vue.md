# Introduction à Vue

Création d'un dépôt pour la démo : [https://classroom.github.com/a/wbeFruIa](https://classroom.github.com/a/wbeFruIa)

## Étape 1 : Initialisation de Vue.js

**Objectif :** Créer une première application Vue.js et afficher un message réactif.

1.  **Inclure Vue.js via CDN**\
    Ajoutez Vue.js dans le fichier `index.html` :

    ```html
    <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
    ```
2.  **Créer une instance Vue**\
    Initialisez Vue.js dans le fichier `script.js` et liez-le à un élément avec l'ID `poke-app`.

    ```javascript
    const { createApp } = Vue;

    createApp({
      setup() {
        const message = "Bienvenue dans PokeCount!";
        return { message };
      }
    }).mount("#poke-app");
    ```
3.  **Utiliser l'interpolation dans le HTML**\
    Dans le fichier HTML, utilisez la syntaxe `{{ message }}` pour afficher le message.

    ```html
    <h1>{{ message }}</h1>
    ```

***

## Étape 2 : Réactivité avec `ref`

**Objectif :** Ajouter un compteur réactif pour capturer des Pokémon.

1.  **Créer une donnée réactive**\
    Utilisez `ref()` dans le fichier `script.js` pour créer une variable réactive `compteur`.

    ```javascript
    const compteur = ref(0);
    ```
2.  **Incrémenter le compteur**\
    Créez une fonction pour capturer des Pokémon et incrémenter le compteur.

    ```javascript
    function capturer() {
      compteur.value += 1;
    }
    ```
3.  **Afficher le compteur et ajouter un bouton**\
    Dans le fichier `index.html`, utilisez `v-on` ou `@click` pour capturer un Pokémon.

    ```html
    <p>Pokémons capturés : {{ compteur }}</p>
    <button @click="capturer">Capturer 🐢</button>
    ```

***

## Étape 3 : Sauvegarder les captures

**Objectif :** Ajouter une fonctionnalité pour sauvegarder les captures.

1.  **Créer une liste réactive pour stocker les captures**\
    Utilisez `ref` pour créer une liste réactive des captures.

    ```javascript
    const capturesTab = ref([]);
    ```
2.  **Créer la fonction `sauver`**\
    Créez une fonction qui ajoute le compteur à la liste des captures et réinitialise le compteur.

    ```javascript
    function sauver() {
      if (compteur.value > 0) {
        capturesTab.value.push(compteur.value);
        compteur.value = 0;
      }
    }
    ```
3.  **Activer/Désactiver le bouton "Sauver"**\
    Utilisez `v-bind:disabled` pour désactiver le bouton si le compteur est à zéro.

    ```html
    <button @click="sauver" :disabled="compteur === 0">Sauver 💾</button>
    ```

***

## Étape 4 : Afficher les captures dans une liste

**Objectif :** Afficher les captures dans une liste et gérer le cas où la liste est vide.

1.  **Boucler avec `v-for`**\
    Utilisez `v-for` pour parcourir les éléments de la liste et les afficher.

    ```html
    <ul>
      <li v-for="(capture, index) in capturesTab" :key="index">
        {{ capture }} Pokémon capturé(s)
      </li>
    </ul>
    ```
2.  **Gérer le cas où la liste est vide avec `v-if`**\
    Ajoutez une condition pour afficher un message si la liste est vide.

    ```html
    <p v-if="capturesTab.length === 0">Aucune capture pour le moment.</p>
    ```

***

## Étape 5 : Suppression de toutes les captures

**Objectif :** Permettre aux utilisateurs de supprimer toutes les captures avec un bouton.

1.  **Ajouter un bouton de suppression**\
    Ajoutez un bouton qui réinitialise la liste des captures.

    ```html
    <button @click="capturesTab = []" :disabled="capturesTab.length === 0">
      Supprimer toutes les captures 🗑️
    </button>
    ```

***

## Étape 6 : Suppression des captures avec un double-clic

**Objectif :** Permettre aux utilisateurs de supprimer une capture spécifique en double-cliquant dessus.

1.  **Utiliser `@dblclick` pour supprimer une capture**\
    Utilisez l'événement `dblclick` pour supprimer un élément spécifique de la liste.

    ```html
    <li v-for="(capture, index) in capturesTab" :key="index" @dblclick="capturesTab.splice(index, 1)">
      {{ capture }} Pokémon capturé(s)
    </li>
    ```

***

## Étape 7 : Calculer le total des Pokémon capturés avec `computed`

**Objectif :** Calculer et afficher le total des Pokémon capturés.

1.  **Utiliser `computed` pour calculer le total**\
    Ajoutez une propriété calculée qui retourne la somme des captures.

    ```javascript
    const totalPokemons = computed(() => {
      return capturesTab.value.reduce((total, capture) => total + capture, 0);
    });
    ```
2.  **Afficher le total dans le HTML**\
    Affichez dynamiquement le total des Pokémon capturés.

    ```html
    <p>Total des Pokémon capturés : {{ totalPokemons }}</p>
    ```

***

## Étape 8 : Persister les données avec `localStorage`

**Objectif :** Sauvegarder les captures dans `localStorage` pour les récupérer après un rechargement.

1.  **Sauvegarder dans `localStorage` lors de la sauvegarde**\
    Ajoutez la persistance dans `localStorage` à chaque sauvegarde.

    ```javascript
    function sauver() {
      if (compteur.value > 0) {
        capturesTab.value.push(compteur.value);
        localStorage.setItem('captures', JSON.stringify(capturesTab.value));
        compteur.value = 0;
      }
    }
    ```
2.  **Charger les données depuis `localStorage` au chargement**\
    Utilisez `onMounted` pour récupérer les données stockées au chargement de la page.

    ```javascript
    onMounted(() => {
      const savedCaptures = JSON.parse(localStorage.getItem('captures'));
      if (savedCaptures) capturesTab.value = savedCaptures;
    });
    ```

***

## Étape 9 : Utiliser `v-model` pour un champ de saisie

**Objectif :** Permettre aux utilisateurs d'entrer manuellement le nombre de Pokémon capturés.

1.  **Ajouter un champ de saisie avec `v-model`**\
    Utilisez `v-model` pour lier la valeur du champ de saisie au compteur.

    ```html
    <input v-model.number="compteur" type="number" />
    ```
2.  **Valider l'entrée**\
    Le bouton "Sauver" ne sera activé que si la saisie est correcte.

    ```html
    <button @click="sauver" :disabled="isNaN(compteur) || compteur < 1">Sauver 💾</button>
    <p v-if="isNaN(compteur) || compteur < 1" class="error">
      Veuillez entrer un nombre valide supérieur à 0.
    </p>
    ```

***

## Étape 10 : Utilisation de `localStorage` et `onMounted` pour persister les données

**Objectif :** Sauvegarder les captures dans le navigateur et récupérer les données à chaque chargement.

1. **Persister les données avec `localStorage`**\
   Sauvegardez chaque capture dans `localStorage` avec `setItem`.
2. **Récupérer les captures lors du chargement**\
   Utilisez `onMounted` pour charger les données.

***

## Étape 11 : Utiliser les **watchers** et le **class binding**

**Objectif :** Utiliser un `watcher` pour changer la couleur du bouton "Capturer" lorsque le compteur dépasse 5.

1.  **Utiliser un `watch` pour surveiller le compteur**\
    Ajoutez un `watcher` pour observer le compteur et activer une classe CSS conditionnellement.

    ```javascript
    watch(compteur, (newVal) => {
      ilFautSauvegader.value = newVal > 5;
    });
    ```
2.  **Ajouter une classe dynamique**\
    Modifiez la classe du bouton en fonction de la valeur du compteur.

    ```html
    <button @click="capturer" :class="{ chaud: ilFautSauvegader }">
      Capturer 🐢
    </button>
    ```

    Ajoutez un style CSS pour la classe `chaud` :

    ```css
    button.chaud {
      background: #e74c3c; /* Rouge */
    }
    ```

***

## Étape 12 : Confirmation sur clic avec `@click.prevent`

**Objectif :** Ajouter une confirmation avant de naviguer vers une nouvelle page.

1. **Empêcher la navigation automatique et ajouter une confirmation**\
   Utilisez `@click.prevent` pour intercepter le

clic sur un lien et demander confirmation.

```html
<a href="https://www.pokemon.com/fr/pokedex" @click.prevent="verifierAvantDeQuitter">
  Ouvrir le Pokédex
</a>
```

2.  **Ajouter la fonction de confirmation**\
    Utilisez `confirm()` pour demander confirmation avant de naviguer.

    ```javascript
    function verifierAvantDeQuitter(event) {
      const confirmation = confirm("Avez-vous bien sauvegardé vos captures ?");
      if (confirmation) {
        window.location.href = event.target.href;
      }
    }
    ```

***

## Étape 13 : Valider la saisie avec la touche **Entrée**

**Objectif :** Sauvegarder les Pokémon capturés en appuyant sur la touche **Entrée**.

1.  **Écouter la touche Entrée avec `@keyup.enter`**\
    Ajoutez un écouteur pour la touche **Entrée** sur le champ de saisie.

    ```html
    <input v-model.number="compteur" type="number" @keyup.enter="sauver" />
    ```

***

## Étape 14 : Utiliser `ref` pour redonner le focus après sauvegarde

**Objectif :** Redonner le focus à l'input après chaque sauvegarde.

1.  **Ajouter `ref` à l'input**\
    Utilisez `ref` pour cibler l'input.

    ```html
    <input v-model.number="compteur" ref="inputCapture" type="number" />
    ```
2.  **Redonner le focus après la sauvegarde**\
    Utilisez `refs.inputCapture.focus()` après chaque sauvegarde pour redonner le focus à l'input.

    ```javascript
    function sauver() {
      if (!isNaN(compteur.value) && compteur.value > 0) {
        capturesTab.value.push(compteur.value);
        compteur.value = 0;
        refs.inputCapture.focus();
      }
    }
    ```

