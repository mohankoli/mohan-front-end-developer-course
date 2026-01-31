# Remove Falsy Values from an Array (Clean)

## Problem
Remove all **falsy values** from a JavaScript array.

### Falsy values in JavaScript
The following values are considered falsy:
- `false`
- `0`
- `""` (empty string)
- `null`
- `undefined`
- `NaN`

---

## Solution (Recommended)

```js
function clean(arr) {
  return arr.filter(Boolean);
}

console.log(clean([0, 1, false, 2, "", 3, null, undefined, NaN]));
// Output: [1, 2, 3]
