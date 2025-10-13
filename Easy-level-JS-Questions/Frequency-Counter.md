# Character Frequency Counter in JavaScript

This snippet demonstrates how to count the frequency of each character in a string and return it as an object.

```javascript
// Count character frequencies in a string (return an object)

let str = 'aabbczzbbttmsq';

let freqCount = (str) => {
    let strMap = {};
    for(let char of str) {
        strMap[char] = (strMap[char] || 0) + 1;
    }
    return strMap;
}

console.log(freqCount(str));
```

## Output

```
{ a: 2, b: 4, c: 1, z: 2, t: 2, m: 1, s: 1, q: 1 }
```

### Explanation

* Iterate over each character in the string.
* Use an object (`strMap`) to keep count of each character.
* Return the object containing character counts.
