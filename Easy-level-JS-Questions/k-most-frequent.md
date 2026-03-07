# Top K Frequent Elements

## Problem

Given an array of integers, return the **k most frequent elements**.

Example:

```javascript
input = [1,2,2,3,3,3,3,4,4,4]
k = 2
```

## Expected Output

```
[3,4]
```

Explanation:

```
1 → 1 time
2 → 2 times
3 → 4 times
4 → 3 times
```

Top 2 frequent elements:

```
3, 4
```

---

# Approach

Steps:

1. Count frequency of each element
2. Convert object to array using `Object.entries`
3. Sort elements based on frequency
4. Return top `k` elements

---

# Solution

```javascript
let input = [1,2,2,3,3,3,3,4,4,4]
let k = 2;

let topKfreq = (arr,k) => {

    let res = {}

    for(let ar of arr){
        res[ar] = (res[ar] || 0) + 1
    }

    let sort = Object.entries(res)
        .sort((a,b)=> b[1] - a[1])

    return sort.slice(0,k).map(x => Number(x[0]))
}

console.log(topKfreq(input,k))
```

---

# Output

```
[3,4]
```

---

# Time Complexity

```
O(N log N)
```

Where:

```
N = number of elements
```

Reason:

```
Sorting operation
```

---

# Space Complexity

```
O(N)
```

Used for frequency map.

---

# Key Concepts

- HashMap / Object for frequency counting
- Sorting
- Top K selection
- Array transformation

---

# Interview Explanation

In an interview you can say:

```
First I count the frequency of each number using a HashMap.
Then I convert it to an array and sort by frequency.
Finally I return the top K elements.
```

---

# Example Walkthrough

Input:

```
[1,2,2,3,3,3,3,4,4,4]
```

Frequency Map:

```
{
1:1,
2:2,
3:4,
4:3
}
```

Sorted:

```
[
[3,4],
[4,3],
[2,2],
[1,1]
]
```

Top 2:

```
[3,4]
```

---
