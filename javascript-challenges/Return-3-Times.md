# Nested Function Example in JavaScript

This example demonstrates how nested functions can be used to compute a specific expression.

```javascript
// example(1,2)(1,2)(3,4)
// 1 * 1 * 3 + 2 * 2 * 4 = 3 + 16 = 19
//short code using arrow function
//const example = (a, b) => (c, d) => (e, f) => a * c * e + b * d * f;


function example(a, b) {
    return function(c, d) {
        return function(e, f) {
            // console.log(a, b, c, d, e, f);
            return a * c * e + b * d * f;
        }
    }
}

console.log(example(1,2)(1,2)(3,4)); // Output: 19
