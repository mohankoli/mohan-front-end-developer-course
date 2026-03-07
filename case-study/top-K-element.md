# Vector Similarity Search (Semantic Search)

## Problem

You are building a simple **semantic search system**.

Each document has a **vector embedding**.  
A user query is also converted into a **vector embedding**.

Your task is to:

1. Compute the **similarity score** between the query vector and each document vector.
2. Rank the documents by similarity.
3. Return the **top K most similar documents**.

---

## Input

```javascript
documents = [
 {id:1, vector:[0.2,0.8,0.5]},
 {id:2, vector:[0.9,0.1,0.2]},
 {id:3, vector:[0.3,0.7,0.6]}
]

query = [0.25,0.75,0.55]

k = 3

function search(documents, query, k) {

    let results = documents.map(doc => {

        let score = 0

        for(let i = 0; i < query.length; i++) {
            score += doc.vector[i] * query[i]
        }

        return { id: doc.id, score }
    })

    results.sort((a,b) => b.score - a.score)

    return results.slice(0,k)
}

console.log(search(documents, query, k))
