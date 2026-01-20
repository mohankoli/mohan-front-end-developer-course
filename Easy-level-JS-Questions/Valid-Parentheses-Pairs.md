# Count Valid Parentheses Pairs

## Problem
Given a string containing letters and parentheses, count how many valid parentheses characters can be formed (each valid pair contributes 2 characters).

---

## Code

```js
let input = "lee(t(c)o)de)";

let findValidParenthis = (input) => {
   let count = 0;
   let validParenthis = 0;
   let arr = input.split('');
   for(let i=0;i<arr.length;i++) {
       if(arr[i]=== '(') {  
           count++;
       } else if(arr[i] === ')' && count>0) {
           count--;
           validParenthis = validParenthis + 2;
       }
   }
  return validParenthis;
};

console.log(findValidParenthis(input));
```

---

## Explanation

- `count` tracks how many `(` are available to match.
- When encountering `(` → increase `count`.
- When encountering `)`:
  - if there is an unmatched `(` (`count > 0`):
    - match them and add `2` to `validParenthis`.
- Only counts valid pairs, does not remove characters.

---

## Example

**Input**
```
"lee(t(c)o)de)"
```

**Output**
```
10
```

---

## Time Complexity
```
O(n)
```

## Space Complexity
```
O(1)
```

