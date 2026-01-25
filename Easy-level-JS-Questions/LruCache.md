# Simple LRU Cache (Array Based)

This LRU cache stores items in usage order using a single array.  
Most recently used (MRU) items are kept at the front.  
Least recently used (LRU) items are removed from the end.

---

## Code

```js
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
```

---

## Notes

- `unshift()` inserts as most recently used (MRU)
- `pop()` removes least recently used (LRU)
- Array ordering: `[MRU → ... → LRU]`
- Easy to explain in interviews


