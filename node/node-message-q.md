# Node.js With Message Queues – Interview Notes

---

## ❓ 1. Why do we use Message Queues?

Message queues help in:
- Decoupling services
- Async/background processing
- Handling traffic spikes
- Retry & failure isolation
- Load leveling (backpressure)
- Scaling workers independently

---

## ❓ 2. Common real-world uses of queues

| Use Case | Queue Example |
|---|---|
| Email sending | Redis / RabbitMQ |
| Payment processing | Kafka / SQS |
| Webhooks | SQS |
| Video/image processing | BullMQ |
| Analytics pipelines | Kafka |
| Notification fan-out | Redis Pub/Sub |
| IoT messaging | MQTT |
| Inventory sync | Kafka |

---

## ❓ 3. High-level architecture

