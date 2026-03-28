# Contains Duplicate (Using Dictionary)

## 🧩 Problem

Given an array of integers `nums`, return **True** if any value appears at least twice. Otherwise, return **False**.

---

## ✅ Code (Python)

```python
nums = [1, 2, 3, 1]

# if item already present return True
# else return False

def contains_duplicate(nums):
    seen = {}

    for num in nums:
        if num in seen:
            return True
        seen[num] = 2  # mark as seen

    return False


print(contains_duplicate(nums))
```

---

## 🧠 Explanation

* We use a dictionary (`seen`) to track elements.
* Iterate through the array:

  * If element already exists in dictionary → duplicate found ✅
  * Otherwise → add it to dictionary

---

## 🎯 Example Walkthrough

```python
nums = [1, 2, 3, 1]
```

Steps:

```python
1 → {}
   add → {1:2}

2 → {1:2}
   add → {1:2, 2:2}

3 → {1:2,2:2}
   add → {1:2,2:2,3:2}

1 → already exists → return True
```

---

## ⚡ Complexity

* **Time Complexity:** O(n)
* **Space Complexity:** O(n)

---

## 🔥 Note

* Value `2` in dictionary is not important — it just marks presence.
* You can also store index instead:

```python
seen[num] = i
```

---

## 🚀 Cleaner Version

```python
def contains_duplicate(nums):
    seen = {}

    for i, num in enumerate(nums):
        if num in seen:
            return True
        seen[num] = i

    return False
```

---
