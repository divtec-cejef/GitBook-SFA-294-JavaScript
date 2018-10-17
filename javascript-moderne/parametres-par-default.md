# Paramètres par défaut

```javascript
let myFunc = function (arg1='default argument one', arg2='default argument two') {
  console.log(arg1 + " & " + arg2);
};

myFunc(undefined, 'and a new value'); // logs 'default argument one & and a new value'
```

