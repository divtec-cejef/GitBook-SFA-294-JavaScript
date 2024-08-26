# PokeCount

## **Objectif général**

* Créer une application web simple pour capturer et sauvegarder des Pokémon.
* Utiliser JavaScript pour manipuler le document HTML (DOM) et ajouter des fonctionnalités interactives.
* Sauvegarder les captures dans le `localStorage` du navigateur pour les recharger entre les sessions.
* Améliorer le code grâce à des écouteurs d'événements.

***

## Instructions

Pour réaliser cet exercice, copier les fichiers de ce dépôt

{% embed url="https://github.com/fallinov/2024-SFA-JS-EXE-PokeCount/tree/main" %}

### **Étape 1 : Liaison du JavaScript au HTML**

#### **Comprendre les fichiers de départ**&#x20;

* **`index.html`** : Page HTML de l'exercice qui se compose de :
  * un titre principal (`<h1>`)
  * un compteur (`<h2 id="compteur-el">`) initialisé à `0` pour suivre le nombre de Pokémon capturés
  * deux boutons (`<button id="capturer-btn">` et `<button id="sauvegarder-btn">`) pour capturer et sauvegarder les Pokémon
  * un paragraphe (`<p id="sauvegarde-el">`) destiné à afficher l'historique des captures.
* **`style.css`** : stylise la page avec un fond thématique Pokémon et des couleurs de boutons.
* **`pokemon-bg.webp`** : Image de fond utilisée dans le CSS.

#### **Créer un fichier JavaScript et lier au HTML :**

* **Action :** Créez un nouveau fichier nommé `script.js` dans le même dossier que `index.html`.
*   **Action :** Liez ce fichier JavaScript au fichier HTML en ajoutant la ligne suivante dans `index.html`, juste avant la fermeture de la balise `</body>` :

    ```html
    <script src="script.js"></script>
    ```

#### **Afficher un message "Hello World" :**

*   **Action :** Ouvrez `script.js` et commencez par ajouter un bloc de commentaires pour décrire le fichier :

    ```javascript
    /**
    * Fichier JavaScript pour l'application PokeCount.
    * @author Steve Fallet <steve.fallet@divtec.ch>
    * @version 0.1 (Version actuelle)
    * @since 2024-01-31 (Date de création)
    */
    ```
*   **Action :** Toujours dans `script.js`, ajoutez le code suivant pour afficher "Hello World" dans la console du navigateur :

    ```javascript
    console.log("Hello World");
    ```
* **Test :**
  * Ouvrez `index.html` dans un navigateur web.
  * Ouvrez la console du navigateur (F12 ou clic droit > Inspecter > Console) pour vérifier que le message "Hello World" s'affiche correctement, ce qui confirme que le JavaScript est correctement lié à votre fichier HTML.
*   **Action :** Remplacez `console.log` par `alert` pour afficher une boîte de dialogue :

    ```javascript
    alert("Hello World");
    ```
* **Test :**
  * Ouvrez `index.html` dans un navigateur web.
  * Vérifiez que la boîte de dialogue s'affiche correctement.

#### Différence entre `console.log` et `alert` :

* **`console.log`** : Affiche des messages dans la console du navigateur, accessible via les outils de développement. Cela permet de vérifier discrètement des informations, des valeurs de variables, ou le flux d’exécution sans interrompre l’expérience utilisateur.
* **`alert`** : Affiche une boîte de dialogue modale à l’utilisateur avec un message. Cette boîte bloque l’exécution du script jusqu’à ce que l’utilisateur la ferme, ce qui interrompt l’expérience utilisateur.

#### **Pourquoi utiliser `console.log` pour le débogage :**

* **Non intrusif** : `console.log` permet de déboguer en arrière-plan sans gêner l’utilisateur, contrairement à `alert` qui interrompt le flux normal de l’application.
* **Flexibilité** : Vous pouvez afficher plusieurs messages successivement, analyser des objets complexes, et garder une trace des événements dans la console, ce qui est bien plus commode pour diagnostiquer des problèmes dans votre code.

