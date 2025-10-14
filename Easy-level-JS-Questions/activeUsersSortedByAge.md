# Program: activeUsersSortedByAge.js

## Description
This program performs the following tasks on a given array of users:

1. Sorts users by age in descending order.
2. Filters only active users.
3. Returns an array of names of these active users.

## Code

```javascript
const users = [
  {
    id: 1,
    name: "Jack",
    isActive: true,
    age: 20,
  },
  {
    id: 2,
    name: "John",
    isActive: true,
    age: 18,
  },
  {
    id: 3,
    name: "Mike",
    isActive: false,
    age: 30,
  },
];

let names = users
    .sort((user1, user2) => user1.age < user2.age ? 1 : -1)
    .filter(user => user.isActive)
    .map(user => user.name);

console.log(names); // Output: ["Jack", "John"]
