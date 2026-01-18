# Remove Extra Parentheses Problem (JS Version)

## Problem
Given a string containing letters and parentheses, remove invalid parentheses and return a valid string with minimum removals.

---

## Your Approach (First Pass Implemented)
This implementation removes extra closing `)` parentheses.

```js
let input = "lee(t(c)o)de)";

let RemoveExtraParenthis = (input) => {
    let arr = input.split('');
    let count = 0;
    let result = [];
    for(let i=0;i<arr.length;i++) {
        if(arr[i] === '(') {
            count++;
            result.push(arr[i]);
        } else if(arr[i] === ')') {
            if(count>0) {
                count--;
                result.push(arr[i])
            }
        } else {
            result.push(arr[i]);
        }
    }
    return result.join('');
};
```

---

## What This Code Does

- Splits input string into characters
- Uses `count` to track open `(`
- Adds valid `(` to `result`
- For `)`:
  - adds only if there is a matching `(`
- Filters out extra `)`
- Joins array back to string

---

## Example

**Input**
```
"lee(t(c)o)de)"
```

**Output after first pass**
```
"lee(t(c)o)de"
```

---

## Next Step (Not Yet Implemented)

To handle cases like:
```
"((a)"
```
you still need a **second pass** to remove extra `(` from left.

---

## Complexity

**Time Complexity**
```
O(n)
```

**Space Complexity**
```
O(n)
```
