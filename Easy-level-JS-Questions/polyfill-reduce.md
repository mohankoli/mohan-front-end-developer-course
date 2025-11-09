https://www.youtube.com/watch?v=r41zkTenKTc
# ✅ Custom `myReduce()` Implementation (Simple Version)

### This version always loops from index 0 and uses `??` to handle the initial value.

---

## ✅ Code Example

```js
let arr = [1, 2, 3, 4];
let initValue = 0;

Array.prototype.myReduce = function(callback, initValue) {
    let inputArray = this;

    // Use initial value if provided, else use first array element
    let acc = initValue ?? inputArray[0];

    for (let i = 0; i < inputArray.length; i++) {
        acc = callback(acc, inputArray[i]);
    }

    return acc;
}

let res = arr.myReduce((acc, curr) => {
    return acc + curr;
}, initValue);

console.log(res); // 10