En résumé, `console.log` est l’**outil de choix pour le débogage**, car il est discret, puissant et n’affecte pas l’expérience utilisateur.

***

### **Étape 2 : Manipulation du DOM pour modifier un élément**

Le JavaScript peut être utilisé pour manipuler le contenu d'une page web en modifiant le Document Object Model (DOM). On peut accéder aux éléments HTML, modifier leur contenu, leur style, ou même ajouter de nouveaux éléments dynamiquement.

#### **Récupérer le premier élément `<h2>` du document HTML et modifier son contenu :**

*   **Action :** Utilisez `document.querySelector` pour récupérer le premier élément `<h2>` du document et modifiez son contenu pour qu'il affiche `20` :

    ```javascript
    document.querySelector("h2").textContent = 20;
    ```
* **Test :** Actualisez la page dans le navigateur. L'élément `<h2>` doit maintenant afficher `20`.

#### **Récupérer un élément par son identifiant unique (ID) :**

*   **Action :** Utilisez `document.getElementById` pour récupérer l'élément avec l'ID `compteur-el` et modifiez son contenu pour qu'il affiche `100`. Ajoutez cette ligne dans `script.js` :

    ```javascript
    document.getElementById("compteur-el").textContent = 100;
    ```
* **Test :** Actualisez la page dans le navigateur. L'élément `<h2>` doit désormais afficher `100`.

#### Différence entre `getElementById` et `querySelector` :

`getElementById` et `querySelector` sont deux méthodes pour récupérer des éléments du DOM en JavaScript.

*   **`getElementById`** : Permet de récupérer un élément par son identifiant unique (ID) défini dans le HTML. C'est la méthode la plus rapide pour accéder à un élément spécifique.

    ```javascript
    // Sélectionner un élément <div> avec l'ID "main-content"
    const mainContent = document.getElementById("main-content");
    // Sélectionner un élément <header> avec l'ID "site-header"
    const siteHeader = document.getElementById("site-header");
    // Sélectionner un bouton avec l'ID "submit-btn"
    const submitButton = document.getElementById("submit-btn");
    ```
*   **`querySelector`** : Permet de récupérer un élément grâce à un sélecteur CSS. Cela signifie que vous pouvez cibler des éléments par leur balise, classe, attribut, ou même leur position dans le DOM.

    ```javascript
    // Sélectionner le premier paragraphe du document
    const firstParagraph = document.querySelector("p");
    // Sélectionner un élément par son identifiant (ID)
    const header = document.querySelector("#header");
    // Sélectionner le premier élément avec une classe spécifique
    const firstButton = document.querySelector(".btn");
    // Sélectionner un élément de type <div> avec une classe spécifique
    const specialDiv = document.querySelector("div.special");
    // Sélectionner le premier élément <input> dans un formulaire avec une classe spécifique
    const firstInput = document.querySelector("form input.form-input");
    ```

> Utilisez `getElementById` pour les éléments avec un identifiant unique, et `querySelector` pour des sélections plus complexes.

***

### **Étape 3 : Création et affichage de variables**

> Avant de commencer, mettez en commentaire ou supprimez les codes précédents pour éviter les conflits.

Nous allons créer des variables pour stocker le compteur de Pokémon et l'élément `<h2 id="compteur-el">` du document.

#### **Créer une variable pour représenter l'élément HTML `<h2 id="compteur-el">` et une pour le compteur du jeu :**

*   **Action :** Dans `script.js`, créez deux variables :

    * Une variable `compteur` pour stocker la valeur du compteur (initialement `0`).
    * Une variable `compteurEl` pour stocker la référence à l'élément `<h2 id="compteur-el">`. Utilisez `const` pour cette référence puisque l'élément ne changera pas.

    ```javascript
    let compteur = 0;
    const compteurEl = document.getElementById("compteur-el");
    ```

