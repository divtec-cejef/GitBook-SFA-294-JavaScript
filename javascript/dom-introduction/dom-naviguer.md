# Naviguer dans le DOM

## Récupérer les enfants d'un élément

### element.childNodes

```javascript
let monElement = document.getElementById('monElement');
let enfants = monElement.childNodes;
```

### Récupérer le dernier fils

**Problème** :  `Element.lastChild` retourne le dernier noeud fils d'un élément. Mais ce derniers fils n'est pas forcément un élément HTML.

**Solution** :  `Element.querySelector(":last-child")`

## Récupérer le parent d'un élément

### element.parentNode

```javascript
let parent = enfants.parentNode;
```



