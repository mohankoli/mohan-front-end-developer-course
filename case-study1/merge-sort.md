# Merge Sort (Divide and Conquer)

## 🧩 Problem

Sort an array using the **Merge Sort algorithm**.

---

## 🧠 Concept

Merge Sort follows **Divide and Conquer**:

1. **Divide** → Split array into halves
2. **Conquer** → Recursively sort both halves
3. **Merge** → Combine sorted halves

---

## 🔍 Example

```text
Input:  [4, 3, 2, 1]

Divide:
[4,3] [2,1]
[4] [3] [2] [1]

Merge:
[4] + [3] → [3,4]
[2] + [1] → [1,2]

Final Merge:
[3,4] + [1,2] → [1,2,3,4]
```

---

## ✅ Code (Python)

```python id="ms01"
def merge_sort(arr):
    if len(arr) <= 1:
        return arr

    mid = len(arr) // 2

    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])

    return merge(left, right)


def merge(left, right):
    result = []
    i = j = 0

    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1

    # Add remaining elements
    result.extend(left[i:])
    result.extend(right[j:])

    return result


# Example
arr = [4, 3, 2, 1]
print(merge_sort(arr))
```

---

## ⚡ Complexity

* **Time Complexity:** O(n log n)
* **Space Complexity:** O(n)

---

## 🎯 Key Points

* Stable sorting algorithm ✅
* Works well for large datasets
* Uses extra space (not in-place)

---

## 🔥 Interview Notes

* You should know:

  * How merge works (important)
  * Time complexity derivation
* Full implementation rarely asked
* Merging logic is **very commonly asked**

---

## 🚀 Summary

* Divide array → recursively sort
* Merge sorted halves
* Efficient and predictable performance

---
