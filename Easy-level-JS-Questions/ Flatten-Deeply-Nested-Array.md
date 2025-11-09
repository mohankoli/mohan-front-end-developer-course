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
```

---

## ✅ 4. Using `reduce()` + Recursion

```js
const flattenReduce = (arr) =>
  arr.reduce((acc, item) => 
    Array.isArray(item) ? acc.concat(flattenReduce(item)) : acc.concat(item)
  , []);

console.log(flattenReduce(sampleData));
```

---

## ✅ 5. Using Stack (Iterative Flattening)

```js
const flattenIterative = (arr) => {
  let stack = [...arr];
  let result = [];

  while (stack.length) {
    let next = stack.pop();
    if (Array.isArray(next)) {
      stack.push(...next); 
    } else {
      result.push(next);
    }
  }

  return result.reverse();
};

console.log(flattenIterative(sampleData));
```

---

## ✅ 6. Using Generator Function

```js
function* flattenGen(arr) {
  for (let item of arr) {
    if (Array.isArray(item)) {
      yield* flattenGen(item);
    } else {
      yield item;
    }
  }
}

console.log([...flattenGen(sampleData)]);
```

---

## ✅ 7. Using JSON.stringify Hack (Not recommended)

```js
let res = JSON.stringify(sampleData)
  .replace(/\[|\]/g, "")
  .split(",")
  .map(Number);

console.log(res);
```

⚠️ Loses data & type safety.

---

## ✅ Summary Table

| Method | Safe? | Readability | Notes |
|--------|-------|-------------|-------|
| `.flat()` | ✅ | ✅ | Best built‑in |
| Recursive | ✅ | ✅ | Most flexible |
| `reduce()` | ✅ | ✅ | Functional style |
| Iterative stack | ✅ | ✅ | No recursion limit |
| Generator | ✅ | ✅ | Lazy + elegant |
| String split | ❌ | ✅ | Type unsafe |
| JSON stringify | ❌ | ❌ | Not recommended |


