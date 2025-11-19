#  capitalizeWords

```javascript
// Simple capitalizeWords program
let capitalizeWords = (sentence) => {
    let words = sentence.split(' ');
    
    let output = words.map((word) => {
        return word.charAt(0).toUpperCase() + word.slice(1);
    }).join(' ');
    
    return output;
}

console.log(capitalizeWords("hello world this is react"));
