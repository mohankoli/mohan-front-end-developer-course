# Search Documents by Keyword

## Problem

Given a list of documents, return the documents that contain a specific **search query**.

---

## Example

Input

```javascript
let docs = [
 {id:1, text:"search engine design"},
 {id:2, text:"ai powered search"},
 {id:3, text:"document retrieval system"}
]

query = "retrieval"
```

Expected Output

```javascript
[
 {id:3, text:"document retrieval system"}
]
```

---

# Approach

Steps:

1. Traverse through each document.
2. Check if the document text contains the query string.
3. If it contains the query, include it in the result.
4. Return all matching documents.

---

# Solution

```javascript
let docs = [
 {id:1, text:"search engine design"},
 {id:2, text:"ai powered search"},
 {id:3, text:"document retrieval system"}
]

let findDoc = (arr,query) => {

    let res = arr.filter((item) => {

        if(item.text.includes(query)){
            return item
        }

    })

    return res
}

console.log(findDoc(docs,'retrieval'))
```

---

# Output

```javascript
[
 { id: 3, text: "document retrieval system" }
]
```

---

# Example Walkthrough

Documents

```
1 → search engine design
2 → ai powered search
3 → document retrieval system
```

Query

```
retrieval
```

Matching document

```
document retrieval system
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

- Array filtering
- String search using `includes`
- Basic search retrieval

---

# Interview Explanation

You can explain it like this:

```
I iterate through all documents and check if the document text contains the query string using includes().
If a document matches the query, I include it in the result list.
```

---

# Possible Improvement (Search Systems)

For large document collections, search engines use:

```
Inverted Index
```

Example

```
search → [doc1, doc2]
engine → [doc1]
retrieval → [doc3]
```

This allows faster search than scanning all documents.

---
