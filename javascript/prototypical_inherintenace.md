# Function Constructor in JavaScript

## 🔹 Definition
A function constructor is a normal function used with the `new` keyword to create objects.


# 🧩 Function Constructor with Inheritance using Object.create()

## 🔹 Definition
A **function constructor** is a normal function used with the `new` keyword to create objects.  
Using **`Object.create()`**, we can make one constructor inherit another constructor’s prototype methods.

---


---

## 🧠 1.Example 
```js
Function Constructor Example
function Car(color) {
  this._color = color;
}

const blueCar = new Car('blue');
console.log(blueCar._color); // "blue"

## 🧠 3. Example
```js
// Parent constructor
function Car(color) {
  this._color = color;
}

// Add method to Car
Car.prototype.getColor = function() {
  return this._color;
};

// Child constructor
function ToyCar(color, price) {
  // Call Car to reuse its properties
  Car.call(this, color);
  this._price = price;
}

// Inherit methods from Car
ToyCar.prototype = Object.create(Car.prototype);

// Fix constructor reference
ToyCar.prototype.constructor = ToyCar;

// Add method to ToyCar
ToyCar.prototype.getPrice = function() {
  return this._price;
};

// Create an object
const smallToy = new ToyCar('red', 500);

// Access inherited and own properties
console.log(smallToy._color);      // "red"
console.log(smallToy._price);      // 500
console.log(smallToy.getColor());  // "red"
console.log(smallToy.getPrice());  // 500



