# 19. Chunk an array into subarrays of size k.

```javascript
function chunkArray(arr, k) {
  let result = [];

  while (arr.length) {
    result.push(arr.splice(0, k));
  }

  return result;
}

console.log(chunkArray([1,2,3,4,5,6,7], 3));
// Output: [[1,2,3], [4,5,6], [7]]
