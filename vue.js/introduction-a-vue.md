# Introduction à Vue

***

### Étape 1 : Initialisation de Vue.js

#### Objectif :

Initialiser une première application Vue.js et afficher un message réactif à l'utilisateur.

#### Ce que vous allez apprendre :

* **Comment inclure Vue.js via un CDN.**
* **Créer une instance Vue.**
* **Utiliser la syntaxe d'interpolation `{{}}` pour afficher des données dynamiques.**

#### Instructions :

1.  **Inclure Vue.js via CDN** : Vue.js peut être facilement inclus dans votre projet en utilisant une URL CDN. Cela permet de commencer rapidement sans configuration complexe.

    Dans le fichier `index.html`, ajoutez ce script dans la balise `<head>` ou juste avant la fin de la balise `<body>` :

    ```html
    <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
    ```
2.  **Créer une instance Vue** : Dans le fichier `script.js`, initialisez Vue.js et liez-le à l'élément avec l'ID `poke-app`. Cette instance Vue gérera le contenu dynamique de votre application.

    ```javascript
    const { createApp } = Vue;

    createApp({
      setup() {
        const message = "Bienvenue dans PokeCount!"; // Donnée réactive
        return { message }; // Expose 'message' au template HTML
      }
    }).mount("#poke-app");
    ```
3.  **Utiliser l'interpolation dans le HTML** : Utilisez la syntaxe `{{ message }}` dans le fichier HTML pour afficher le message d'accueil de façon réactive.

    ```html
    <h1>{{ message }}</h1>
    ```

#### Résultat attendu :

Vous devriez voir le message "Bienvenue dans PokeCount!" apparaître dans l'élément `<h1>`. Ce message est maintenant réactif et pourra être modifié dynamiquement par Vue.js.

#### Documentation officielle :

