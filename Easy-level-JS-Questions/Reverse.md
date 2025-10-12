# JavaScript String Reverse Utilities

```javascript
// 1. Reverse a String (Using Loop)
const reverseStringLoop = (str) => {
    let reversed = '';
    for (let i = str.length - 1; i >= 0; i--) {
        reversed += str[i];
    }
    return reversed;
}

console.log(reverseStringLoop('test')); // Output: 'tset'

// 2. Reverse a String (Using Built-in Functions)
const reverseString = (str) => {
    return str.split('').reverse().join('');
}

console.log(reverseString('Mohan')); // Output: 'nahoM'

