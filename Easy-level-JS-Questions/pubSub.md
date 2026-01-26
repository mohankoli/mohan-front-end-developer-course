# Simple Pub/Sub Implementation in JavaScript

This is a minimal implementation of the Publish–Subscribe pattern, often used in event-driven backend systems.

---

## Code

```js
class Pubsub {
  constructor() {
    this.events = {};
  }

  subscribe(event, listener) {
    if (!this.events[event]) {
      this.events[event] = [];
    }
    this.events[event].push(listener);
  }

  publish(event, data) {
    if (this.events[event]) {
      this.events[event].forEach(listener => listener(data));
    }
  }
}

const ps = new Pubsub();

ps.subscribe("order", (data) => {
  console.log("email", data);
});

ps.subscribe("order", (data) => {
  console.log("analytics", data);
});

ps.publish("order", { id: 1, product: 'book' });
```

---

## Expected Output

```
email { id: 1, product: 'book' }
analytics { id: 1, product: 'book' }
```

---

## Explanation

- `subscribe(event, listener)` registers handlers for a given event.
- `publish(event, data)` triggers all listeners for that event.
- Decouples event producers from event consumers.

This pattern is used in:
- Microservices
- Event buses
- Message queues (Kafka, RabbitMQ)
- Real-time systems