* [Vue.js - Démarrage rapide](https://vuejs.org/guide/quick-start.html)
* [Vue.js - Création d'une instance](https://vuejs.org/guide/essentials/application.html)

***

### Étape 2 : Introduction à la réactivité avec `ref`

#### Objectif :

Apprendre à rendre des données réactives avec `ref()` et à gérer les changements de données dans Vue.js.

#### Ce que vous allez apprendre :

* **Utiliser `ref()` pour rendre une donnée réactive.**
* **Créer des méthodes pour manipuler des données réactives.**
* **Comprendre comment Vue.js met à jour le DOM automatiquement en fonction des changements des données.**

#### Instructions :

1.  **Utiliser `ref()` pour rendre une donnée réactive** : Dans Vue.js, vous pouvez rendre n'importe quelle donnée réactive en utilisant `ref()`. Cela crée une référence réactive, et toute modification de cette donnée entraînera une mise à jour automatique de l'interface utilisateur.

    Ajoutez un compteur pour capturer des Pokémon et le rendre réactif :

    ```javascript
    const compteur = ref(0); // Crée une donnée réactive 'compteur' initialisée à 0
    ```
2.  **Manipuler les données réactives avec des méthodes** : Créez une méthode pour capturer des Pokémon, en incrémentant le compteur à chaque capture.

    ```javascript
    function capturer() {
      compteur.value += 1; // Incrémentation du compteur
    }
    ```
3.  **Afficher la valeur du compteur dans le HTML** : Utilisez la syntaxe d'interpolation `{{ compteur }}` dans votre fichier HTML pour afficher la valeur actuelle du compteur.

    ```html
    <p>Pokémons capturés : {{ compteur }}</p>
    ```
4.  **Ajouter un bouton pour capturer des Pokémon** : Utilisez la directive `@click` pour lier l'événement de clic au bouton qui appelle la méthode `capturer`.

    ```html
    <button @click="capturer">Capturer 🐢</button>
    ```

#### Résultat attendu :

* Vous verrez le compteur de Pokémon capturés commencer à 0. Chaque fois que vous cliquerez sur le bouton "Capturer 🐢", le nombre de Pokémon capturés s'incrémentera.

#### Documentation officielle :

* [Vue.js - Données réactives avec `ref`](https://vuejs.org/guide/essentials/reactivity-fundamentals.html#ref)
* [Vue.js - Événements et méthodes](https://vuejs.org/guide/essentials/event-handling.html)

Voici les **étapes 3 et 4** pour la création de la fonction **sauver** et l'affichage des captures dans une liste avec Vue.js. Ces étapes couvrent la gestion des captures et leur affichage dynamique dans l'interface, y compris la gestion des cas où il n'y a pas de captures.

***

### Étape 3 : Création de la fonction `sauver` et gestion du bouton de sauvegarde

#### Objectif :

Ajouter une fonctionnalité pour sauvegarder les captures de Pokémon. Le bouton "Sauver" sera activé uniquement lorsque des captures sont présentes.

#### Ce que vous allez apprendre :

* **Créer une méthode pour sauvegarder les captures dans une liste.**
* **Gérer l'état d'un bouton (désactivé ou activé) en fonction des données.**

#### Instructions :

1.  **Ajouter une liste réactive pour stocker les captures** : Utilisez `ref` pour créer une liste réactive qui stockera les Pokémon capturés.

    ```javascript
    const capturesTab = ref([]); // Tableau réactif pour stocker les captures
    ```
2.  **Créer la fonction `sauver`** : Cette fonction ajoutera la valeur actuelle du compteur à la liste des captures.

    ```javascript
    function sauver() {
      if (compteur.value > 0) { // Sauvegarde uniquement si compteur > 0
        capturesTab.value.push(compteur.value); // Ajoute la capture
        compteur.value = 0; // Réinitialise le compteur
      }
    }
    ```
3.  **Activer ou désactiver le bouton "Sauver"** : Utilisez `v-bind` ou son raccourci `:` pour gérer dynamiquement l'état du bouton "Sauver". Le bouton sera activé uniquement si le compteur est supérieur à 0.

    ```html
    <button @click="sauver" :disabled="compteur === 0">Sauver 💾</button>
    ```

#### Résultat attendu :

* Le bouton "Sauver" est désactivé tant que le compteur est à 0. Lorsqu'il y a des captures, il est activé. Lorsque vous cliquez sur "Sauver", la capture est ajoutée à la liste et le compteur est réinitialisé.

#### Documentation officielle :

* [Vue.js - Gestion des événements](https://vuejs.org/guide/essentials/event-handling.html)
* [Vue.js - Liaison des attributs avec `v-bind`](https://vuejs.org/guide/essentials/template-syntax.html#attribute-bindings)

***

### Étape 4 : Affichage des captures dans une liste et gestion du cas où il n'y a pas de captures

#### Objectif :

Afficher dynamiquement les captures dans une liste HTML. Lorsque la liste est vide, un message indiquant "Aucune capture" sera affiché.

#### Ce que vous allez apprendre :

* **Utiliser `v-for` pour boucler sur une liste et afficher des éléments.**
* **Gérer l'affichage conditionnel avec `v-if` et `v-else`.**

#### Instructions :

1.  **Afficher les captures avec `v-for`** : Utilisez `v-for` pour parcourir la liste des captures et les afficher sous forme de liste (`<ul>`). Chaque élément de la liste aura un identifiant unique pour améliorer la performance (via `:key`).

    ```html
    <ul id="captures">
      <li v-for="(capture, index) in capturesTab" :key="index">
        {{ capture }} Pokémon capturé(s)
      </li>
    </ul>
    ```
2.  **Gérer le cas où il n'y a pas de captures** : Ajoutez un message conditionnel qui sera affiché lorsque la liste des captures est vide. Utilisez `v-if` et `v-else` pour gérer cet affichage conditionnel.

    ```html
    <ul id="captures" v-if="capturesTab.length">
      <li v-for="(capture, index) in capturesTab" :key="index">
        {{ capture }} Pokémon capturé(s)
      </li>
    </ul>
    <p v-else>Aucune capture pour le moment. N'oublie pas de sauvegarder !</p>
    ```
3. **Réinitialiser les captures après la sauvegarde** : Chaque fois que vous sauvegardez, vous pouvez réinitialiser le compteur à 0 pour permettre de nouvelles captures.

#### Résultat attendu :

* Les captures sont affichées dans une liste HTML avec la possibilité de les sauvegarder et de les afficher dynamiquement.
* Si aucune capture n'est présente, un message "Aucune capture pour le moment" est affiché à la place de la liste.

#### Documentation officielle :

* [Vue.js - Boucles avec `v-for`](https://vuejs.org/guide/essentials/list.html)
* [Vue.js - Affichage conditionnel avec `v-if` et `v-else`](https://vuejs.org/guide/essentials/conditional.html)

### Étape 5 : Suppression de toutes les captures

#### Objectif :

Permettre aux utilisateurs de **supprimer toutes les captures directement depuis le bouton**, en mettant directement le code JavaScript dans l'attribut `@click`. Cela montre comment Vue.js permet d'exécuter des instructions JavaScript directement dans le template.

#### Ce que vous allez apprendre :

* **Exécuter directement des instructions JavaScript** dans les attributs Vue.js comme `@click`.
* **Réinitialiser une liste réactive directement à partir du template** sans créer de fonction dédiée.

#### Instructions :

***

#### 1. **Suppression de toutes les captures directement dans le bouton**

1.  **Ajouter un bouton pour réinitialiser toutes les captures** : Vous allez créer un bouton pour permettre aux utilisateurs de supprimer toutes les captures en mettant directement la logique JavaScript dans l'attribut `@click` sans passer par une méthode définie dans `setup`.

    ```html
    <button class="chaud" @click="capturesTab = []" :disabled="capturesTab.length < 1">
      Supprimer toutes les captures 🗑️
    </button>
    ```
2. **Explication du code** :
   * **`@click="capturesTab = []"`** : Ici, Vue.js vous permet d'exécuter directement une instruction JavaScript dans l'attribut `@click`. Lorsque l'utilisateur clique sur le bouton, cela vide simplement la liste réactive `capturesTab` en l'assignant à un tableau vide `[]`.
   * **`:disabled="capturesTab.length < 1"`** : Le bouton est désactivé lorsque la liste `capturesTab` est vide (c'est-à-dire lorsque `capturesTab.length < 1`).

***

#### Résultat attendu :

* Lorsque l'utilisateur clique sur le bouton "Supprimer toutes les captures", toutes les captures sont immédiatement supprimées de la liste.
* Si la liste est déjà vide, le bouton sera désactivé grâce à la directive `:disabled`.

#### Avantage de cette approche :

* **Simplicité** : Pas besoin de créer une fonction séparée dans `setup`. Vue.js vous permet d'utiliser des expressions JavaScript directement dans les directives comme `@click`.
* **Rapidité** : Cela rend le code plus concis pour des actions simples, comme la suppression de toutes les captures ici.

#### Documentation officielle :

* [Vue.js - Événements et gestion directe](https://vuejs.org/guide/essentials/event-handling.html#inline-handlers)

***

#### Exemple de code complet :

```html
<button class="chaud" @click="capturesTab = []" :disabled="capturesTab.length < 1">
  Supprimer toutes les captures 🗑️
</button>
```

Cette approche montre la flexibilité de Vue.js pour exécuter des instructions simples directement depuis le template, sans nécessiter de méthode définie dans `setup`. Vous pouvez utiliser cette méthode pour des actions simples comme vider un tableau ou modifier une variable.



***

### Étape 6 : Suppression des captures avec `@dblclick`

#### Objectif :

Permettre aux utilisateurs de **supprimer une capture spécifique** en double-cliquant sur l'élément dans la liste des captures.

#### Ce que vous allez apprendre :

* **Utiliser l'événement `@dblclick`** pour exécuter une action lorsqu'un élément est double-cliqué.
* **Supprimer un élément d'un tableau réactif** en utilisant `splice()`.

***

#### Instructions :

#### 1. **Ajout de la fonctionnalité `@dblclick` pour supprimer une capture**

1.  **Utiliser `splice()` pour retirer un élément de la liste** : Vue.js permet d'intercepter des événements utilisateurs comme le double-clic avec la directive `@dblclick`. Nous allons utiliser cet événement pour supprimer une capture spécifique dans la liste des captures.

    Ajoutez `@dblclick` directement sur l'élément `<li>` de votre liste. Lorsqu'un élément est double-cliqué, nous utiliserons `splice()` pour supprimer l'élément du tableau.

    ```html
    <ul id="captures" v-if="capturesTab.length">
      <li v-for="(capture, index) in capturesTab" :key="index" @dblclick="capturesTab.splice(index, 1)">
        {{ capture }} Pokémon capturé(s)
      </li>
    </ul>
    ```
2. **Explication du code** :
   * **`@dblclick="capturesTab.splice(index, 1)"`** : Cette ligne intercepte l'événement de double-clic sur un élément `<li>`. Elle utilise `splice()` pour supprimer l'élément correspondant à l'index `index` dans le tableau réactif `capturesTab`.
     * **`index`** est fourni par `v-for`, ce qui permet de localiser l'élément à supprimer dans le tableau.
3.  **Affichage conditionnel avec `v-if` et `v-else`** : Assurez-vous que le tableau `capturesTab` est affiché uniquement lorsqu'il contient des éléments. Si la liste est vide, un message est affiché.

    ```html
    <ul id="captures" v-if="capturesTab.length">
      <li v-for="(capture, index) in capturesTab" :key="index" @dblclick="capturesTab.splice(index, 1)">
        {{ capture }} Pokémon capturé(s)
      </li>
    </ul>
    <p v-else>Aucune capture pour le moment. N'oublie pas de sauvegarder !</p>
    ```

***

#### Résultat attendu :

* Lorsque l'utilisateur double-clique sur un élément de la liste, celui-ci est supprimé.
* Si toutes les captures sont supprimées, le message "Aucune capture pour le moment" sera affiché.

#### Documentation officielle :

* [Vue.js - Gestion des événements](https://vuejs.org/guide/essentials/event-handling.html#inline-handlers)
* [Vue.js - Boucles avec `v-for`](https://vuejs.org/guide/essentials/list.html)

***

#### Exemple de code complet :

```html
<ul id="captures" v-if="capturesTab.length">
  <li v-for="(capture, index) in capturesTab" :key="index" @dblclick="capturesTab.splice(index, 1)">
    {{ capture }} Pokémon capturé(s)
  </li>
</ul>
<p v-else>Aucune capture pour le moment. N'oublie pas de sauvegarder !</p>
```

***

#### Conclusion :

Cette étape ajoute la fonctionnalité permettant de **supprimer une capture spécifique** avec un simple double-clic sur un élément de la liste. Vous avez appris à utiliser l'événement `@dblclick` dans Vue.js pour manipuler directement un tableau réactif.

### Étape 7 : Calculer des valeurs avec `computed` et ajouter le total de Pokémon capturés

#### Objectif :

Ajouter une **propriété calculée** (`computed`) pour afficher le **total des Pokémon capturés** dynamiquement. Vue.js propose une méthode efficace pour gérer les calculs à partir des données réactives, qui ne sont recalculés que lorsque les données sous-jacentes changent.

#### Ce que vous allez apprendre :

* **Utiliser `computed`** pour créer des propriétés dérivées.
* **Calculer des valeurs dynamiques** (comme le total des Pokémon capturés) à partir d'un tableau réactif.

***

#### Instructions :

#### 1. **Introduction à `computed`**

* Dans Vue.js, les propriétés `computed` sont des **propriétés dérivées** des données réactives. Elles sont **cachées** aux performances car elles ne sont recalculées que lorsque leurs dépendances changent.
* Nous allons utiliser `computed` pour calculer dynamiquement le **total des Pokémon capturés** en additionnant les valeurs présentes dans `capturesTab`.

***

#### 2. **Ajouter la propriété `totalPokemons` avec `computed`**

1.  **Définir `totalPokemons`** dans la fonction `setup` : Utilisez `computed` pour créer une propriété réactive qui calcule le total des Pokémon capturés. Cette propriété sera mise à jour automatiquement à chaque modification de `capturesTab`.

    ```javascript
    const totalPokemons = computed(() => {
      return capturesTab.value.reduce((total, capture) => total + capture, 0);
    });
    ```

    * **`capturesTab.value.reduce(...)`** : Cette méthode additionne tous les éléments du tableau `capturesTab` pour obtenir le total.
    * **`computed(...)`** : Vue.js ne recalculera `totalPokemons` que lorsque `capturesTab` sera modifié.
2.  **Afficher `totalPokemons` dans le HTML** : Affichez dynamiquement le total des Pokémon capturés en utilisant `{{ totalPokemons }}` dans votre template HTML.

    ```html
    <p class="total">Pokémons sauvegardés : {{ totalPokemons }}</p>
    ```

***

#### 3. **Explication des étapes**

* **`computed` est utile** lorsque vous devez dériver des données à partir d'autres données réactives. Il permet de créer des propriétés qui sont automatiquement mises à jour lorsque leurs dépendances changent.
* **`totalPokemons`** calcule la somme des captures dans `capturesTab`, et le résultat est affiché dans l'interface utilisateur à l'aide de la syntaxe `{{ totalPokemons }}`.

***

#### Résultat attendu :

* Chaque fois que l'utilisateur sauvegarde une capture, le total des Pokémon capturés s'affiche et se met à jour dynamiquement.
* Si l'utilisateur supprime une capture ou réinitialise la liste, le total est recalculé automatiquement.

***

#### Documentation officielle :

* [Vue.js - Propriétés calculées `computed`](https://vuejs.org/guide/essentials/computed.html)

***

#### Exemple de code complet :

**Dans le fichier `script.js` :**

```javascript
const { createApp, ref, computed } = Vue;

createApp({
  setup() {
    const compteur = ref(0);
    const capturesTab = ref([]);

    function capturer() {
      compteur.value += 1;
    }

    function sauver() {
      capturesTab.value.push(compteur.value);
      compteur.value = 0;
    }

    const totalPokemons = computed(() => {
      return capturesTab.value.reduce((total, capture) => total + capture, 0);
    });

    return { compteur, capturesTab, capturer, sauver, totalPokemons };
  }
}).mount("#poke-app");
```

**Dans le fichier `index.html` :**

```html
<p class="total">Pokémons sauvegardés : {{ totalPokemons }}</p>
```

***

#### Conclusion :

Avec cette étape, vous avez appris à utiliser **`computed`** pour dériver dynamiquement des valeurs à partir des données réactives. Le **total des Pokémon capturés** est désormais automatiquement mis à jour lorsque de nouvelles captures sont ajoutées ou supprimées.

### Étape 8 : Utilisation de `v-if` et `v-show` dans le bouton "Capturer"

#### Objectif :

Ajouter un message d'avertissement **directement dans le bouton "Capturer"** à l'aide de **`v-show`** pour indiquer que l'utilisateur doit sauvegarder les Pokémon capturés lorsque le compteur dépasse 5. Vous allez également apprendre à utiliser **`v-if`** pour conditionner l'affichage d'éléments dans le DOM en fonction d'une condition.

#### Ce que vous allez apprendre :

* **Différences entre `v-if` et `v-show`**.
* **Utiliser `v-show`** pour afficher un message dans le bouton **sans retirer l'élément du DOM**.
* **Utiliser `v-if`** pour afficher conditionnellement des éléments **en les ajoutant ou retirant du DOM**.

***

#### Instructions :

#### 1. **Utilisation de `v-show` pour afficher un message dans le bouton "Capturer"**

1.  **Ajouter un message d'avertissement "Faut sauvegarder !"** : Vous allez afficher un message d'avertissement **dans le bouton de capture** lorsqu'il est nécessaire de sauvegarder (i.e. lorsque le compteur dépasse 5). Ce message apparaîtra sans retirer l'élément du DOM grâce à la directive `v-show`.

    **Dans le fichier `index.html`, modifiez le bouton "Capturer" :**

    ```html
    <button @click="capturer" :class="{ chaud: ilFautSauvegader }">
      Capturer 🐢
      <!-- Affiche le message d'avertissement lorsque le compteur dépasse 5 -->
      <div class="note" v-show="compteur > 5">Faut sauvegarder !</div>
    </button>
    ```

    * **`@click="capturer"`** : Lorsque l'utilisateur clique sur ce bouton, la fonction `capturer` est exécutée et le compteur de Pokémon capturés est incrémenté.
    * **`v-show="compteur > 5"`** : Ce div contenant le message "Faut sauvegarder !" sera visible seulement si la valeur du **compteur dépasse 5**. L'élément reste dans le DOM même lorsqu'il est caché.

***

#### 2. **Utilisation de `v-if` pour afficher un message conditionnel**

1.  **Ajouter un message conditionnel "T'es un vrai chasseur" avec `v-if`** : Utilisez `v-if` pour afficher un message lorsque le total des Pokémon capturés dépasse 9. Cette directive va **insérer ou retirer complètement l'élément du DOM**.

    **Ajoutez le message après l'élément total dans `index.html` :**

    ```html
    <p v-if="totalPokemons > 9" class="chasseur">
      🏆 T'es un vrai chasseur ! 🏆
    </p>
    ```

    * **`v-if="totalPokemons > 9"`** : Ce paragraphe sera ajouté au DOM seulement si la valeur de `totalPokemons` dépasse 9. Si cette condition est fausse, l'élément est totalement retiré du DOM.

***

#### 3. **Mise à jour de la logique dans le fichier `script.js`**

Dans le fichier **`script.js`**, assurez-vous que le compteur et le total des Pokémon capturés sont bien définis dans `setup`. Vous devez avoir :

* **Un compteur réactif** pour capturer des Pokémon.
* **Une propriété calculée (`computed`)** pour calculer le total des Pokémon capturés à partir de la liste des captures.

Voici un exemple complet du fichier **`script.js`** mis à jour :

```javascript
const { createApp, ref, computed } = Vue;

createApp({
  setup() {
    const compteur = ref(0); // Compteur pour les captures
    const capturesTab = ref([]); // Tableau pour stocker les captures

    // Fonction pour capturer un Pokémon
    function capturer() {
      compteur.value += 1;
    }

    // Fonction pour sauvegarder les captures
    function sauver() {
      capturesTab.value.push(compteur.value); // Ajoute la capture au tableau
      compteur.value = 0; // Réinitialise le compteur
    }

    // Calcul du total des Pokémon capturés
    const totalPokemons = computed(() => {
      return capturesTab.value.reduce((total, capture) => total + capture, 0);
    });

    return { compteur, capturesTab, capturer, sauver, totalPokemons };
  }
}).mount("#poke-app");
```

***

#### 4. **Ajout du HTML dans le fichier `index.html`**

Le fichier **`index.html`** doit inclure les éléments suivants :

* Le bouton **"Capturer"** avec le message d'avertissement "Faut sauvegarder !", visible si le compteur dépasse 5.
* Le message **"T'es un vrai chasseur"**, visible seulement lorsque le total des Pokémon capturés dépasse 9.

Voici un extrait complet de l'HTML avec les éléments de l'étape 8 :

```html
<button @click="capturer" :class="{ chaud: ilFautSauvegader }">
  Capturer 🐢
  <!-- Affiche "Faut sauvegarder" lorsque le compteur dépasse 5 -->
  <div class="note" v-show="compteur > 5">Faut sauvegarder !</div>
</button>

<p v-if="totalPokemons > 9" class="chasseur">
  🏆 T'es un vrai chasseur ! 🏆
</p>
```

***

#### 5. **Différences entre `v-if` et `v-show`**

* **`v-if`** : L'élément est **ajouté ou retiré du DOM** selon la condition. C'est idéal pour des éléments qui changent rarement d'état, car Vue.js doit recréer ou détruire l'élément chaque fois que la condition change.
* **`v-show`** : L'élément reste toujours dans le DOM, mais son affichage est contrôlé par `display: none;`. Utilisez `v-show` pour des éléments qui changent fréquemment d'état (comme dans le cas du message d'avertissement "Faut sauvegarder !").

***

#### Résultat attendu :

* Le message "Faut sauvegarder !" s'affiche **dans le bouton "Capturer"** lorsque le compteur dépasse 5, mais il est toujours présent dans le DOM.
* Le message "T'es un vrai chasseur !" est **ajouté ou retiré du DOM** selon que le total des Pokémon capturés dépasse 9.

***

#### Documentation officielle :

* [Vue.js - Affichage conditionnel avec `v-if` et `v-show`](https://vuejs.org/guide/essentials/conditional.html)

***

#### Conclusion :

Vous avez maintenant intégré **`v-if` et `v-show`** dans votre projet pour afficher dynamiquement des messages en fonction de conditions. Vous avez appris à utiliser **`v-show`** pour afficher un message d'avertissement dans un bouton sans le retirer du DOM, et **`v-if`** pour conditionner l'affichage en fonction du total des Pokémon capturés.

### Étape 9 : Ajout d'un champ de saisie avec `v-model` et validation des entrées

#### Objectif :

Ajouter un **champ de saisie** pour permettre aux utilisateurs d'entrer manuellement le nombre de Pokémon capturés. Utilisez **`v-model`** pour lier les données réactives à un élément `<input>` et ajouter des validations pour s'assurer que l'utilisateur entre un nombre valide.

#### Ce que vous allez apprendre :

* **Utiliser `v-model`** pour créer une liaison bidirectionnelle entre un champ de saisie et des données réactives.
* **Effectuer des validations simples** pour vérifier que l'utilisateur entre bien un nombre valide (non `NaN` et supérieur à 0).

***

#### Instructions :

#### 1. **Utilisation de `v-model` pour lier un champ de saisie au compteur**

**1.1. Ajouter un champ de saisie et un label dans la div `.captures`**

Vous allez placer le champ de saisie et le label **directement dans la div `.captures`**. Ce champ permettra à l'utilisateur d'entrer le nombre de Pokémon capturés manuellement, et la valeur saisie sera liée réactivement à la donnée `compteur`.

**Ajoutez le champ de saisie dans `index.html` à l'intérieur de la div `.captures` :**

```html
<div class="captures">
  <label for="compteur">Saisir le nombre de Pokémon capturés :</label>
  <input id="compteur" v-model.number="compteur" type="number" />
</div>
```

* **`v-model.number="compteur"`** : Cette directive crée une **liaison bidirectionnelle** entre l'élément `<input>` et la donnée réactive `compteur`. La valeur saisie sera automatiquement convertie en nombre grâce au modificateur `.number`.
* **`type="number"`** : Cela permet de limiter l'entrée utilisateur aux nombres uniquement.

***

#### 2. **Présentation de `v-model`**

* **`v-model`** : Vue.js crée une **liaison bidirectionnelle** entre l'élément de formulaire et la variable réactive. Ainsi, toute modification dans le champ mettra à jour `compteur`, et vice versa.
* **`v-model.number`** : Le modificateur `.number` convertit automatiquement la saisie en nombre. Cela garantit que la valeur est bien un nombre dans `compteur`.

***

#### 3. **Ajouter des validations sur l'entrée utilisateur**

Vous allez maintenant tester que l'utilisateur a bien entré un **nombre valide**. Le bouton "Sauver" ne sera activé que si la saisie est correcte (non `NaN` et supérieure à 0). De plus, si la saisie est invalide, un message d'erreur apparaîtra.

**3.1. Modifier le bouton "Sauver" pour valider l'entrée utilisateur**

Vous allez utiliser **`v-bind`** pour désactiver le bouton "Sauver" si la saisie est soit **NaN**, soit inférieure à 1. Testez d'abord si la valeur est un nombre valide avec **`isNaN`**, puis vérifiez si la valeur est supérieure à 0 avec un **OU** (`||`).

**Ajoutez cette condition dans `index.html` pour le bouton "Sauver" :**

```html
<button @click="sauver" :disabled="isNaN(compteur) || compteur < 1">
  Sauver 💾
</button>
```

* **`isNaN(compteur)`** : Cette condition vérifie que la valeur saisie est un **nombre valide**.
* **`compteur < 1`** : Vérifie que la valeur est strictement supérieure à 0.
* Si l'une des deux conditions est remplie, le bouton est désactivé.

***

#### 4. **Afficher un message d'erreur si la saisie est invalide**

Si la saisie est incorrecte (non numérique ou inférieure à 1), vous pouvez afficher un **message d'erreur** sous le champ de saisie.

**Ajoutez un message d'erreur sous le champ dans `index.html` :**

```html
<p v-if="isNaN(compteur) || compteur < 1" class="error">
  Veuillez entrer un nombre valide supérieur à 0.
</p>
```

* **`v-if="isNaN(compteur) || compteur < 1"`** : Affiche le message d'erreur si la saisie est non numérique ou inférieure à 1.

***

#### 5. **Mise à jour du fichier `script.js` pour la gestion de la saisie**

Voici la logique à intégrer dans le fichier **`script.js`** pour gérer la saisie et la validation du compteur. La fonction `sauver` ne permettra de sauvegarder que si la saisie est valide.

**Dans le fichier `script.js` :**

```javascript
const { createApp, ref } = Vue;

createApp({
  setup() {
    const compteur = ref(0); // Compteur réactif pour les captures
    const capturesTab = ref([]); // Tableau pour stocker les captures

    // Fonction pour capturer un Pokémon
    function capturer() {
      compteur.value += 1;
    }

    // Fonction pour sauvegarder les captures
    function sauver() {
      if (!isNaN(compteur.value) && compteur.value > 0) {
        capturesTab.value.push(compteur.value); // Ajoute la capture au tableau
        compteur.value = 0; // Réinitialise le compteur
      }
    }

    return { compteur, capturesTab, capturer, sauver };
  }
}).mount("#poke-app");
```

***

#### 6. **Ajout complet du HTML dans le fichier `index.html`**

Vous allez ajouter les éléments suivants :

* Le champ de saisie avec un label.
* Un message d'erreur sous le champ.
* Le bouton "Sauver" désactivé en cas de saisie invalide.

**Voici le code complet à ajouter dans `index.html` pour cette étape :**

```html
<div class="captures">
  <label for="compteur">Saisir le nombre de Pokémon capturés :</label>
  <input id="compteur" v-model.number="compteur" type="number" />
  
  <!-- Affichage d'un message d'erreur si la saisie est invalide -->
  <p v-if="isNaN(compteur) || compteur < 1" class="error">
    Veuillez entrer un nombre valide supérieur à 0.
  </p>
  
  <button @click="sauver" :disabled="isNaN(compteur) || compteur < 1">
    Sauver 💾
  </button>
</div>
```

***

#### Résultat attendu :

* **Champ de saisie** : L'utilisateur peut entrer manuellement un nombre dans le champ.
* **Validation** : Le bouton "Sauver" est désactivé si la saisie est incorrecte (non numérique ou inférieure à 1).
* **Message d'erreur** : Si la saisie est incorrecte, un message d'erreur s'affiche sous le champ de saisie.

***

#### Documentation officielle :

* [Vue.js - Liaison bidirectionnelle avec `v-model`](https://vuejs.org/guide/essentials/forms.html)
* [Vue.js - Syntaxe de template](https://vuejs.org/guide/essentials/template-syntax.html)

***

#### Conclusion :

Dans cette étape, vous avez appris à utiliser **`v-model`** pour lier un champ de saisie à des données réactives et à effectuer des validations simples sur les entrées utilisateur. Vous avez également ajouté un message d'erreur et désactivé le bouton "Sauver" lorsque la saisie est invalide.

### Étape 10 : Utiliser `localStorage` et `onMounted` pour persister les données et introduction au cycle de vie de Vue.js

#### Objectif :

Permettre de **sauvegarder les captures dans le navigateur** grâce à **`localStorage`** et **récupérer les données sauvegardées** lors du chargement de l'application à l'aide du hook de cycle de vie **`onMounted`**. Vous allez également découvrir le cycle de vie d'une application Vue.js.

#### Ce que vous allez apprendre :

* **Utiliser `localStorage`** pour persister des données entre les sessions de l'utilisateur.
* **Introduction aux hooks du cycle de vie** dans Vue.js, avec un focus sur **`onMounted`** pour récupérer des données lors du chargement de l'application.
* Comprendre les étapes du **cycle de vie d'une application Vue.js**.

***

#### Instructions :

#### 1. **Utilisation de `localStorage` pour persister les captures**

Le **`localStorage`** permet de stocker des données directement dans le navigateur, de manière persistante. Cela signifie que même après un rechargement de la page ou la fermeture du navigateur, les données restent disponibles.

***

**1.1. Ajouter la persistance des captures avec `localStorage` dans la fonction `sauver`**

Lorsque vous sauvegardez des Pokémon capturés, vous pouvez ajouter les données dans **`localStorage`** pour qu'elles soient disponibles lors de la prochaine session.

Modifiez la fonction `sauver` dans **`script.js`** pour y inclure la logique de sauvegarde dans `localStorage` :

```javascript
function sauver() {
  if (!isNaN(compteur.value) && compteur.value > 0) {
    capturesTab.value.push(compteur.value); // Ajoute la capture au tableau
    localStorage.setItem('captures', JSON.stringify(capturesTab.value)); // Sauvegarde dans localStorage
    compteur.value = 0; // Réinitialise le compteur
  }
}
```

* **`localStorage.setItem()`** : Cette méthode permet de sauvegarder des données dans le navigateur. Ici, nous convertissons le tableau des captures en chaîne JSON avec `JSON.stringify` avant de le stocker.

***

#### 2. **Récupérer les données avec `onMounted`**

Pour récupérer les captures stockées dans le **`localStorage`** lors du chargement de l'application, nous utiliserons le hook de cycle de vie **`onMounted`**. Ce hook est exécuté une fois que le composant Vue.js est monté dans le DOM.

**2.1. Utilisation de `onMounted` pour récupérer les données stockées**

Dans **`script.js`**, ajoutez le hook **`onMounted`** pour vérifier si des données sont déjà présentes dans le `localStorage` et les charger dans l'application.

```javascript
onMounted(() => {
  const savedCaptures = JSON.parse(localStorage.getItem('captures')); // Récupère les captures depuis localStorage
  if (savedCaptures) {
    capturesTab.value = savedCaptures; // Si des captures existent, les charge dans le tableau réactif
  }
});
```

* **`onMounted()`** : Ce hook est exécuté après que le composant est monté et que le DOM est prêt. Ici, il est utilisé pour récupérer les captures stockées dans `localStorage`.

***

#### 3. **Présentation du cycle de vie de Vue.js**

Les composants Vue.js suivent un **cycle de vie** en plusieurs étapes. Le cycle de vie fait référence aux différentes phases par lesquelles passe un composant Vue, depuis sa création jusqu'à sa destruction.

**Principaux hooks du cycle de vie :**

* **`onMounted`** : S'exécute une fois que le composant est monté dans le DOM.
* **`onBeforeUnmount`** : S'exécute juste avant que le composant ne soit détruit.
* **`onUpdated`** : S'exécute après une mise à jour du DOM.

**Schéma du cycle de vie d'une application Vue.js :**

![Schéma du cycle de vie Vue.js](https://vuejs.org/assets/lifecycle.16e4c08e.png)

[Vue.js - Documentation sur le cycle de vie](https://vuejs.org/guide/essentials/lifecycle.html)

***

#### 4. **Mise à jour complète du fichier `script.js`**

Voici le fichier **`script.js`** mis à jour avec la gestion de **`localStorage`** et l'utilisation de **`onMounted`** :

```javascript
const { createApp, ref, computed, onMounted } = Vue;

createApp({
  setup() {
    const compteur = ref(0); // Compteur réactif
    const capturesTab = ref([]); // Tableau pour stocker les captures

    // Fonction pour capturer un Pokémon
    function capturer() {
      compteur.value += 1;
    }

    // Fonction pour sauvegarder les captures
    function sauver() {
      if (!isNaN(compteur.value) && compteur.value > 0) {
        capturesTab.value.push(compteur.value); // Ajoute la capture au tableau
        localStorage.setItem('captures', JSON.stringify(capturesTab.value)); // Sauvegarde dans localStorage
        compteur.value = 0; // Réinitialise le compteur
      }
    }

    // Récupérer les données depuis localStorage lorsque le composant est monté
    onMounted(() => {
      const savedCaptures = JSON.parse(localStorage.getItem('captures')); // Récupère les captures depuis localStorage
      if (savedCaptures) {
        capturesTab.value = savedCaptures; // Si des captures existent, les charge dans le tableau réactif
      }
    });

    return { compteur, capturesTab, capturer, sauver };
  }
}).mount("#poke-app");
```

***

#### Résultat attendu :

* Lorsque l'utilisateur capture des Pokémon, ils sont **sauvegardés dans le `localStorage`**.
* Lorsqu'il recharge la page, les captures sauvegardées sont automatiquement récupérées et affichées.
* Le cycle de vie de Vue.js, avec le hook **`onMounted`**, est utilisé pour charger les données après le montage du composant.

***

#### Documentation officielle :

* [Vue.js - `onMounted`](https://vuejs.org/guide/essentials/lifecycle.html#lifecycle-hooks)
* [Vue.js - Cycle de vie d'un composant](https://vuejs.org/guide/essentials/lifecycle.html)

***

#### Conclusion :

Dans cette étape, vous avez appris à **persister des données avec `localStorage`** et à les récupérer lors du **montage du composant** grâce au hook **`onMounted`**. Vous avez également été introduit au **cycle de vie** d'un composant Vue.js, qui comprend plusieurs phases importantes, comme la **montée** et la **mise à jour**.

### Étape 11 : Utilisation des **watchers** et du **class binding** pour afficher dynamiquement le bouton "Capturer" en rouge

#### Objectif :

Vous allez apprendre à utiliser un **watcher** pour observer les changements du compteur et activer une **classe conditionnelle** pour changer la couleur du bouton "Capturer" en rouge lorsque l'utilisateur doit sauvegarder (c'est-à-dire lorsque le compteur dépasse une certaine valeur, par exemple 5).

#### Ce que vous allez apprendre :

* **Utiliser les watchers (`watch`)** pour observer les changements de données réactives et exécuter du code en conséquence.
* **Appliquer des classes dynamiques** à un élément à l'aide du **class binding** (`:class`) pour changer l'apparence du bouton "Capturer" en fonction de la valeur du compteur.

***

#### Instructions :

#### 1. **Ajouter un watcher pour observer le compteur**

Les **watchers** permettent d'observer une donnée réactive et d'exécuter du code lorsque cette donnée change. Nous allons utiliser un watcher pour surveiller le **compteur** et activer une variable `ilFautSauvegader` lorsque le compteur dépasse 5.

**1.1. Ajouter un watcher dans `script.js`**

Dans **`script.js`**, ajoutez un **watcher** pour observer la valeur du **compteur** :

```javascript
watch(compteur, (newVal) => {
  if (newVal > 5) {
    ilFautSauvegader.value = true; // Active l'indicateur de sauvegarde
  } else {
    ilFautSauvegader.value = false; // Désactive l'indicateur de sauvegarde
  }
});
```

* **`watch(compteur, (newVal) => ...)`** : Ce watcher surveille les changements du **compteur**. Si le compteur dépasse 5, il met à jour la variable `ilFautSauvegader` à `true`, sinon à `false`.

***

#### 2. **Utiliser `:class` pour appliquer une classe conditionnelle au bouton "Capturer"**

Nous allons maintenant lier dynamiquement une **classe CSS** au bouton "Capturer" pour qu'il devienne rouge lorsque l'utilisateur doit sauvegarder ses captures (c'est-à-dire lorsque `ilFautSauvegader` est activé).

**2.1. Modifier le bouton "Capturer" dans `index.html` pour appliquer la classe conditionnelle**

Dans **`index.html`**, utilisez **`v-bind:class`** (ou son raccourci `:class`) pour appliquer la classe **`chaud`** lorsque la variable `ilFautSauvegader` est `true`.

```html
<button @click="capturer" :class="{ chaud: ilFautSauvegader }">
  Capturer 🐢
  <div class="note" v-show="compteur > 5">Faut sauvegarder !</div>
</button>
```

* **`:class="{ chaud: ilFautSauvegader }`** : Cette expression applique la classe **`chaud`** (qui rend le bouton rouge) lorsque `ilFautSauvegader` est vrai.

***

#### 3. **Mettre à jour le fichier `script.js`**

Voici le fichier **`script.js`** avec le watcher et la gestion de la classe conditionnelle :

```javascript
const { createApp, ref, computed, watch } = Vue;

createApp({
  setup() {
    const compteur = ref(0); // Compteur réactif
    const capturesTab = ref([]); // Tableau pour stocker les captures
    const ilFautSauvegader = ref(false); // Indicateur si une sauvegarde est nécessaire

    // Fonction pour capturer un Pokémon
    function capturer() {
      compteur.value += 1;
    }

    // Fonction pour sauvegarder les captures
    function sauver() {
      if (!isNaN(compteur.value) && compteur.value > 0) {
        capturesTab.value.push(compteur.value); // Ajoute la capture au tableau
        localStorage.setItem('captures', JSON.stringify(capturesTab.value)); // Sauvegarde dans localStorage
        compteur.value = 0; // Réinitialise le compteur
      }
    }

    // Watcher pour observer les changements du compteur
    watch(compteur, (newVal) => {
      if (newVal > 5) {
        ilFautSauvegader.value = true; // Active l'indicateur de sauvegarde
      } else {
        ilFautSauvegader.value = false; // Désactive l'indicateur de sauvegarde
      }
    });

    return { compteur, capturesTab, capturer, sauver, ilFautSauvegader };
  }
}).mount("#poke-app");
```

***

#### 4. **Mettre à jour le CSS pour la classe "chaud"**

Assurez-vous que la classe **`chaud`** est bien définie dans votre fichier **`style.css`**. Cette classe rendra le bouton rouge pour indiquer que l'utilisateur doit sauvegarder ses captures.

**Dans le fichier `style.css` :**

```css
button.chaud {
  background: #e74c3c; /* Rouge pour indiquer qu'il faut sauvegarder */
}
```

***

#### Résultat attendu :

* Lorsque le **compteur dépasse 5**, le bouton "Capturer" devient **rouge** pour indiquer qu'il faut sauvegarder.
* Le bouton redevient normal si le compteur est réinitialisé à une valeur inférieure ou égale à 5.
* Le message **"Faut sauvegarder !"** s'affiche dans le bouton si le compteur dépasse 5.

***

#### Documentation officielle :

* [Vue.js - `watch`](https://vuejs.org/guide/essentials/watchers.html)
* [Vue.js - `v-bind:class` pour les classes dynamiques](https://vuejs.org/guide/essentials/class-and-style.html#binding-html-classes)

***

#### Conclusion :

Dans cette étape, vous avez appris à utiliser les **watchers** pour observer les changements d'une donnée réactive et exécuter du code en conséquence. Vous avez également vu comment lier dynamiquement une classe à un élément HTML avec **`v-bind:class`** pour modifier l'apparence du bouton en fonction des conditions.

### Étape 12 : Confirmation sur clic du bouton "Ouvrir le Pokédex" avec `@click.prevent` et présentation des modificateurs d'événements

#### Objectif :

Ajouter une **confirmation** lorsque l'utilisateur clique sur le bouton "Ouvrir le Pokédex". Vous allez intercepter l'événement de clic avec **`@click.prevent`** pour empêcher la navigation automatique, demander confirmation à l'utilisateur et gérer la navigation si nécessaire. Vous apprendrez également à utiliser d'autres **modificateurs d'événements** dans Vue.js.

#### Ce que vous allez apprendre :

* **Utiliser `.prevent`** pour empêcher le comportement par défaut d'un lien.
* **Récupérer l'objet `event`** et ses propriétés, comme **`event.target.href`**, pour gérer la navigation.
* **Présentation des modificateurs d'événements** en Vue.js, comme `.stop`, `.prevent`, `.once`, `.self`, etc.

***

#### Instructions :

#### 1. **Utilisation de `@click.prevent` pour bloquer la navigation automatique**

* **`@click.prevent`** : Ce modificateur d'événement empêche le comportement par défaut de l'événement, qui dans le cas d'un lien est la **navigation**. Nous allons l'utiliser pour intercepter le clic sur le lien "Ouvrir le Pokédex" et ajouter une confirmation avant de naviguer.

***

**1.1. Ajouter la confirmation dans `index.html`**

Modifiez le lien "Ouvrir le Pokédex" pour ajouter **`@click.prevent`** et une fonction qui demandera à l'utilisateur de confirmer avant de quitter la page.

**Ajoutez le lien suivant dans `index.html` :**

```html
<a class="button" href="https://www.pokemon.com/fr/pokedex" @click.prevent="verifierAvantDeQuitter">
  Ouvrir le Pokédex
</a>
```

* **`@click.prevent="verifierAvantDeQuitter"`** : Le modificateur **`.prevent`** empêche le lien de naviguer automatiquement vers l'URL. La fonction `verifierAvantDeQuitter` est appelée à la place, et elle gérera la navigation après confirmation.

***

#### 2. **Utilisation de `event.target.href` pour gérer la navigation manuelle**

Dans la fonction `verifierAvantDeQuitter`, nous allons récupérer l'objet **`event`** pour accéder à **`event.target.href`**, qui contient l'URL vers laquelle l'utilisateur souhaite naviguer. Si l'utilisateur confirme, nous naviguerons manuellement vers cette URL.

**2.1. Ajouter la fonction `verifierAvantDeQuitter` dans `script.js`**

Ajoutez la fonction suivante dans **`script.js`** pour gérer la confirmation avant la navigation :

```javascript
function verifierAvantDeQuitter(event) {
  const confirmation = confirm("Avez-vous bien sauvegardé vos captures avant d'ouvrir le Pokédex ?");
  if (confirmation) {
    // Si l'utilisateur confirme, naviguer vers l'URL du lien
    window.location.href = event.target.href;
  }
}
```

* **`event.target.href`** : Cette propriété récupère l'URL associée à l'élément `<a>` sur lequel l'utilisateur a cliqué.
* **`confirm()`** : Affiche une boîte de dialogue pour demander confirmation à l'utilisateur avant de quitter la page.

***

#### 3. **Présentation des autres modificateurs d'événements dans Vue.js**

Vue.js propose plusieurs **modificateurs d'événements** qui permettent de modifier le comportement par défaut d'un événement. Voici les modificateurs les plus courants :

1. **`.prevent`** :
   * Empêche l'action par défaut (par exemple, la navigation pour un lien).
   * Exemple : `@submit.prevent="handleSubmit"`.
2. **`.stop`** :
   * Empêche la propagation de l'événement à d'autres éléments parents.
   * Exemple : `@click.stop="handleClick"`.
3. **`.once`** :
   * Exécute le gestionnaire d'événement une seule fois, puis le désactive.
   * Exemple : `@click.once="handleClick"`.
4. **`.self`** :
   * Ne déclenche l'événement que si l'utilisateur clique exactement sur l'élément, et non sur un descendant.
   * Exemple : `@click.self="handleClick"`.
5. **`.capture`** :
   * Change l'ordre d'exécution de l'événement pour utiliser la phase de capture.
   * Exemple : `@click.capture="handleClick"`.
6. **`.passive`** :
   * Indique que l'écouteur ne va jamais appeler `preventDefault`, ce qui peut améliorer les performances pour les événements de défilement.
   * Exemple : `@scroll.passive="handleScroll"`.

***

#### Exemple de code complet :

**Dans `index.html` :**

```html
<a class="button" href="https://www.pokemon.com/fr/pokedex" @click.prevent="verifierAvantDeQuitter">
  Ouvrir le Pokédex
</a>
```

**Dans `script.js` :**

```javascript
const { createApp, ref } = Vue;

createApp({
  setup() {
    const compteur = ref(0); // Compteur réactif
    const capturesTab = ref([]); // Tableau pour stocker les captures

    // Fonction de capture
    function capturer() {
      compteur.value += 1;
    }

    // Fonction de sauvegarde
    function sauver() {
      capturesTab.value.push(compteur.value);
      compteur.value = 0;
    }

    // Confirmation avant de quitter pour ouvrir le Pokédex
    function verifierAvantDeQuitter(event) {
      const confirmation = confirm("Avez-vous bien sauvegardé vos captures avant d'ouvrir le Pokédex ?");
      if (confirmation) {
        window.location.href = event.target.href;
      }
    }

    return { compteur, capturesTab, capturer, sauver, verifierAvantDeQuitter };
  }
}).mount("#poke-app");
```

***

#### Résultat attendu :

* Lorsque l'utilisateur clique sur **"Ouvrir le Pokédex"**, une **boîte de dialogue de confirmation** s'affiche.
* Si l'utilisateur **confirme**, il est redirigé vers l'URL du Pokédex.
* Si l'utilisateur **annule**, il reste sur la page actuelle.

***

#### Documentation officielle :

* [Vue.js - Modificateurs d'événements](https://vuejs.org/guide/essentials/event-handling.html#event-modifiers)

***

#### Conclusion :

Dans cette étape, vous avez appris à utiliser **`@click.prevent`** pour intercepter la navigation automatique d'un lien et afficher une confirmation avant de naviguer. Vous avez également découvert d'autres modificateurs d'événements utiles dans Vue.js, tels que **`.stop`**, **`.once`**, et **`.self`**, qui permettent de personnaliser le comportement des événements.

Très bien, nous allons donc nous concentrer sur l'écoute de la touche **Entrée** pour valider et sauvegarder la saisie, sans nous occuper de redonner le focus au champ de saisie.

***

### Étape 13 : Écouter la touche **Entrée** sur l'input pour valider la saisie et sauvegarder

#### Objectif :

Ajouter un **écouteur d'événements clavier** sur le champ de saisie pour permettre à l'utilisateur de valider directement la saisie et de sauvegarder la capture en appuyant sur la touche **Entrée**.

#### Ce que vous allez apprendre :

* **Écouter les événements clavier** avec `@keyup.enter`.
* **Réutiliser la méthode `sauver`** pour éviter les redondances dans le code.

***

#### Instructions :

#### 1. **Écouter la touche Entrée avec `@keyup.enter` dans le champ de saisie**

Utilisons l'événement **Entrée** pour permettre à l'utilisateur de **sauvegarder ses captures directement depuis le clavier**. Cela améliore l'expérience utilisateur en rendant l'interface plus fluide.

**Ajoutez l'écoute de la touche Entrée dans la div `.captures` du fichier `index.html` :**

```html
<div class="captures">
  <label for="compteur">Saisir le nombre de Pokémon capturés :</label>
  <input id="compteur" v-model.number="compteur" type="number" @keyup.enter="sauver" />
  
  <!-- Affichage d'un message d'erreur si la saisie est invalide -->
  <p v-if="isNaN(compteur) || compteur < 1" class="error">
    Veuillez entrer un nombre valide supérieur à 0.
  </p>
  
  <button @click="sauver" :disabled="isNaN(compteur) || compteur < 1">
    Sauver 💾
  </button>
</div>
```

* **`@keyup.enter="sauver"`** : Cette directive écoute l'événement **Entrée** sur le champ de saisie. Lorsque l'utilisateur appuie sur la touche Entrée, la méthode `sauver` est appelée automatiquement, sans avoir besoin de cliquer sur le bouton "Sauver".

***

#### 2. **Réutiliser la méthode `sauver` dans `script.js`**

Aucun changement dans la méthode **`sauver`** n'est nécessaire. Voici un rappel de ce qu'elle doit contenir dans **`script.js`** :

```javascript
function sauver() {
  if (!isNaN(compteur.value) && compteur.value > 0) {
    capturesTab.value.push(compteur.value); // Ajoute la capture au tableau
    localStorage.setItem('captures', JSON.stringify(capturesTab.value)); // Sauvegarde dans localStorage
    compteur.value = 0; // Réinitialise le compteur
  }
}
```

* **`compteur.value > 0 && !isNaN(compteur.value)`** : Vérifie que la saisie est un nombre valide avant de l'ajouter à la liste des captures.

***

#### Résultat attendu :

* Lorsque l'utilisateur saisit un nombre dans le champ de saisie et appuie sur **Entrée**, la capture est automatiquement sauvegardée sans avoir besoin de cliquer sur le bouton "Sauver".
* Le comportement est le même que lorsqu'on clique sur le bouton, mais l'expérience utilisateur est améliorée grâce à l'interaction clavier.

***

#### Documentation officielle :

* [Vue.js - Gestion des événements clavier avec `@keyup`](https://vuejs.org/guide/essentials/event-handling.html#keyboard-events)

***

#### Conclusion :

Vous avez maintenant ajouté une fonctionnalité qui permet de **sauvegarder directement la saisie** en appuyant sur la touche **Entrée**, sans avoir besoin de cliquer sur le bouton "Sauver". Cela améliore l'expérience utilisateur en rendant l'interface plus fluide et intuitive.

### Étape 14 : Utiliser `ref` pour cibler l'input et redonner le focus après la sauvegarde

#### Objectif :

Nous allons utiliser la directive Vue.js **`ref`** pour cibler directement l'élément `<input>` dans le DOM. Ensuite, nous mettrons à jour la méthode **`sauver`** pour redonner le **focus** à cet input après avoir sauvegardé la capture. Vous apprendrez comment **`ref`** fonctionne pour référencer des éléments DOM spécifiques dans Vue.js.

#### Ce que vous allez apprendre :

* **Utiliser `ref` pour référencer un élément DOM**.
* **Accéder aux éléments DOM via `ref`** dans une méthode Vue.js.
* **Redonner le focus à un input** après une action (ici, après la sauvegarde).

***

#### Instructions :

#### 1. **Utilisation de `ref` pour cibler l'input**

Dans Vue.js, **`ref`** permet d'obtenir une **référence directe à un élément du DOM** (comme un input, un bouton, etc.). Cela permet d'interagir avec cet élément via JavaScript, comme vous le feriez avec **`document.getElementById()`**, mais de manière plus réactive.

**1.1. Ajouter `ref` à l'input**

Nous allons ajouter **`ref`** sur l'élément `<input>` pour pouvoir y accéder et redonner le focus après la sauvegarde.

**Dans `index.html`, ajoutez `ref="inputCapture"` à l'input dans la div `.captures` :**

```html
<div class="captures">
  <label for="compteur">Saisir le nombre de Pokémon capturés :</label>
  <input id="compteur" v-model.number="compteur" ref="inputCapture" type="number" @keyup.enter="sauver" />
  
  <!-- Affichage d'un message d'erreur si la saisie est invalide -->
  <p v-if="isNaN(compteur) || compteur < 1" class="error">
    Veuillez entrer un nombre valide supérieur à 0.
  </p>
  
  <button @click="sauver" :disabled="isNaN(compteur) || compteur < 1">
    Sauver 💾
  </button>
</div>
```

* **`ref="inputCapture"`** : Ce `ref` crée une référence vers cet élément `<input>` dans le DOM. Nous pourrons ensuite y accéder depuis notre script et lui redonner le focus après la sauvegarde.

***

#### 2. **Explication du fonctionnement de `ref` dans Vue.js**

* **`ref`** est utilisé pour obtenir une **référence directe** à un élément du DOM ou un composant enfant dans Vue.js.
* Lorsque vous ajoutez **`ref="nomDuRef"`** à un élément dans votre template HTML, Vue.js rend cet élément accessible depuis votre script via l'objet `refs`.

**Accès à un élément DOM via `refs` :**

* Vous pouvez accéder à l'élément référencé en utilisant **`this.$refs.nomDuRef`** dans une méthode Vue.js.

***

#### 3. **Mettre à jour la méthode `sauver` pour redonner le focus à l'input**

Nous allons maintenant mettre à jour la méthode `sauver` pour redonner le focus à l'input après avoir sauvegardé la capture.

**Modifiez la méthode `sauver` dans `script.js` pour redonner le focus à l'input :**

```javascript
function sauver() {
  if (!isNaN(compteur.value) && compteur.value > 0) {
    capturesTab.value.push(compteur.value); // Ajoute la capture au tableau
    localStorage.setItem('captures', JSON.stringify(capturesTab.value)); // Sauvegarde dans localStorage
    compteur.value = 0; // Réinitialise le compteur

    // Redonne le focus à l'input après la sauvegarde
    refs.inputCapture.focus(); // Cible l'input via le ref et redonne le focus
  }
}
```

* **`refs.inputCapture.focus()`** : Cela permet d'accéder à l'élément `<input>` référencé par **`ref="inputCapture"`** et de redonner le focus à cet élément après la sauvegarde.

***

#### 4. **Mise à jour complète du fichier `script.js`**

Voici le fichier **`script.js`** mis à jour avec l'utilisation de **`ref`** pour redonner le focus à l'input après chaque sauvegarde.

```javascript
const { createApp, ref } = Vue;

createApp({
  setup() {
    const compteur = ref(0); // Compteur réactif pour les captures
    const capturesTab = ref([]); // Tableau pour stocker les captures

    // Fonction pour capturer un Pokémon
    function capturer() {
      compteur.value += 1;
    }

    // Fonction pour sauvegarder les captures et redonner le focus à l'input
    function sauver() {
      if (!isNaN(compteur.value) && compteur.value > 0) {
        capturesTab.value.push(compteur.value); // Ajoute la capture au tableau
        localStorage.setItem('captures', JSON.stringify(capturesTab.value)); // Sauvegarde dans localStorage
        compteur.value = 0; // Réinitialise le compteur

        // Redonne le focus à l'input
        refs.inputCapture.focus();
      }
    }

    return { compteur, capturesTab, capturer, sauver };
  },
  mounted() {
    this.$refs.inputCapture.focus(); // Met le focus sur l'input à l'ouverture de l'application
  }
}).mount("#poke-app");
```

***

#### Résultat attendu :

* Lorsque l'utilisateur **sauvegarde** une capture en cliquant sur le bouton ou en appuyant sur **Entrée**, l'input est automatiquement **remis en focus** pour permettre à l'utilisateur de saisir rapidement une nouvelle capture.
* Le focus est également mis sur l'input au **chargement de l'application**, ce qui permet de commencer directement la saisie sans cliquer.

***

#### Documentation officielle :

* [Vue.js - Utilisation de `ref`](https://vuejs.org/guide/essentials/template-refs.html)

***

#### Conclusion :

Vous avez maintenant appris à utiliser **`ref`** pour cibler un élément DOM dans Vue.js et interagir avec lui. Grâce à **`ref`**, vous pouvez redonner le **focus à l'input** après la sauvegarde, ce qui améliore l'expérience utilisateur et rend l'interface plus fluide.
