# Valid Anagram

## Problem

Given two strings `s` and `t`, determine whether `t` is an **anagram** of `s`.

An **anagram** means both strings contain the **same characters with the same frequency**, but possibly in different order.

---

## Example

```javascript
s = "anagram"
t = "nagaram"
```

Output

```
true
```

Example 2

```javascript
s = "rat"
t = "car"
```

Output

```
false
```

---

# Approach

Steps:

1. Count frequency of characters in string `s`.
2. Traverse string `t`.
3. If a character is not found in the frequency map → return `false`.
4. Otherwise decrement the count.
5. If all characters match → return `true`.

---

# Solution

```javascript
let isAnagram = (s,t) => {

    let res = {}

    for(let char of s){
        res[char] = (res[char] || 0) + 1
    }

    for(let char of t){

        if(!res[char]){
            return false
        }

        res[char]--
    }

    return true
}

console.log(isAnagram("anagram","nagaram"))
```

---

# Example Walkthrough

```
s = "anagram"
```

Frequency Map

```
{
a:3,
n:1,
g:1,
r:1,
m:1
}
```

Traverse `t = "nagaram"`

```
n → decrease
a → decrease
g → decrease
a → decrease
r → decrease
a → decrease
m → decrease
```

All counts become `0`.

Result

```
true
```

---

# Time Complexity

```
O(N)
```

Where

```
N = length of string
```

---

# Space Complexity

```
O(1)
```

Because character set is limited (26 lowercase letters).

---

# Key Concepts

- HashMap / Object frequency counting
- String traversal
- Character matching

---

# Interview Explanation

You can explain it like this:

```
First I count the frequency of characters in the first string.
Then I iterate through the second string and decrease the counts.
If a character is missing or count becomes invalid, it is not an anagram.
If all characters match, the strings are anagrams.
```

---
