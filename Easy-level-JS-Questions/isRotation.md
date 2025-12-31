
---

## JavaScript Solution

```js
const isRotation = (st1, st2) => {
    if (st1.length !== st2.length) return false;

    let oneWord = st1 + st1;

    if (oneWord.includes(st2)) {
        return true;
    }
};

console.log(isRotation("abcd", "cdab"));


