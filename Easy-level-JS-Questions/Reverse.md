# Reverse a String in JavaScript

```javascript
const reverseString = (str) => {
    let reversed = '';
    for (let i = str.length - 1; i >= 0; i--) {
        reversed += str[i];
    }
    console.log(reversed);
}

console.log(reverseString('test')); // Output: 'tset'
