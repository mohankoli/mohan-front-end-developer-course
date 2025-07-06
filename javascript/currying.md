# JavaScript Currying

**Currying** is a functional programming technique in JavaScript where a function with multiple arguments is transformed into a series of functions that each take a single argument.

## Why use currying?
- Improves function reusability
- Makes code more readable and modular
- Enables partial function application

## Example

```javascript
// Normal function
function multiply(a, b) {
  return a * b;
}

// Curried version
function curriedMultiply(a) {
  return function(b) {
    return a * b;
  };
}

const multiplyBy2 = curriedMultiply(2);
console.log(multiplyBy2(5)); // Output: 10
