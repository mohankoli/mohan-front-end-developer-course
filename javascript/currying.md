# JavaScript Currying

**Currying** is a functional programming technique in JavaScript where a function with multiple arguments is transformed into a series of functions that each take a single argument.


In simple terms, it allows you to call functions like this: `func(a)(b)` instead of `func(a, b)`.

## Example

```javascript
function add(a) {
  return function(b) {
    return a + b;
  };
}

console.log(add(3)(4)); // Output: 7


