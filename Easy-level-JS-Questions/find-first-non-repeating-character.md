# 🧩 Find First Non-Repeating Character in a String

## 🧠 Problem Statement
Given a string, find the **first non-repeating character** in it.  
Return the character if found, otherwise return `null`.

---

## 💡 Example
**Input:**  
`"aabbccdghhgac"`

**Output:**  
`"d"`
---

## 🧑‍💻 Code

```js
let findNonRepeatChar = (str) => {
    let strMap = {};
    
    // Count frequency of each character
    for (let char of str) {
        strMap[char] = (strMap[char] || 0) + 1;
    }

    // Find first non-repeating character
    for (let i = 0; i < str.length; i++) {
        if (strMap[str[i]] === 1) {
            return str[i];
        }
    }

    return null; // If all are repeated
}

console.log(findNonRepeatChar('aabbccdghhgac')); // Output: 'd'
