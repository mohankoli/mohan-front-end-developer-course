# JavaScript Currying

**Currying** means breaking a function with multiple arguments into a series of functions that each take one argument.

In simple terms, it allows you to call functions like this: `func(a)(b)` instead of `func(a, b)`.

## Example

```javascript
function add(a) {
  return function(b) {
    return a + b;
  };
}

console.log(add(3)(4)); // Output: 7


