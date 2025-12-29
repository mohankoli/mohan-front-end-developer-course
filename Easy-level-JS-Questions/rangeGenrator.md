# Range Generator Using Closures (JavaScript)

## Problem

Implement a `range(start, end)` generator using **closures**.
The function should return numbers one by one on each call.

---

## Solution

```js
function range(start, end) {
  let current = start;

  return function () {
    if (current <= end) {
      return current++;
    }
    return null; // end of range
  };
}
```

---

## Example Usage

```js
const next = range(1, 5);

console.log(next()); // 1
console.log(next()); // 2
console.log(next()); // 3
console.log(next()); // 4
console.log(next()); // 5
console.log(next()); // null
```

---

## Explanation

* `current` is a local variable inside `range`
* The inner function **remembers** `current` using a closure
* Each call updates and returns the next value

---

## Key Concept

> A closure allows a function to access variables from its outer scope even after the outer function has finished execution.

---

## Complexity

* Time: **O(1)** per call
* Space: **O(1)**

---

## Notes

* This is a closure-based generator
* No ES6 `function*` or iterators used
* Ideal for interview questions