#### Pourquoi stocker les références des éléments HTML dans des variables ?

Cela améliore les **performances** en évitant de chercher l'élément dans le DOM à chaque fois. C'est aussi plus **lisible** et **facile à maintenir** comme vous réutilisez la même variable.

***

### **Étape 4 : Préparation pour la capture de Pokémon**

#### **Créer une fonction pour capturer un Pokémon :**

*   **Action :** Créez une fonction `capturer()` qui incrémente le compteur et actualise le texte de `<h2 id="compteur-el">`.

    ```javascript
    function capturer() {
        compteur += 1; // Incrémenter le compteur de 1
        compteurEl.textContent = compteur; // Actualiser le texte de l'élément <h2>
    }
    ```

#### **Lier la fonction au bouton "CAPTURER" :**

*   **Action :** Assurez-vous que le bouton "CAPTURER" dans `index.html` appelle la fonction `capturer()` grâce à l'attribut `onclick` :

    ```html
          <button id="capturer-btn" onclick="capturer()">CAPTURER</button>
    ```

3. **Test :** Actualisez la page dans le navigateur. Cliquez sur le bouton "CAPTURER" et vérifiez que le compteur augmente à chaque clic.

***

### **Étape 5 : Changer la couleur du compteur toutes les cinq captures**

Nous souhaitons modifier la couleur du texte du compteur toutes les cinq captures pour rendre le jeu plus interactif.

* Moins de 5 captures : couleur verte
* De 5 à 10 captures : couleur jaune
* Plus de 10 captures : couleur rouge

#### **Modifier le code de la fonction `capturer()` pour modifier la couleur du texte du compteur en fonction du nombre de captures :**

*   **Action :** Modifiez la fonction `capturer()` pour changer la couleur du texte du compteur selon le nombre de captures. Utilisez une condition `if...else if...else` pour déterminer la couleur :

    ```javascript
    function capturer() {
        compteur += 1; // Incrémenter le compteur de 1
        compteurEl.textContent = compteur; // Mettre à jour le texte de l'élément <h2>
        if (compteur < 5) {
            compteurEl.style.color = "green"; // Couleur verte pour moins de 5 captures
        } else if (compteur < 10) {
            compteurEl.style.color = "yellow"; // Couleur jaune pour 5 à 9 captures
        } else {
            compteurEl.style.color = "red"; // Couleur rouge pour 10 captures ou plus
        }
    }
    ```
* **Test :** Actualisez la page dans le navigateur. Capturez des Pokémon pour vérifier que la couleur du texte du compteur change correctement.

***

### **Étape 6 : Sauvegarde des captures**

#### **Créer une variable pour stocker les captures sauvegardées :**

*   **Action :** Créez une variable `sauvegardeEl` pour stocker la référence à l'élément `<p id="sauvegarde-el">` :

    ```javascript
    const sauvegardeEl = document.getElementById("sauvegarde-el");
    ```

#### **Créer une fonction pour sauvegarder les captures :**

*   **Action :** Créez une fonction `sauvegarder()` qui ajoute la valeur actuelle du compteur au paragraphe `sauvegarde-el` et réinitialise le compteur à `0`.

    ```javascript
    function sauvegarder() {
        let compteurStr = compteur + " Pokémons - ";
        sauvegardeEl.textContent += compteurStr; // Ajouter la valeur actuelle du compteur
        compteur = 0;
        compteurEl.textContent = compteur;
    }
    ```

#### **Lier la fonction au bouton "SAUVEGARDER" :**

*   **Action :** Assurez-vous que le bouton "SAUVEGARDER" dans `index.html` appelle la fonction `sauvegarder()` :

    ```html
    <button id="sauvegarder-btn" onclick="sauvegarder()">SAUVEGARDER</button>
    ```
