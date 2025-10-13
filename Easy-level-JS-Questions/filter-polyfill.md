# Custom `myFilter()` Implementation in JavaScript

This example demonstrates how to create a custom implementation of the JavaScript `Array.prototype.filter()` method.

```javascript
const array = [1, 4, 9, 16, 25, 30];

Array.prototype.myFilter = function(cb) {
    let arr = this;
    let output = [];
    for (let i = 0; i < arr.length; i++) {
        if (cb(arr[i], i, arr)) {
            output.push(arr[i]);
        }
    }
    return output;
}

// Pass a function to filter
const filtered = array.myFilter((x) => x > 10);

console.log(filtered); // Output: [16, 25, 30]
