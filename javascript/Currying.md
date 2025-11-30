# Currying in JavaScript

## 📘 Definition
**Currying** means converting a function that takes **multiple arguments** into a function that takes **one argument at a time**.

---

## ✅ 1. Currying Function (Currying)

```js
function add(a) {
  return function(b) {
    return function(c) {
      return a + b + c;
    }
  }
}

console.log(add(1)(2)(3)); // 6

```

---

## ✅ 2. Infinite Currying Example

```js
function add(a) {
  return function (b) {
    if (b !== undefined) {   // keep chaining
      return add(a + b);
    }
    return a;                // terminate
  };
}

console.log(add(1)(2)(3)());    // 6
console.log(add(5)(10)(20)());  // 35
