# Check if Two Strings Are Anagrams

```javascript
const isAnagram = (str1, str2) => {
    if (str1.length === str2.length) {
    let first = str1.toLowerCase().split('').sort().join();
    let second = str2.toLowerCase().split('').sort().join();
    return first === second;
    }
    return false;
}


console.log(isAnagram('listen', 'silent'))
