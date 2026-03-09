# Group Anagrams (JavaScript)

## Problem
Given an array of strings, group the **anagrams** together.

Two words are anagrams if they contain the **same characters in different order**.

---

## Example

Input

```
["eat","tea","tan","ate","nat","bat"]
```

Output

```
[
  ["eat","tea","ate"],
  ["tan","nat"],
  ["bat"]
]
```

Explanation

```
eat, tea, ate → same characters
tan, nat → same characters
bat → no matching anagram
```

---

# Approach

1. Iterate through each word in the array.
2. Sort the characters of the word.
3. Use the sorted word as a **key in a hashmap**.
4. Store original words inside the same key.
5. Return the grouped values.

Sorted strings act as **unique identifiers for anagrams**.

Example

```
eat → aet
tea → aet
ate → aet
```

---

# JavaScript Solution

```javascript
let Input = ["eat","tea","tan","ate","nat","bat"]

let groupAnagram = (arr) => {

    let map = {}

    for(let word of arr){

        let key = word.split('').sort().join('')

        if(!map[key]){
            map[key] = []
        }

        map[key].push(word)

    }

    return Object.values(map)
}

console.log(groupAnagram(Input))
```

---

# Output

```
[
  ["eat","tea","ate"],
  ["tan","nat"],
  ["bat"]
]
```

---

# Time Complexity

```
O(n * k log k)
```

Where:

```
n = number of words
k = length of each word
```

Sorting each word takes `k log k`.

---

# Space Complexity

```
O(n)
```

For storing groups in the hashmap.

---

# Key Idea

```
Sort characters of each word
→ use sorted word as hashmap key
→ group words with same key
```
