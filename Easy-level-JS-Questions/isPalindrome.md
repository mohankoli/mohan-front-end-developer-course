# Check if a String is a Palindrome

```javascript
// Simple Palindrome Check
let isPalindrome = (str) => {
    let reversedStr = str.split('').reverse().join('');
    return str === reversedStr; 
}

console.log(isPalindrome('madam')); // Output: true
