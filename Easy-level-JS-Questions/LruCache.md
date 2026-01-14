class LruCache {
    constructor(capacity) {
        this.capacity = capacity;
        this.cache = [];
    }

    isCapacityFull() {
        return this.cache.length >= this.capacity;
    }

    getItem(item) {
        return this.cache.indexOf(item);
    }

    setItem(item) {
        const index = this.getItem(item);

        if (index !== -1) {
            // Item exists → move to front (most recently used)
            this.cache.splice(index, 1);
            this.cache.unshift(item);
            return;
        }

        // New item
        if (this.isCapacityFull()) {
            // Remove least recently used (last item)
            this.cache.pop();
        }

        // Insert as most recently used
        this.cache.unshift(item);
    }
}

// Usage Example

let lru = new LruCache(3);

lru.setItem(1);
lru.setItem(2);
lru.setItem(3);
console.log(lru.cache); // [3,2,1]

lru.setItem(2);
console.log(lru.cache); // [2,3,1]

lru.setItem(4);
console.log(lru.cache); // [4,2,3] → 1 evicted (LRU)
