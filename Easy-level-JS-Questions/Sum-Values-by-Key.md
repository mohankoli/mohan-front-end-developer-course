# Sum Values by Key Across an Array of Objects

## Program

```js
const data = [
  { category: "food", amount: 100 },
  { category: "travel", amount: 200 },
  { category: "food", amount: 50 },
  { category: "shopping", amount: 300 },
  { category: "travel", amount: 150 }
];

let sumByKey = (data) => {
  let result = {};

  for (let i = 0; i < data.length; i++) {
    const key = data[i].category;
    const val = data[i].amount;

    result[key] = (result[key] || 0) + val;
  }

  return result;
};

console.log(sumByKey(data));
