## 🔹 `call()` – Short Note

- `call()` is used to borrow a function from one object and use it for another.
- It sets the value of `this` inside the function.
- Arguments are passed one by one.

### 🧪 Example:
```js
const obj = { name: 'Mohan', age: 35 };

let setName = function(name) {
    this.name = name;
};

setName.call(obj, 'Shrikar');

console.log(obj); // { name: 'Shrikar', age: 35 }


