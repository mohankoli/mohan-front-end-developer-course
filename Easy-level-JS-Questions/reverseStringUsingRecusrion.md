### 📌 Reverse String Using Recursion (JavaScript)

```js
function reverseString(str) {
  if (str === "") return "";     // base case
  return reverseString(str.slice(1)) + str[0];
}

console.log(reverseString("hello")); // "olleh"