* **Test :**&#x20;
  * Actualisez la page dans le navigateur.
  * Capturez quelques Pokémon, puis cliquez sur "SAUVEGARDER".
  * Vérifiez que les captures sont ajoutées à la liste et que le compteur se réinitialise.

***

### **Étape 7 : Amélioration du code avec des écouteurs d'événements**

#### **Retirer les attributs `onclick` du HTML :**

*   **Action :** Ouvrez `index.html` et retirez les attributs `onclick` des boutons "CAPTURER" et "SAUVEGARDER". Les boutons devraient ressembler à ceci :

    ```html
    <button id="capturer-btn">CAPTURER</button>
    <button id="sauvegarder-btn">SAUVEGARDER</button>
    ```

#### **Ajouter des écouteurs d'événements dans JavaScript :**

*   **Action :** Dans `script.js`, récupérez les références aux boutons et ajoutez des écouteurs d'événements pour lier les fonctions `capturer()` et `sauvegarder()` :

    ```javascript
    const capturerBtn = document.getElementById("capturer-btn");
    const sauvegarderBtn = document.getElementById("sauvegarder-btn");

    capturerBtn.addEventListener("click", capturer);
    sauvegarderBtn.addEventListener("click", sauvegarder);
    ```
* **Test :**&#x20;
  * Actualisez la page dans le navigateur.
  * Vérifiez que le bouton "CAPTURER" incrémente toujours le compteur et que le bouton "SAUVEGARDER" sauvegarde correctement les captures.

#### Pourquoi cette étape est-elle importante ?

L'utilisation d'écouteurs d'événements améliore la **séparation** entre le HTML (contenu) et le JavaScript (fonctionnalité). Cela rend le code plus **modulaire**, plus **facile à maintenir**, et **extensible** pour des projets plus complexes.

***

### **Étape 8 : Utiliser le `localStorage` pour sauvegarder les captures**

Actuellement, les captures sont stockées temporairement dans la page web, mais elles sont perdues si l'utilisateur recharge la page ou ferme le navigateur. Pour résoudre ce problème, nous allons utiliser le `localStorage`.

Le `localStorage` est une fonctionnalité du navigateur qui permet de stocker des données localement sur l'ordinateur de l'utilisateur. Cela peut être utile pour sauvegarder des informations entre les rechargements de page ou les sessions.

**Sauvegarder les captures dans le `localStorage` :**

*   **Action :** Modifiez la fonction `sauvegarder()` pour stocker les captures dans le `localStorage` du navigateur :

    ```javascript
    function sauvegarder() {
        let compteurStr = compteur + " Pokémons - ";
        sauvegardeEl.textContent += compteurStr; // Ajouter la valeur actuelle du compteur
        localStorage.setItem("captures", sauvegardeEl.textContent); // Sauvegarder les captures dans le localStorage
        compteur = 0;
        compteurEl.textContent = compteur;
    }
    ```
* **Test :** Visualisez les données sauvegardées dans le `localStorage` en ouvrant les outils de développement du navigateur (F12 ou clic droit > Inspecter > Application > Local Storage).

**Charger les captures sauvegardées au chargement de la page :§**

*   **Action :** Ajoutez le code suivant pour charger les captures sauvegardées au chargement de la page :

    ```javascript
    window.addEventListener("load", () => { // Attendre que la page soit chargée pour exécuter le code 
        sauvegardeEl.textContent = localStorage.getItem("captures") || ""; // Charger les captures sauvegardées ou une chaîne vide
    });
    ```
* **Test :** Actualisez la page dans le navigateur. Capturez quelques Pokémon, sauvegardez-les, puis rechargez la page.

***

## **Challenges supplémentaires**

* Ajouter un bouton "RESET" pour réinitialiser le compteur et les captures.
* Afficher l'historique des captures dans une liste à puce.
* Conduire l'historique des captures dans un tableau JavaScript.
* Permettre à l'utilisateur de supprimer des captures de l'historique.
