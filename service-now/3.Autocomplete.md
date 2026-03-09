# Autocomplete using Prefix Search

## Problem
Given a list of words and a prefix, return all words that start with the given prefix.

---

## Example

Input

words = ["search","service","server","system","design"]

prefix = "se"

Output

["search","service","server"]

---

## Approach

1. Iterate through the list of words
2. Check if each word starts with the prefix
3. Use `startsWith()` for prefix comparison
4. Return the matching words

---

## JavaScript Implementation

```javascript
let words = ["search","service","server","system","design"]
let prefix = "se"

let Autocomplete = (arr, prefix) => {
    let res = arr.filter((word) => word.startsWith(prefix))
    return res
}

console.log(Autocomplete(words,prefix))
