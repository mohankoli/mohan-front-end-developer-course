# Custom `myMap()` Implementation in JavaScript

https://www.youtube.com/watch?v=1N1wq742qeo

This example demonstrates how to create a custom implementation of the JavaScript `Array.prototype.map()` method.

```javascript
const array = [1, 4, 9, 16];

Array.prototype.myMap = function(cb) {
    let arr = this;
    let output = [];
    for (let i = 0; i < arr.length; i++) {
        output.push(cb(arr[i], i, arr));
    }
    return output;
}

// Pass a function to map
const mapped = array.myMap((x) => x * 2);

console.log(mapped); // Output: [2, 8, 18, 32]
