# Memoization

Memoization is a way to **cache a return value of a function based on its parameters**. This makes the function that takes a long time run much faster after one execution. If the parameter changes, it will still have to reevaluate the function.

---

## Things to Avoid in JavaScript (if possible)

- `eval()`
- `arguments`
- `for...in`

---

## Example Without Memoization

```javascript
function addTo80(n) {
  console.log('long time...');
  return n + 80;
}

addTo80(5);
addTo80(5);
addTo80(5);

// Output:
// long time... 85
// long time... 85
// long time... 85
