# Template Literals

Les **Template literals** permettent d'écrire des **chaines de caractètes multilignes** contenant des **expressions**.

* Ces chaines spéciales sont délimitées par des **accents graves** ```ma chaine```.
* Les expressions commencent par un  `$` et sont délimitées par des accolades : `${expression}`

```typescript
let nom = 'Skywlaker';
let prenom = 'Luc'
let message = `Salut ${prenom} ${nom} !`;

alert(message); // Salut Luc Skywlaker !

let ficheClient = `<div class="fiche-client">
						<div>Nom : ${nom}</div>
				   		<div>Prenom : ${prenom}</div>
            	   		<button>Appeler papa</button>
                    </div>`;

document.write(ficheClient);
```

{% embed url="https://codepen.io/fallinov/pen/NEXGGX?editors=0010" %}

