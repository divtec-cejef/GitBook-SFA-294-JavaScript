# Création d'une application Vuetify

### Création et Configuration d'un Projet Vuetify

Pour créer un nouveau projet avec Vuetify en utilisant la configuration recommandée, suivez les étapes ci-dessous :

1. **Créer un projet Vuetify :**
   *   Dans votre terminal, exécutez la commande suivante pour créer un nouveau projet Vuetify :

       ```bash
       npm create vuetify
       ```
   * Vous serez invité à répondre à quelques questions pour configurer le projet :
     * **Project name:** Entrez le nom de votre projet, par exemple, `hello-world`.
     * **Which preset would you like to install?** Sélectionnez `Recommended`&#x20;
     * **Would you like to install dependencies with yarn, npm, pnpm, or bun?** Sélectionnez `npm`
     * **Use TypeScript?** Sélectionnez `No`&#x20;
     * **Install Dependencies?** Sélectionnez `Yes`&#x20;
2. **Accéder au répertoire de votre projet**
   *   Une fois la création du projet terminée, accédez au répertoire de votre nouveau projet :

       ```bash
       cd hello-world
       ```
3. **Démarrer le serveur de développement**
   *   Pour lancer votre projet en mode développement, exécutez la commande suivante :

       ```bash
       npm run dev
       ```
   *   Cette commande démarrera un serveur local. Vous verrez une sortie similaire à celle-ci dans votre terminal :

       ```
       VITE v5.4.1  ready in 302 ms

       ➜  Local:   http://localhost:3000/
       ➜  Network: use --host to expose
       ➜  press h + enter to show help
       ```
4. **Voir votre projet dans le navigateur**
   * Ouvrez votre navigateur web préféré (Chrome, Firefox, etc.).
   * Entrez l'URL `http://localhost:3000/` dans la barre d'adresse.
   * Votre projet Vuetify sera visible et interactif dans le navigateur.
5. **Arrêter le serveur de développement**&#x20;
   * Utilisez le raccourci `CTRL+C` pour arrêter le serveur
   * Ou fermer le terminal

### Commandes de base utiles avec Vuetify

Voici quelques commandes de base que vous trouverez utiles pour travailler avec un projet Vuetify :

1. **Installer un nouveau composant ou une nouvelle dépendance :**
   *   Pour ajouter des packages ou des composants supplémentaires à votre projet, utilisez la commande `npm install`. Par exemple :

       ```bash
       npm install @vuetify/icons-material
       ```
   * Cela installe le package `@vuetify/icons-material` qui peut être utilisé dans votre projet.
2. **Générer un fichier de production :**
   *   Lorsque vous êtes prêt à déployer votre application, vous devez générer un fichier de production optimisé :

       ```bash
       npm run build
       ```
   * Cette commande compile votre projet et crée un dossier `dist/` contenant les fichiers optimisés pour la production.
3. **Lancer un serveur de prévisualisation pour la production :**
   *   Après avoir généré les fichiers de production, vous pouvez les prévisualiser avec cette commande :

       ```bash
       npm run preview
       ```
   * Cela lancera un serveur local pour voir à quoi ressemble votre application en production.
4. **Mise à jour des dépendances :**
   *   Gardez vos dépendances à jour avec la commande suivante :

       ```bash
       npm update
       ```
   * Cela met à jour tous les packages listés dans votre `package.json` vers leurs versions les plus récentes compatibles.
5. **Lint et correction automatique du code :**
   *   Vuetify utilise ESLint pour vérifier la qualité du code. Vous pouvez lancer ESLint pour vérifier votre code :

       ```bash
       npm run lint
       ```
   *   Vous pouvez également corriger automatiquement les erreurs de linting en ajoutant `--fix` :

       ```bash
       npm run lint --fix
       ```

Ces commandes vous aideront à gérer efficacement votre projet Vuetify et à maintenir un flux de travail fluide tout au long du développement.
