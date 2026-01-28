## Limit duplicates (max 2 occurrences)

```js
const limitDuplicates = (arr) => {
  let output = [];
  let countMap = {};

  for (let i = 0; i < arr.length; i++) {
    countMap[arr[i]] = (countMap[arr[i]] || 0) + 1;

    if (countMap[arr[i]] <= 2) {
      output.push(arr[i]);
    }
  }

  return output;
};

const arr = [9,1,1,1,1,1,1,2,2,3,3,3,4,4,4,5,5,5,10];
console.log(limitDuplicates(arr));
// [9,1,1,2,2,3,3,4,4,5,5,10]
