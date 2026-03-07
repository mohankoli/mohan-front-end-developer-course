# Search Result Ranking by Keyword Frequency

## Problem

Given a list of documents and a query word, rank the documents based on how many times the query appears in each document.

Documents with higher occurrences of the query should appear first.

---

# Example Input

```javascript
docs = [
 {id:1, text:"search engine search"},
 {id:2, text:"ai search system"},
 {id:3, text:"document retrieval"}
]

query = "search"
```

---

# Expected Output

```javascript
[
 { id:1, count:2 },
 { id:2, count:1 }
]
```

Explanation

```
doc1 → "search engine search" → 2 occurrences
doc2 → "ai search system" → 1 occurrence
doc3 → "document retrieval" → 0 occurrences
```

Documents with `0` matches are removed.

---

# Approach

Steps:

1. Iterate through all documents.
2. Split document text into words.
3. Count occurrences of the query word.
4. Return document ID and count.
5. Remove documents with zero matches.
6. Sort documents by count in descending order.

---

# Solution

```javascript
let docs = [
 {id:1, text:"search engine search"},
 {id:2, text:"ai search system"},
 {id:3, text:"document retrieval"}
]

let query = "search"

let SearchingToRanking = (arr, query) => {

    let res = arr.map((doc) => {

        let words = doc.text.split(" ")
        let count = 0

        words.forEach(word => {
            if(word === query){
                count++
            }
        })

        return { id: doc.id, count }
    })

    return res
        .filter(doc => doc.count > 0)
        .sort((a,b)=> b.count - a.count)
}

console.log(SearchingToRanking(docs,query))
```

---

# Output

```javascript
[
 { id:1, count:2 },
 { id:2, count:1 }
]
```

---

# Time Complexity

```
O(N × W)
```

Where:

```
N = number of documents
W = number of words per document
```

---

# Space Complexity

```
O(N)
```

For storing ranking results.

---

# Key Concepts

- Text processing
- Keyword frequency counting
- Document ranking
- Sorting results by relevance

---

# Real Search Engine Concept

This is a simplified version of **search relevance ranking**.

Real search engines use advanced ranking algorithms like:

```
TF-IDF
BM25
Semantic embeddings
Vector similarity
```

---
