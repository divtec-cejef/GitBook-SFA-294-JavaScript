# Number

L'objet **`Number`** est une enveloppe objet (_wrapper_) autour du [type primitif numérique](https://developer.mozilla.org/fr/docs/Web/JavaScript/Data\_structures#le\_type\_nombre). Autrement dit, il est utilisé pour manipuler les nombres comme des objets. Pour créer un objet `Number`, on utilise le constructeur `Number()`.

### Syntaxe <a href="#syntaxe" id="syntaxe"></a>

```
new Number(valeur);
var a = new Number('123'); // a === 123 donnera false
var b = Number('123'); // b === 123 donnera true
a instanceof Number; // donnera true
b instanceof Number; // donnera false
```

#### Paramètres <a href="#parametres" id="parametres"></a>

`valeur`

La valeur numérique pour l'objet qu'on souhaite créer.

### Description <a href="#description" id="description"></a>

L'objet `Number` est principalement utilisé dans les cas de figure suivants :

* Si l'argument ne peut pas être converti en un nombre, il renverra [`NaN`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/NaN).
* Dans un contexte de fonction simple (quand il n'est pas utilisé comme un constructeur avec l'opérateur [`new`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Operators/new)), `Number` peut être utilisé afin d'effectuer des conversions.

### Propriétés <a href="#proprietes" id="proprietes"></a>

[`Number.EPSILON`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/EPSILON)

Le plus petit intervalle entre deux valeurs qu'il est possible de représenter en JavaScript.

[`Number.MAX_SAFE_INTEGER`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/MAX\_SAFE\_INTEGER)

La valeur entière maximale qu'on peut représenter en JavaScript (`2^53 - 1`).

[`Number.MAX_VALUE`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/MAX\_VALUE)

La valeur numérique maximale qu'on peut représenter en JavaScript.

[`Number.MIN_SAFE_INTEGER`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/MIN\_SAFE\_INTEGER)

La valeur entière minimale qu'on peut représenter en JavaScript (`-(2^53 - 1)`).

[`Number.MIN_VALUE`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/MIN\_VALUE)

La plus petite valeur qu'on peut représenter en JavaScript, c'est-à-dire le plus petit nombre positif (le nombre le plus près de zéro qui n'est pas égal à zéro et qu'on peut représenter en JavaScript).

[`Number.NaN`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/NaN)

Une valeur spéciale pour représenter les valeurs non-numériques (**NaN** correspond à « **\*n**ot **a** **n**umber\* » en anglais, qui signifie « n'est pas un nombre »).

[`Number.NEGATIVE_INFINITY`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/NEGATIVE\_INFINITY)

Une valeur spéciale pour représenter l'infini négatif.

[`Number.POSITIVE_INFINITY`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/POSITIVE\_INFINITY)

Une valeur spéciale pour représenter l'infini (positif).

[`Number.prototype` (en-US)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Number)

Cet objet permet d'ajouter des propriétés aux instances de `Number`.

### Méthodes <a href="#methodes" id="methodes"></a>

[`Number.isNaN()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/isNaN)

Cette méthode permet de déterminer si la valeur passée en argument vaut `NaN`.

[`Number.isFinite()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/isFinite)

Cette méthode permet de déterminer si la valeur numérique passée en argument est un nombre fini.

[`Number.isInteger()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/isInteger)

Cette méthode permet de déterminer si la valeur passée en argument est un entier.

[`Number.isSafeInteger()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/isSafeInteger)

Cette méthode permet de déterminer si la valeur passée en argument peut correctement être représentée comme un entier en JavaScript (savoir si elle est comprise entre `-(2^53 - 1)` et `2^53 - 1`).

`Number.toInteger()`&#x20;

Cette méthode est utilisée afin d'évaluer et de convertir la valeur passée en argument en entier (ou en l'[infini](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Infinity)). Cette méthode a été supprimée.

[`Number.parseFloat(string)`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/parseFloat)

Cette méthode correspond à la méthode [`parseFloat()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/parseFloat) de l'objet global.

[`Number.parseInt(string, [radix])`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/parseInt)

Cette méthode correspond à la méthode [`parseInt()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/parseInt) de l'objet global.

