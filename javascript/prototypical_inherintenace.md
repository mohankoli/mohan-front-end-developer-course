# Function Constructor in JavaScript

## 🔹 Definition

Every JavaScript object has a hidden parent object called `[[Prototype]]`.


# 🧩 Function Constructor with Inheritance using Object.create()

## 🔹 Definition
## Prototype Chain
```text
child object
   ↓
prototype (parent)
   ↓
prototype of prototype
   ↓
null

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
function Person(name) {
  this.name = name;
}

// Method stored on prototype
Person.prototype.sayHello = function () {
  console.log("Hello, " + this.name);
};

const p1 = new Person("Mohan");

p1.sayHello(); // method found via prototype




