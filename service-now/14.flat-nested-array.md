https://www.youtube.com/watch?v=AoIizkhJoo4

# Array Flattening in JavaScript — All Variants

## ✅ Sample Data
```js
let sampleData = [1, 2, [3, 4, [5]], 6, 7, [8]];
```

---

## ✅ 1. Built‑in Method: `Array.prototype.flat()`

```js
let res = sampleData.flat(2);
console.log(res); // [1,2,3,4,5,6,7,8]
```

---

## ✅ 2. Convert to String + Split (Not Recommended)

```js
let res = sampleData.toString().split(',').map(Number);
console.log(res); // [1,2,3,4,5,6,7,8]
```

⚠️ **Issues:** Loses type info (objects, null become strings)

---

## ✅ 3. Recursive Function (Custom)

```js
let flatten = (array) => {
  let res = [];
  array.forEach((item) => {
    if (Array.isArray(item)) {
      res.push(...flatten(item));
    } else {
      res.push(item);
    }
  });
  return res;
};

console.log(flatten(sampleData));
