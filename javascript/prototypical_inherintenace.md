# Function Constructor in JavaScript

## 🔹 Definition
A function constructor is a normal function used with the `new` keyword to create objects.

---

## 🧠 Example
```js
Function Constructor Example
function Car(color) {
  this._color = color;
}

const blueCar = new Car('blue');
console.log(blueCar._color); // "blue"
