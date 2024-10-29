# Magasin Pinia

#### Introduction au magasin Pinia

Pinia est un **gestionnaire d'état** pour Vue.js qui vous permet de centraliser l'**état des données** de votre application de manière propre et efficace.

Dans cet exemple, nous avons un magasin Pinia appelé **`pokemon`** qui contient une liste de différents Pokémon, chacun avec des informations comme le type, le niveau, les capacités, etc. Nous allons voir comment ce magasin est structuré, ainsi que les différentes fonctionnalités qu'il offre.

#### Contenu du Magasin

Le magasin se compose de trois sections principales :&#x20;

* L'état (state) → Les données
* Les getters → Les données calculées → computed
* Les actions → Les méthodes utilisées pour modifier l'état, les données

**État (state)**

L'état est la partie du magasin qui contient **les données** que nous voulons partager dans notre application. Dans cet exemple, l'état comprend :

* **`typeColors`** : un objet associant à chaque type de Pokémon une couleur
* **`pokemons`** : un tableau d'objets représentant chaque Pokémon, chacun avec des caractéristiques comme le nom, le type, le niveau, les capacités et des statistiques (PV, attaque, défense, etc.).
* **`selectedPokemon`** : permet de garder une référence au Pokémon sélectionné par l'utilisateur.
* **`favorites`** : un tableau des Pokémon favoris sélectionnés par l'utilisateur.

**Getters**

Les getters ressemblent aux propriétés calculées pour votre état. Ils permettent de dériver des données  établies sur l'état existant. Par exemple :

* **`favoritesCount`** : ce getter renvoie le nombre de Pokémon ajoutés aux favoris.

**Actions**

Les actions sont utilisées pour modifier l'état. Elles sont comparables aux méthodes dans une classe ou un composant. Voici les actions définies dans notre magasin :

* **`selectPokemon(id)`** : permet de sélectionner un Pokémon à partir de son identifiant. Cela met à jour la propriété `selectedPokemon`.
* **`toggleFavorite(pokemon)`** : ajoute ou de retire un Pokémon de la liste des favoris.
* **`isFavorite(pokemon)`** : renvoie `true` si le Pokémon est dans les favoris, sinon `false`.
* **`getTypeColor(type)`** : renvoie la couleur associée à un type de Pokémon. Si le type n'existe pas, une couleur par défaut est renvoyée.

#### Utilisation du magasin dans un composant

Voyons maintenant comment utiliser ce magasin Pinia dans un composant.

**Importer le magasin**

Pour utiliser le magasin, nous devons d'abord l'importer dans notre composant. Les magasins se trouvent dans le dossier `src/stores/`.

```markup
<script setup>
import { usePokemonStore } from '@/stores/pokemon'
import { storeToRefs } from 'pinia'

// Récupère le magasin des Pokémons
const pokemonStore = usePokemonStore()

/* Récupère les données pokemons, selectedPokemon, favorites
 * et les transforme directement en refs (données réactives) dans le composant
 *
 * Elles sont donc directement accessibles dans le template HTML
 *
 * Attention à ne pas oublier le .value dans le <script> pour accéder à la valeur 
 * comme pour les autre refs.
 */
const { pokemons, selectedPokemon, favorites } = storeToRefs(pokemonStore)

// Fonction pour sélectionner un Pokémon
function selectPokemon(id) {
  pokemonStore.selectPokemon(id)
}

// Fonction pour basculer un Pokémon en favori
function toggleFavorite(pokemon) {
  pokemonStore.toggleFavorite(pokemon)
}

// Fonction pour obtenir le nombre total de Pokémon
function getTotalPokemons() {
  // On utilise .value pour récupérer la valeur
  return pokemons.value.length;
}
</script>
```

* **`usePokemonStore()`** : Cette fonction nous permet d'accéder au magasin.
* **`storeToRefs(pokemonStore)`** : Cette méthode est utilisée pour convertir les propriétés réactives du magasin en références réactives, ce qui facilite leur utilisation dans le template.
* **`selectPokemon()`** et **`toggleFavorite()`** : ces méthodes sont définies localement en appelant les actions du magasin.
* **`getTotalPokemons()`** : méthode locale qui retourne la taille du tableau des Pokémons.

**Utilisation dans le Template**

Voici un exemple de la façon dont vous pouvez utiliser l'état, les getters et les actions dans le template :

```html
<template>
  <div>
    <h1>Liste des Pokémon</h1>
    <ul>
      <li v-for="pokemon in pokemons" :key="pokemon.id">
        <img :src="pokemon.img" :alt="pokemon.name" />
        <h2>{{ pokemon.name }}</h2>
        <p>Type : <span :style="{ color: getTypeColor(pokemon.type) }">{{ pokemon.type }}</span></p>
        <button @click="selectPokemon(pokemon.id)">Voir les détails</button>
        <button @click="toggleFavorite(pokemon)">
          {{ isFavorite(pokemon) ? 'Retirer des favoris' : 'Ajouter aux favoris' }}
        </button>
      </li>
    </ul>
  </div>
</template>
```

* **`v-for="pokemon in pokemons"`** : Boucle sur la liste des Pokémon pour les afficher.
* **`getTypeColor(pokemon.type)`** : Utilise la couleur du type pour styliser le texte.
* **`selectPokemon(pokemon.id)`** : Action pour sélectionner un Pokémon spécifique.
* **`toggleFavorite(pokemon)`** : Action pour ajouter ou retirer un Pokémon des favoris.
