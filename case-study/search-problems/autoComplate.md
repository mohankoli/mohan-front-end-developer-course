# Autocomplete using Prefix Search (JavaScript)

## Problem
Given a list of words and a prefix, return all words that start with the given prefix.

## Example

Input

words = ["search","service","server","system","design"]  
prefix = "ser"

Output

["search","service","server"]

---

## JavaScript Solution

```javascript
let words = ["search","service","server","system","design"]

let prefix = "ser"

let autoComplate = (words, prefix) => {
    let result = words.filter((item) => item.startsWith(prefix));
    return result;
}

console.log(autoComplate(words, prefix));
```

---

## Explanation

1. `filter()` iterates through each word in the array.
2. `startsWith(prefix)` checks if the word begins with the given prefix.
3. Matching words are stored in `result`.
4. Return the filtered array.

---

## Time Complexity

O(n)

Where `n` = number of words.

Each word is checked once.

---

## Space Complexity

O(k)

Where `k` = number of matching words.

---

## Example Walkthrough

Array:

["search","service","server","system","design"]

Prefix:

"ser"

Matching words:

search  
service  
server
