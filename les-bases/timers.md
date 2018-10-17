# Timers

```javascript
function simpleMessage() {
  alert('This is just a simple alert');
}

// set time out
window.setTimeout(simpleMessage, 5000);

// if you wanted to clear the timer.
let timer = window.setTimeout(simpleMessage, 5000);
window.clearTimeout(timer);

// set interval. will repeat every  5000ms
window.setInterval(simpleMessage, 5000);

// if you wanted to clear the intervals.

let intervalHandler = window.setInterval(simpleMessage, 5000);
window.clearInterval(intervalHandle);
```

