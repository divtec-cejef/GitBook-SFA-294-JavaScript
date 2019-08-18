# Créer des éléments

## Ajouter un élément enfant à la fin d'un élément existant

Pour ajouter un élément comme dernier fils d'un élément existant il faut :

1. Créer un nouvel élément : `createElement("nomTagHTML")`
2. Créer un nœud texte : `createTextNode("chaine de caractères")`
3. Attacher le nœud texte au nouvel élément : `appendChild(nœudTexte)`
4. Récupérer un élément existant du DOM : voir chapitre [Accéder aux éléments de la DOM](dom-creer.md#Accéder-aux%20éléments-de-la-DOM)
5. Attacher le nouvel élément à l'élément existant du DOM : `appendChild(element)`

### Exemple : Ajouter un élément à la fin d'une liste

Voici comment ajouter le nouvel élément `<li>2kg de Pain</li>` **à la fin** de la liste `#fondue`.

```markup
<ul id="fondue">
    <li>2kg de Fromage</li>
    <li>1L de Kirsh</li>
</ul>

<script>
// 1. Création du nouvel élément <li> 
const newLi = document.createElement('li');

// 2. Création du nœud texte
const newLiTexte = document.createTextNode("2kg de Pain");

// 3. Ajout du texte au <li>
newLi.appendChild(newLiTexte);

// 4. Récupération de la liste
const listeFondue = document.getElementById('fondue');

// 5. Ajoute le nouvel élément <li> à la fin de la liste
listeFondue.appendChild(newLi);
</script>
```

#### Résultat

```markup
<ul id="fondue">
    <li>2kg de Fromage</li>
    <li>1L de Kirsh</li>
    <li>2kg de Pain</li>
</ul>
```

## Ajouter un nouvel élément avant un élément enfant existant

L'exemple précédent nous a montré comment ajouter un nouvel élément enfant à la fin d'un élément existant avec `appendChild()`.

Il existe un autre méthode pour ajouter des éléments : `element.insertBefore()`

```javascript
elementParent.insertBefore(nouvelElement, elementEnfantExistant);
```

Cette méthode permet d'ajouter à un élément existant `elementParent` un élément enfant `nouvelElement` juste avant l'élément enfant spécifié `elementEnfantExistant`.

### Exemple : Ajouter un élément au début d'une liste

Voici comment ajouter le nouvel élément `<li>2kg de Pain</li>` **au début** de la liste `#fondue`.

```markup
<ul id="fondue">
    <li>2kg de Fromage</li>
    <li>1L de Kirsh</li>
</ul>

<script>
// 1. Création du nouvel élément <li> 
const newLi = document.createElement('li');

// 2. Création du nœud texte
const newLiTexte = document.createTextNode("2kg de Pain");

// 3. Ajout du texte au <li>
newLi.appendChild(newLiTexte);

// 4. Récupération d'un 1er élément <li> de la liste actuelle existant du DOM
const premierLi = document.querySelector('#fondue li:first-child');

// 3. Récupération du parent de premierLi
const parentLi = premierLi.parentNode;

// 6. Ajout de newLi avant premierLi
parentLi.insertBefore(newLi, premierLi);
</script>
```

#### Résultat

```markup
<ul id="fondue">
    <li>2kg de Pain</li>
    <li>2kg de Fromage</li>
    <li>1L de Kirsh</li>
</ul>
```