[`Number.prototype.toFixed()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/toFixed)

La méthode **`toFixed()`** permet de formater (arrondir) un nombre en notation à point-fixe.

```javascript
2.345789.toFixed(2); // Renvoie '2.35'
```

### Les instances de `Number` <a href="#les_instances_de_number" id="les_instances_de_number"></a>

Toutes les instances de `Number` héritent de [`Number.prototype` (en-US)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Number). Il est possible de modifier le prototype du constructeur `Number` pour affecter toutes les instances de `Number`.

#### Méthodes <a href="#methodes_2" id="methodes_2"></a>

[`Number.prototype.toExponential(fractionDigits)`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/toExponential)

Retourne une chaîne représentant le nombre en notation exponentielle.

[`Number.prototype.toFixed(digits)`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/toFixed)

Retourne une chaîne représentant le nombre avec la notation virgule fixe.

[`Number.prototype.toLocaleString([locales [, options]])`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/toLocaleString)

Retourne une chaîne avec une représentation sensible à la langue de ce nombre. Surcharge la méthode [`Object.prototype.toLocaleString()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Object/toLocaleString).

[`Number.prototype.toPrecision(precision)`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/toPrecision)

Retourne une chaîne représentant le nombre avec une précision donnée en notation virgule fixe ou exponentielle.

[`Number.prototype.toString([radix])`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/toString)

Retourne une chaîne représentant le nombre dans une base numérique (radix) donnée. Surcharge la méthode [`Object.prototype.toString()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Object/toString).

[`Number.prototype.valueOf()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Number/valueOf)

Retourne la valeur primitive de l'objet spécifié. Surcharge la méthode [`Object.prototype.valueOf()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Object/valueOf).

### Exemples <a href="#exemples" id="exemples"></a>

#### Utiliser l'objet `Number` pour affecter des valeurs numériques à des variables <a href="#utiliser_lobjet_number_pour_affecter_des_valeurs_numeriques_a_des_variables" id="utiliser_lobjet_number_pour_affecter_des_valeurs_numeriques_a_des_variables"></a>

Dans l'exemple suivant, on utilise les propriétés de l'objet `Number` pour affecter des valeurs à des variables numériques :

```
var plusGrandNombre = Number.MAX_VALUE;
var plusPetitNombre = Number.MIN_VALUE;
var infini = Number.POSITIVE_INFINITY;
var infiniNégatif = Number.NEGATIVE_INFINITY;
var nonNumérique = Number.NaN;
```

#### Intervalle entier pour `Number` <a href="#intervalle_entier_pour_number" id="intervalle_entier_pour_number"></a>

Dans l'exemple suivant, on illustre les valeurs numériques maximales et minimales (exclues) qu'on peut représenter avec un nombre en JavaScript (pour plus de détails, [voir le chapitre 6.1.6 du standard ECMAScript](https://tc39.github.io/ecma262/#sec-ecmascript-language-types-number-type)) :

```
var biggestInt = 9007199254740992; //Number.MAX_SAFE_INTEGER+1 (2^53-1)
var smallestInt = -9007199254740992; //Number.MIN_SAFE_INTEGER-1 -(2^53-1)
```

Lorsqu'on analyse et convertit des données JSON, les valeurs en dehors de cet intervalle peuvent entraîner des erreurs ou des corruptions de valeurs lors de leurs conversions. Selon les objets qu'on souhaite représenter, on peut utiliser [`String`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/String) dans certains cas pour représenter certaines valeurs.

#### Utiliser `Number` pour convertir un objet `Date` <a href="#utiliser_number_pour_convertir_un_objet_date" id="utiliser_number_pour_convertir_un_objet_date"></a>

Dans l'exemple suivant, on convertit un objet [`Date`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global\_Objects/Date) en une valeur numérique grâce à la fonction `Number` :

```
var d = new Date('December 17, 1995 03:24:00');
console.log(Number(d));
```

Ceci affichera "819167040000".

#### Convertir une chaîne représentant une valeur numérique en un nombre <a href="#convertir_une_chaine_representant_une_valeur_numerique_en_un_nombre" id="convertir_une_chaine_representant_une_valeur_numerique_en_un_nombre"></a>

```
Number("123");       // 123
Number("12.3");      // 12.3
Number("12.00");     // 12
Number("123e-1");    // 12.3
Number("");          // 0
Number("0x11");      // 17
Number("0b11");      // 3
Number("0o11");      // 9
Number("toto");      // NaN
Number("100a");      // NaN
Number("-Infinity"); // -Infinity
```

**Note :** On pourra également convertir `null` en `0` grâce à `Number` : `Number(null)` donnera `0`.
