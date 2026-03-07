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
