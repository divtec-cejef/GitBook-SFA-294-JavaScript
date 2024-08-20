# Environnement de développement

Dans ce cours, nous utiliserons plusieurs outils pour développer des applications web interactives et maintenir un code de haute qualité. Ces outils comprennent des éditeurs de code, des extensions de navigateur, des gestionnaires de versions, ainsi que des bibliothèques et des frameworks JavaScript.

Cette section vous guidera à travers les outils requis et vous fournira des instructions détaillées pour les installer et les configurer.

Voici le chapitre 1 mis à jour pour **WebStorm**, incluant les instructions pour se connecter à JetBrains Toolbox après l'activation de la licence :

***

## 1. **WebStorm**

WebStorm est un éditeur de code puissant et intelligent, spécialement conçu pour le développement JavaScript. Il offre des fonctionnalités avancées comme l'autocomplétion, la refactorisation et le débogage intégré. WebStorm est particulièrement utile pour travailler sur des projets Vue.js et JavaScript.

### Installation de WebStorm via JetBrains Toolbox

Pour faciliter la gestion des différents outils JetBrains, y compris WebStorm, nous recommandons d'utiliser **JetBrains Toolbox**.

#### **Étapes d'installation :**

1. **Télécharger JetBrains Toolbox :**
   * Rendez-vous sur le site officiel de [JetBrains Toolbox](https://www.jetbrains.com/toolbox-app/).
   * Téléchargez l'application pour votre système d'exploitation.
2. **Installer JetBrains Toolbox :**
   * Ouvrez le fichier téléchargé et suivez les instructions pour installer JetBrains Toolbox.
3. **Utiliser JetBrains Toolbox pour installer WebStorm :**
   * Lancez l'application JetBrains Toolbox après l'installation.
   * Dans la liste des produits disponibles, trouvez **WebStorm** et cliquez sur le bouton "Install".
   * Une fois l'installation terminée, vous pouvez lancer WebStorm directement depuis JetBrains Toolbox.
4. **Activation de la licence étudiante :**
   * Lorsque vous lancez WebStorm pour la première fois, il vous sera demandé de vous connecter à votre compte JetBrains.
   * **Utilisez votre email de l'école** pour activer votre licence étudiante. Vous pouvez obtenir cette licence via le programme [JetBrains Student License](https://www.jetbrains.com/fr-fr/community/education/#students).
5. **Connexion à JetBrains Toolbox :**
   * Après avoir activé votre licence étudiante, retournez dans l'application **JetBrains Toolbox**.
   * Connectez-vous avec votre compte JetBrains (en utilisant l'email de l'école) pour synchroniser la licence avec JetBrains Toolbox.
   * Une fois connecté, vous pourrez gérer vos installations JetBrains, y compris WebStorm, directement depuis Toolbox.

## 2. **GitHub et GitHub Classroom**

GitHub est une plateforme de gestion de versions qui permet de suivre les modifications du code et de collaborer efficacement avec d'autres développeurs. Nous utiliserons également GitHub Classroom pour la gestion des exercices et des projets.

### Installation de Git et Configuration de GitHub

1. Téléchargez et installez Git depuis le site officiel : [git-scm.com](https://git-scm.com/).
2. Créez un compte GitHub sur [github.com](https://github.com/).
3. **Activation de la licence éducation :**  \
   Pour bénéficier des fonctionnalités supplémentaires de GitHub, activez la licence éducation GitHub Student en vous inscrivant via [GitHub Student Developer Pack](https://education.github.com/pack). \
   **Utilisez votre email de l'école** pour cette étape afin de valider votre statut d'étudiant.
4.  Configurez votre identité Git en utilisant les commandes suivantes dans votre terminal :

    ```bash
    git config --global user.name "Votre Nom"
    git config --global user.email "votre.email@exemple.com"
    ```

## 3. **Vuetify**

Vuetify est une bibliothèque de composants Material Design pour Vue.js. Il vous permet de créer des interfaces utilisateur élégantes et responsives rapidement.

### Installation de Vuetify

Pour installer Vuetify dans un projet Vue.js, vous pouvez utiliser l'une des commandes suivantes :

*   Si vous créez un nouveau projet Vuetify :

    ```bash
    npm create vuetify
    ```
*   Si vous ajoutez Vuetify à un projet Vue.js existant :

    ```bash
    npm create vue@3
    npm install vuetify
    ```

Suivez les instructions à l'écran pour configurer Vuetify dans votre projet.

## 4. **Docker**

Docker est un outil de conteneurisation qui permet de déployer des applications dans des environnements isolés. Vous utiliserez Docker pour travailler avec les API fournies pendant le cours.

### Installation de Docker

1. Téléchargez Docker Desktop depuis le site officiel : [docker.com](https://www.docker.com/products/docker-desktop).
2. Installez Docker Desktop en suivant les instructions spécifiques à votre système d'exploitation.
3. Lancez Docker et assurez-vous qu'il fonctionne correctement.

## 5. **Vue Devtools**

Vue Devtools est une extension de navigateur dédiée à l'inspection et au débogage des applications Vue.js. Elle permet de visualiser l'état des composants, les événements et le store, ce qui facilite le développement et le débogage des applications Vue.js.

### Installation de Vue Devtools

1. **Pour Google Chrome :**\
   Ajoutez l'extension Vue Devtools depuis le [Chrome Web Store](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd).
2. **Pour Mozilla Firefox :**\
   Ajoutez l'extension Vue Devtools depuis [Firefox Add-ons](https://addons.mozilla.org/fr/firefox/addon/vue-js-devtools/).
3. Une fois installée, vous pouvez accéder à Vue Devtools directement depuis les outils de développement de votre navigateur (`F12` ou `Ctrl+Shift+I`). Recherchez l'onglet **Vue** dans le panneau des outils de développement

## 6. **ESLint**

ESLint est un outil de linting pour JavaScript, essentiel pour maintenir un code propre et conforme aux normes de développement. Il aide à identifier et corriger les erreurs dans le code tout en respectant des conventions de style définies. Dans ce cours, ESLint est installé par défaut avec Vuetify.

### Commandes de base d'ESLint

Une fois ESLint configuré dans votre projet, voici quelques commandes de base que vous pouvez utiliser :

#### **Vérifier tous les fichiers JavaScript dans le projet :**

```bash
npx eslint .
```

Cette commande scanne tous les fichiers `.js` de votre projet pour détecter les erreurs et les avertissements.

#### **Corriger automatiquement les erreurs :**

```bash
npx eslint . --fix
```

ESLint tentera de corriger automatiquement les erreurs de linting dans votre code.

#### **Vérifier un fichier spécifique :**

```bash
npx eslint chemin/vers/fichier.js
```

Vous pouvez cibler un fichier spécifique pour vérifier les erreurs.

#### **Ignorer des fichiers ou des répertoires spécifiques :**&#x20;

Vous pouvez créer un fichier `.eslintignore` à la racine de votre projet et y ajouter les chemins des fichiers ou répertoires à ignorer. Par exemple :

```
node_modules/
dist/
```

#### Ignorer une ou plusieurs lignes de code

Dans certains cas, vous pourriez avoir besoin d'ignorer une ou plusieurs lignes de code spécifiques lors de l'analyse ESLint. Voici comment procéder :

*   **Ignorer une seule ligne de code :** Pour ignorer une seule ligne, ajoutez un commentaire `eslint-disable-next-line` avant la ligne de code concernée :

    ```javascript
    // eslint-disable-next-line
    const exemple = "Ce code ne sera pas vérifié par ESLint";
    ```
*   **Ignorer des règles spécifiques pour une ligne :** Vous pouvez spécifier quelles règles ESLint doit ignorer pour une ligne donnée :

    ```javascript
    // eslint-disable-next-line no-console
    console.log("Ce code ignore la règle no-console");
    ```
*   **Ignorer plusieurs lignes de code :** Pour ignorer un bloc de code, utilisez `eslint-disable` et `eslint-enable` autour du code concerné :

    ```javascript
    /* eslint-disable */
    const exemple1 = "Cette ligne est ignorée par ESLint";
    const exemple2 = "Celle-ci aussi";
    /* eslint-enable */
    ```
*   **Ignorer des règles spécifiques pour un bloc de code :** Vous pouvez également spécifier quelles règles doivent être ignorées pour un bloc :

    ```javascript
    /* eslint-disable no-alert, no-console */
    alert("Alerte ignorée");
    console.log("Log ignoré");
    /* eslint-enable no-alert, no-console */
    ```



## Conclusion

L'installation et la configuration de ces outils sont essentielles pour réussir dans ce cours. Assurez-vous de **bien utiliser votre email de l'école pour toutes les activations de licences** afin de bénéficier des avantages étudiants.&#x20;

Prenez le temps de bien les configurer avant de commencer les exercices et les projets.&#x20;

Si vous rencontrez des difficultés, n'hésitez pas à demander de l'aide.

