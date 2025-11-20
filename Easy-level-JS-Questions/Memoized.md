# Memoized/ caching

```javascript
const cache = {};

function addTwo(x) {

  // check in cache using for..in
  for (let key in cache) {
    if (key == x) {
      console.log("From cache:", cache[key]);
      return cache[key];
    }
  }

  // compute if not in cache
  const result = x + 2;
  cache[x] = result;

  console.log("Calculated:", result);
  return result;
}

// Test
console.log(addTwo(5));   // Calculated: 7
console.log(addTwo(5));   // From cache: 7
console.log(addTwo(10));  // Calculated: 12
console.log(addTwo(10));  // From cache: 12
