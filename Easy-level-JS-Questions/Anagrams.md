Check if Two Strings Are Anagrams

// Function to check if two strings are anagrams
const checkAnagrams = (str1, str2) => {
  const firstString = str1.split('').sort().join('');
  const secondString = str2.split('').sort().join('');
  return firstString === secondString;
};

// Example usage
console.log(checkAnagrams('DOM', 'MOD'));   // true
console.log(checkAnagrams('test', 'etts')); // true
console.log(checkAnagrams('rat', 'cat'));   // false
