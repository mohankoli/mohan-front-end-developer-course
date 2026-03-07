# Document Search Processing

## Problem

Given a block of text containing multiple sentences, convert it into documents with unique IDs and search for documents containing a specific query word.

---

## Example Input

```javascript
const text = "AI powered search services platform. Angular frontend development. Semantic search and retrieval system."

query = "platform"
```

---

## Expected Output

```javascript
[
 { docId: 1, text: "AI powered search services platform" }
]
```

---

# Approach

Steps:

1. Split the text into sentences using `"."`.
2. Generate a unique `docId` for each sentence.
3. Store sentences as document objects.
4. Filter documents that contain the search query.
5. Return matching documents.

---

# Solution

```javascript
const text = "AI powered search services platform. Angular frontend development. Semantic search and retrieval system.";

let DocumentProcessing = (query) => {
    let arr = text.split('.');
    return genrateDocId(arr,query);
}

let genrateDocId = (input, query) => {

    let document = [];
    let count = 0;

    for(let doc of input){
        count++;

        if(doc !== ''){
            document.push({
                docId: count,
                text: doc.trim()
            })
        }
    }

    let res = document.filter(item =>
        item.text.includes(query)
    )

    return res;
}

console.log(DocumentProcessing('platform'));
```

---

# Example Walkthrough

Text

```
AI powered search services platform.
Angular frontend development.
Semantic search and retrieval system.
```

After splitting

```
[
 "AI powered search services platform",
 " Angular frontend development",
 " Semantic search and retrieval system",
 ""
]
```

After generating documents

```
[
 {docId:1, text:"AI powered search services platform"},
 {docId:2, text:"Angular frontend development"},
 {docId:3, text:"Semantic search and retrieval system"}
]
```

Search query

```
platform
```

Matching document

```
docId:1
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
O(N)
```

Because we store document objects.

---

# Key Concepts

- Text processing
- Document indexing
- Filtering documents by query
- Simple search retrieval

---

# Interview Explanation

You can explain this solution like:

```
First I split the text into sentences.
Then I assign a document ID to each sentence.
After that I search for documents containing the query string.
Finally I return the matching documents.
```

---

# Possible Improvement

Real search engines do not scan every document. Instead they build an **inverted index**.

Example

```
search → [doc1, doc3]
platform → [doc1]
retrieval → [doc3]
```

This allows faster search.

---
