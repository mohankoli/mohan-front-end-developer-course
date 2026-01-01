### 📌 Nested Array Sum using Recursion + Reduce

```js
const sumNested = (arr) => {
    let res = [];
    arr.forEach((item) => {
        if (Array.isArray(item)) {
            res.push(...sumNested(item));
        } else {
            res.push(item);
        }
    });
    return res;
};

let total = sumNested([1, [2, [3]]]).reduce((acc, curr) => {
    return acc + curr;
}, 0);

console.log(total); // 6
