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

## 🔹 `apply()` – Short Note

- `apply()` is used to borrow a function from one object and use it for another.
- Just like `call()`, but arguments are passed as an **array**.
- Useful for dynamic or unknown number of arguments.

### 🧪 Example:
```js
const obj = { name: 'Mohan', age: 35 };

let setProfile = function(name, age) {
    this.name = name;
    this.age = age;
};

let params = ['Jill', 30];

// Call function with obj as `this` and array as arguments
setProfile.apply(obj, params);

console.log(obj); // { name: 'Jill', age: 30 }


