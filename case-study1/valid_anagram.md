# Anagram Check (Using Hashmap)

## 🧩 Problem

Check whether two strings are anagrams of each other.

---

## ✅ Code (Python)

```python id="a1n4gm"
def anagaram():
    s = 'aab'
    t = 'aaa'  # Example case

    if len(s) != len(t):
        return False

    charmap = {}

    # Count characters from string s
    for ch in s:
        charmap[ch] = charmap.get(ch, 0) + 1

    print(charmap)

    # Validate using string t
    for ch in t:
        if ch not in charmap:
            return False
        else:
            if charmap[ch] == 0:
                return False
            else:
                charmap[ch] -= 1

    return True
```

---

## 🧠 Explanation

### Step 1: Build Frequency Map

```python id="f1reqm"
for ch in s:
    charmap[ch] = charmap.get(ch, 0) + 1
```

For:

```python id="inp01"
s = "aab"
```

👉 `charmap` becomes:

```python id="map01"
{'a': 2, 'b': 1}
```

---

### Step 2: Traverse String `t`

```python id="step2"
for ch in t:
```

We reduce frequency while checking validity.

---

## ❗ Key Condition

```python id="cond01"
if charmap[ch] == 0:
    return False
```

👉 Meaning:

* Character exists
* But all occurrences are already used

---

## 💥 Example Walkthrough

### Input:

```python id="inp02"
s = "aab"
t = "aaa"
```

### Process:

```python id="proc01"
Initial map: {'a': 2, 'b': 1}

t[0] = 'a' → count becomes 1
t[1] = 'a' → count becomes 0
t[2] = 'a' → ❌ count already 0 → return False
```

---

## ❌ Output

```python id="out01"
False
```

---

## ⚡ Complexity

* Time Complexity: **O(n)**
* Space Complexity: **O(n)**

---

## 🔥 Cleaner Version

```python id="clean01"
def is_anagram(s, t):
    if len(s) != len(t):
        return False

    charmap = {}

    for ch in s:
        charmap[ch] = charmap.get(ch, 0) + 1

    for ch in t:
        if ch not in charmap or charmap[ch] == 0:
            return False
        charmap[ch] -= 1

    return True
```

---
