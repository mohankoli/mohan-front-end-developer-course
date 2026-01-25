class LRU {
  constructor(capacity) {
    this.capacity = capacity;
    this.store = [];
  }

  set(item) {
    let index = this.store.indexOf(item);

    if (index !== -1) {
      this.store.splice(index, 1);
    } else if (this.store.length === this.capacity) {
      this.store.pop();
    }

    this.store.unshift(item);
    return this.store;
  }
}

let lru = new LRU(3);
console.log(lru.set(1)); // [1]
console.log(lru.set(2)); // [2,1]
console.log(lru.set(3)); // [3,2,1]

console.log(lru.set(2)); // [2,3,1]


// Usage Example

let lru = new LruCache(3);

lru.setItem(1);
lru.setItem(2);
lru.setItem(3);
console.log(lru.cache); // [3, 2, 1]

lru.setItem(2);
console.log(lru.cache); // [2, 3, 1]

lru.setItem(4);
console.log(lru.cache); // [4, 2, 3] → 1 evicted (LRU)
```

