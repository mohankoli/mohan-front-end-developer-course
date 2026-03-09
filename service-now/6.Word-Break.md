# Word Break (Using includes + replace)

## Problem
Given a string `s` and a dictionary `dict`, determine whether the string can be segmented into words present in the dictionary.

---

## Example

Input

```
s = "servicenowk"
dict = ["service","now"]
```

Expected Output

```
false
```

Explanation

```
servicenowk
= service + now + k
```

Since `"k"` is not in the dictionary, segmentation is **not possible**.

---

# JavaScript Solution (Using includes)

```javascript
function wordBreak(s, dict){

    for(let word of dict){

        if(s.includes(word)){

            s = s.replace(word,'')
            console.log(s)

        }

    }

    return s.length === 0
}

console.log(wordBreak("servicenowk",["service","now"]))
```

---

# Execution Steps

Initial string

```
servicenowk
```

Check dictionary word

```
service → found
```

Remove it

```
nowk
```

Next dictionary word

```
now → found
```

Remove it

```
k
```

Final string

```
k
```

Since the string is **not empty**, result is:

```
false
```

---

# Output

```
nowk
k
false
```

---

# Time Complexity

```
O(n * m)
```

Where

```
n = number of dictionary words
m = string length
```

---

# Limitation

This approach may fail for some cases because:

```
includes() checks the word anywhere in the string
```

But correct segmentation should check:

```
prefix → remaining string
```

Therefore, interviewers usually prefer:

```
startsWith() + recursion
or
Dynamic Programming
```
