
---

### Solution (JavaScript)

```js
let text = "I love javascript coding";

const findLong = (str) => {
    let words = str.split(" ");
    let longest = "";

    for (let word of words) {
        if (word.length > longest.length) {
            longest = word;
        }
    }
    return longest;
};

findLong(text);
