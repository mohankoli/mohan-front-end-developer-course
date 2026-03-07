# Longest Substring Without Repeating Characters

## Problem

Given a string `s`, find the **length of the longest substring without repeating characters**.

---

## Example

Input

```javascript
s = "abcabcefbb"
```

Output

```
5
```

Explanation

The longest substring without repeating characters is:

```
abcef
```

Length

```
5
```

---

# Approach (Simple Brute Force)

Steps:

1. Convert the string into an array.
2. Start from each character in the array.
3. Build a temporary substring (`temp` array).
4. If a duplicate character is found using `indexOf`, stop expanding the substring.
5. Track the maximum substring length.

---

# Solution

```javascript
function longestSubstring(s){

    let arr = s.split("")
    let max = 0
    
    for(let i = 0; i < arr.length; i++){

        let temp = []

        for(let j = i; j < arr.length; j++){

            if(temp.indexOf(arr[j]) !== -1){
                break
            }

            temp.push(arr[j])

            max = Math.max(max, temp.length)
        }
    }

    return max
}

console.log(longestSubstring("abcabcefbb"))
```

---

# Example Walkthrough

```
abcabcefbb
```

Start at index `0`

```
a
ab
abc
abca → duplicate → stop
```

Length = `3`

Start at index `3`

```
a
ab
abc
abce
abcef
```

Length = `5`

Maximum substring:

```
abcef
```

---

# Time Complexity

```
O(N²)
```

Because we check substrings starting from each index.

---

# Space Complexity

```
O(N)
```

Used for temporary array storage.

---

# Key Concepts

- Substring traversal
- Duplicate detection using `indexOf`
- Nested loops
- Tracking maximum length

---

# Interview Explanation

You can explain it like this:

```
I iterate through each character and build a temporary substring.
If a duplicate character appears, I stop expanding the substring.
I keep tracking the maximum substring length found.
```

---

# Possible Optimization

This solution can be improved using **Sliding Window technique**.

Optimized complexity:

```
O(N)
```

---
