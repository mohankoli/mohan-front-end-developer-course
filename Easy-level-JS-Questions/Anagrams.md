# Check if Two Strings Are Anagrams

```javascript
const checkAnagram = (str1, str2) => {
    if (str1.length === str2.length) {
        let firstString = str1.split('').sort().join('');
        let secondString = str2.split('').sort().join('');
        return firstString === secondString;
    }
    return false;
}

console.log(checkAnagram('dom', 'mod')); // Output: true

