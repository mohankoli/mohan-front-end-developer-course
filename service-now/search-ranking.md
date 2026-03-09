# Document Ranking using Term Frequency

## Problem
Given a list of documents and a query word, rank the documents based on how many times the query appears.

Return documents sorted by frequency of the query word.

---

## Example

Input

docs = [
 {id:1, text:"search engine search"},
 {id:2, text:"ai search system"},
 {id:3, text:"document search retrieval search search"}
]

query = "search"

---

## Approach

1. Iterate through all documents
2. Split document text into words
3. Count occurrences of the query word
4. Return document id with count
5. Sort documents by count (descending)
6. Filter documents with count > 1

---

## JavaScript Implementation

```javascript
let docs = [
 {id:1, text:"search engine search"},
 {id:2, text:"ai search system"},
 {id:3, text:"document search retrieval search search"}
]

let query = "search"

let SearchingToRanking = (arr, query) => {
    
   let res = arr.map((doc)=> {
       let words = doc.text.split(' ')
       let count = 0

       for(let word of words){
           if(word === query){
               count++
           }
       }

       return {id:doc.id, count}
   })
   .sort((a,b)=> b.count - a.count)
   .filter((doc)=> doc.count > 1)

   return res
}

console.log(SearchingToRanking(docs,query))
