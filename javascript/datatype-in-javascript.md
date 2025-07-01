### JavaScript Data Types

In JavaScript, data types represent the different kinds of values that can be stored and manipulated in a program.

JavaScript has two main categories of data types:

```
JavaScript Data Types
├── Primitive
│   ├── Number
│   ├── String
│   ├── Boolean
│   ├── Undefined
│   ├── Null
│   ├── Symbol
│   └── BigInt
└── Non-Primitive (Reference)
    ├── Object
    │   ├── Array
    │   ├── Function
    │   └── Date, RegExp, etc.
```

### ❓ Why are `Symbol` and `BigInt` tricky?

- `Symbol` (ES6) is rarely used by beginners and is mainly for creating **unique keys** in objects.
- `BigInt` (ES2020) is newer and is used for handling **very large integers** beyond the safe limit of `Number`.

🧪 **Example:**

```js
console.log(typeof Symbol("id")); // "symbol"
console.log(typeof 10n);          // "bigint"
```

