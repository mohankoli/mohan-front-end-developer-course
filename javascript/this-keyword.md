# JavaScript `this` Binding Rules (Quick Guide)

`this` refers to **how a function is called**, not where it is written.

There are **4 rules** (priority order matters).

---

## 1️⃣ Default Binding
When a function is called **normally**.

```js
function show() {
  console.log(this);
}
show();
```

- Browser: `this` → `window`
- Strict mode: `this` → `undefined`

---

## 2️⃣ Implicit Binding
When a function is called as an **object method**.

```js
const user = {
  name: "Mohan",
  greet() {
    console.log(this.name);
  }
};

user.greet();
```

### Output
```
Mohan
```

👉 `this` points to the **object before the dot**.

---

## 3️⃣ Explicit Binding
When `this` is **manually set**.

### call / apply / bind

```js
function greet(city) {
  console.log(this.name, city);
}

const user = { name: "Mohan" };

greet.call(user, "Pune");
greet.apply(user, ["Pune"]);

const fn = greet.bind(user);
fn("Pune");
```

---

## 4️⃣ New Binding
When a function is called with `new`.

```js
function Person(name) {
  this.name = name;
}

const p1 = new Person("Mohan");
console.log(p1.name);
```

### Output
```
Mohan
```

👉 `this` points to the **newly created object**.

---

## ⭐ Priority Order (Important)
```
new
> explicit (call/apply/bind)
> implicit
> default
```

---

## ⚠️ Arrow Functions (Special Case)
Arrow functions **do not have their own `this`**.

```js
const obj = {
  name: "Mohan",
  greet: () => {
    console.log(this.name);
  }
};

obj.greet();
```

### Output
```
undefined
```

👉 Arrow functions take `this` from **lexical scope**.

---

## One-Line Interview Answer
**`this` is determined by how a function is called: default, implicit, explicit, or new binding, with arrow functions inheriting `this` from their surrounding scope.**
