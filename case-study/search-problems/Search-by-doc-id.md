# Document Search by Keyword

## Problem

Given a list of documents, return the **document IDs that contain a given search query**.

---

## Input

```javascript
docs = [
 {id:1, text:"search engine design"},
 {id:2, text:"ai powered search"},
 {id:3, text:"document retrieval system"}
]

query = "ai"
```

---

## Expected Output

```javascript
{
 ai: [2]
}
```

Explanation

```
Document 2 contains the word "ai".
```

---

# Approach

Steps:

1. Create a result object where the key is the query.
2. Iterate through all documents.
3. Check if the document text contains the query using `includes()`.
4. If matched, push the document `id` into the result array.
5. Return the result object.

---

# Solution

```javascript
let docs = [
 {id:1, text:"search engine design"},
 {id:2, text:"ai powered search"},
 {id:3, text:"document retrieval system"}
]

let findDoc = (arr,query) => {

    let fRes = {[query]:[]}

    arr.forEach((item) => {

        if(item.text.includes(query)){
            fRes[query].push(item.id)
        }

    })

    return fRes
}

console.log(findDoc(docs,"ai"))
```

---

# Example Walkthrough

Query

```
ai
```

Check documents

```
doc1 → "search engine design" ❌
doc2 → "ai powered search" ✅
doc3 → "document retrieval system" ❌
```

Result

```
{
 ai: [2]
}
```

---

# Time Complexity

```
O(N)
```

Where

```
N = number of documents
```

Because each document is scanned once.

---

# Space Complexity

```
O(K)
```

Where

```
K = number of matched documents
```

---

# Key Concepts

- Document search
- Keyword matching
- Array traversal
- Dynamic object keys

---

# Interview Explanation

You can explain it like this:

```
I iterate through each document and check if the document text contains the query string.
If it matches, I store the document ID in the result object.
Finally I return the list of matching document IDs.
```

---

# Possible Optimization

For large-scale search systems, scanning all documents is inefficient.

Instead we build an **Inverted Index**:

```
search → [1,2]
engine → [1]
ai → [2]
retrieval → [3]
```

Then searching becomes:

```
O(1) lookup
```

instead of scanning all documents.

---
