# Longest Substring Without Repeating Characters

## Problem
Given a string `s`, find the length of the **longest substring without repeating characters**.

### Example

Input

```
s = "abcabcbb"
```

Output

```
3
```

Explanation

```
Longest substring = "abc"
Length = 3
```

---

# JavaScript Solution

```javascript
function longestSubstring(s) {

    let left = 0
    let map = {}
    let max = 0

    for(let right = 0; right < s.length; right++) {
        
        if(map[s[right]] !== undefined && map[s[right]] >= left) {
            left = map[s[right]] + 1
        }
     
        map[s[right]] = right

        max = Math.max(max, right - left + 1)
    }

    return max
}

console.log(longestSubstring("abcabcbb"))
```

---

# Approach

This solution uses the **Sliding Window technique**.

- `left` → start of the window
- `right` → end of the window
- `map` → stores the last index of each character

Steps:

1. Expand the window using the `right` pointer.
2. If a duplicate character is found inside the current window:
   - Move `left` pointer after the previous occurrence.
3. Store the current character index in the map.
4. Update the maximum length.

---

# Time Complexity

```
O(n)
```

Each character is processed at most once.

---

# Space Complexity

```
O(n)
```

For storing characters in the hashmap.

---

# Key Idea

```
Expand → Check Duplicate → Move Left → Update Max Length
```
