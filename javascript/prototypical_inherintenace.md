# Function Constructor in JavaScript

## 🔹 Definition
A function constructor is a normal function used with the `new` keyword to create objects.

---

## 🧠 1.Example 
```js
Function Constructor Example
function Car(color) {
  this._color = color;
}

const blueCar = new Car('blue');
console.log(blueCar._color); // "blue"

## 🧠 2.Example 
function Car(color) {
  this._color = color;
}

function ToyCar(color, price) {
  Car.call(this, color); // Inherit color property from Car
  this._price = price;
}

const smallToy = new ToyCar('red', 500);
console.log(smallToy._color); // "red"
console.log(smallToy._price); // 500




