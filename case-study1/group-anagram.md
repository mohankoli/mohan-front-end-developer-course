# 🧩 Group Anagrams (Python)

## 🔹 Problem

Given an array of strings, group the anagrams together.

### Example

```python
Input: ["eat","tea","tan","ate","nat","bat"]

Output:
[
 ["eat","tea","ate"],
 ["tan","nat"],
 ["bat"]
]
```

---

## 🔹 Approach

* Use a hashmap (`defaultdict`)
* Sort each string → use it as a key
* Same sorted key → same group

---

## 🔹 Code

```python
from collections import defaultdict

def groupAnagrams(strs):
    ans = defaultdict(list)
    
    for s in strs:
        key = ''.join(sorted(s))   # create key by sorting
        ans[key].append(s)         # group anagrams
    
    return list(ans.values())


# Test
strs = ["eat","tea","tan","ate","nat","bat"]
print(groupAnagrams(strs))
```

---

## 🔹 Explanation

* `"eat" → "aet"`
* `"tea" → "aet"`
* `"ate" → "aet"`

👉 Same sorted string → grouped together

---

## 🔹 Data Structure Used

* `defaultdict(list)`

  * Automatically creates empty list for new keys
  * Avoids manual initialization

---

## 🔹 Time Complexity

* **O(n * k log k)**

  * n = number of strings
  * k = length of each string

---

## 🔹 Space Complexity

* **O(n)**

---

## 🔹 Optimization (Important for Interviews 🚀)

Instead of sorting:

* Use **character frequency (26 array)**
* Time improves to **O(n * k)**

---

## 🔹 Interview Tip 💡

> “I use sorting to create a canonical key for grouping anagrams. For optimization, I can use frequency counting to avoid sorting overhead.”

---
