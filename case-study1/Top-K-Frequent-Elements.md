# 🧩 Top K Frequent Elements (Using HashMap + get)

## 🔹 Problem

Given an array of integers `nums` and an integer `k`, return the **k most frequent elements**.

---

## 🔹 Example

```python
nums = [1,1,1,2,2,3]
k = 2

Output: [1,2]
```

---

## 🔹 Approach

1. Use a **hashmap (dictionary)** to count frequency
2. Sort elements based on frequency
3. Return first `k` elements

---

## 🔹 Code

```python
def topKFrequent(nums, k):
    freq = {}
    
    # Step 1: Count frequency
    for i in nums:
        freq[i] = freq.get(i, 0) + 1
    
    # Debug: print frequency map
    print(freq)
    
    # Step 2: Sort based on frequency (descending)
    result = sorted(freq, key=freq.get, reverse=True)
    
    # Step 3: Return top k elements
    return result[:k]


# Test
nums = [1,1,1,2,2,3]
k = 2
print(topKFrequent(nums, k))
```

---

## 🔹 Explanation

### Frequency Map

```
{1: 3, 2: 2, 3: 1}
```

### Sorted by Frequency

```
[1, 2, 3]
```

### Top K Elements

```
[1, 2]
```

---

## 🔹 Time Complexity

* **O(n log n)** → due to sorting

---

## 🔹 Space Complexity

* **O(n)** → hashmap storage

---

## 🔹 Key Concept

```python
freq[i] = freq.get(i, 0) + 1
```

* If key exists → increment
* If not → start from 0

---

## 🔹 Interview Tip 💡

> “I used a hashmap to count frequency and sorted based on frequency to get top k elements.”

---

## 🔹 Optimization (Follow-up 🚀)

* Heap → **O(n log k)**
* Bucket Sort → **O(n)**

---

## 🔹 Final Verdict

* ✅ Easy to understand
* ✅ Interview accepted
* ⚠️ Can be optimized further

---
