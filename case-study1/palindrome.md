# Valid Palindrome (Two Pointer Approach)

## 🧩 Problem

Given a string `s`, check whether it is a **palindrome**.

A palindrome reads the same forward and backward.

---

## ✅ Code (Python)

```python id="pal123"
s = 'madam'

def valid_palindrome(s):
    n = s
    left = 0
    right = len(n) - 1

    while left < right:
        if s[left] != s[right]:
            return False
        left += 1
        right -= 1

    return True


print(valid_palindrome(s))
```

---

## 🧠 Explanation

* Use **two pointers**:

  * `left` → start of string
  * `right` → end of string

* Compare characters:

  * If mismatch → ❌ not palindrome
  * If all match → ✅ palindrome

---

## 🎯 Example

```python id="ex1"
s = "madam"
```

Steps:

```python id="steps1"
m == m ✅
a == a ✅
d == d ✅
```

👉 Output:

```python id="out1"
True
```

---

## ❌ Non-Palindrome Example

```python id="ex2"
s = "hello"
```

👉 `h != o` → return False

---

## ⚡ Complexity

* **Time Complexity:** O(n)
* **Space Complexity:** O(1)

---

## 🔥 Cleaner Version

```python id="cleanpal"
def valid_palindrome(s):
    left, right = 0, len(s) - 1

    while left < right:
        if s[left] != s[right]:
            return False
        left += 1
        right -= 1

    return True
```

---

## 🚀 Interview Tip

This is a classic:
👉 **Two Pointer Pattern**

Used in:

* Palindrome problems
* String reversal
* Sliding window variants

---
