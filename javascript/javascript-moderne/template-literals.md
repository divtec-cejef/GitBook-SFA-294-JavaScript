# Template Literals

Les **Template literals** permettent d'écrire des **chaines de caractètes multilignes** contenant des **expressions**.

Ces chaines spéciales sont délimitées par des **accents graves** ```ma chaine```.

```typescript
let nom = 'Luc';
let prenom = 'Skywlaker'
let message = `Salut ${nom} ${prenom} !`;

alert(message); // Salut Luc !

let ficheClient = `<div class="fiche-client">
						<div>Nom : ${nom}</div>
				   		<div>Prenom : ${prenom}</div>
            	   		<button>Appeler papa</button>
                    </div>`;

document.write(ficheClient);
```

{% embed url="https://codepen.io/fallinov/pen/NEXGGX?editors=0010" %}

