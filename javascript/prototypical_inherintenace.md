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

## 🧠 2.Example 
function Car(color) {
  this._color = color;
}

function ToyCar(color, price) {
  Car.call(this, color); // Inherit color property from Car
  this._price = price;
}

## 🧠 3. Example
```js
function Car(color) {
  this._color = color;
}

Car.prototype.getColor = function() {
  return this._color;
};

function ToyCar(color, price) {
  Car.call(this, color); // Reuse Car's constructor logic
  this._price = price;
}

// Inherit Car's prototype methods
ToyCar.prototype = Object.create(Car.prototype);

// Reset constructor reference
ToyCar.prototype.constructor = ToyCar;

ToyCar.prototype.getPrice = function() {
  return this._price;
};

const smallToy = new ToyCar('red', 500);
console.log(smallToy.getColor()); // "red"
console.log(smallToy.getPrice()); // 500


const smallToy = new ToyCar('red', 500);
console.log(smallToy._color); // "red"
console.log(smallToy._price); // 500




