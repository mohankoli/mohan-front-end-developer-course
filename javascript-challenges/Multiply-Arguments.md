# `multiply` Function Example in JavaScript

This example demonstrates a custom `multiply` function that uses the `arguments` object and `Array.reduce()` to perform multiplication or addition based on a condition.

## Code

```javascript
// Online Javascript Editor for free
// Write, Edit and Run your Javascript code using JS Online Compiler

// console.log(multiply(4, 5))
// // 4 * 5 = 20

// console.log(multiply(1, 2, 3, 5))
// // 1 * 2 * 3 * 5 = 30

// console.log(multiply(2, 0, 4, 2))
// // 2 + 0 * 4 * 2

function multiply() {
    let arr = [...arguments];
    const result = arr.reduce((total, item) => {
        return item ? total * item : total + item; 
    }, 1);
    return result;
}

console.log(multiply(2, 0, 4, 2)); // Output: 3
