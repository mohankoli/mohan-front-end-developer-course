## 🔹 `call()`, `apply()`, `bind()` – Short Comparison

| Method   | Use Case                               | Arguments              | Invoked Immediately? | Example Output                       |
|----------|----------------------------------------|------------------------|-----------------------|--------------------------------------|
| `call()` | Borrow function, pass args one by one  | Arguments separately   | ✅ Yes                | `obj = { name: 'peter', age: 20 }`   |
| `apply()`| Same as `call()`, but args in array    | Arguments in array     | ✅ Yes                | `obj = { name: 'jill', age: 30 }`    |
| `bind()` | Create new function with fixed `this`  | Arguments separately   | ❌ No (call later)    | `obj = { name: 'romeo', age: 21 }`   |

---

### 🧪 Combined Code Example:
```js
const obj = {
  name: "john", 
  age: 20
};

const setName = function(name) {
  this.name = name;
};

// ✅ Using call()
setName.call(obj, 'peter');
console.log(obj); // { name: 'peter', age: 20 }

const setProfile = function(name, age) {
  this.name = name;
  this.age = age;
};

let params = ['jill', 30];

// ✅ Using apply()
setProfile.apply(obj, params);
console.log(obj); // { name: 'jill', age: 30 }

// ❌ Using bind() (returns a new function)
const boundObj = setProfile.bind(obj);
boundObj('romeo', 21);
console.log(obj); // { name: 'romeo', age: 21 }
