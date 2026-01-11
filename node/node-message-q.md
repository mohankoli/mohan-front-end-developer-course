
Node API returns fast; heavy work happens in worker.

---

## ❓ 4. Popular queues for Node.js

| Queue | Best for |
|---|---|
| Redis + BullMQ | job queues + retries |
| RabbitMQ | routing + pub/sub |
| Kafka | high throughput event streaming |
| AWS SQS | cloud managed queue |
| NATS | low-latency messaging |
| MQTT | IoT devices |

---

## ❓ 5. Pull vs Push based message consumption

- **Push** → Broker pushes message to consumer  
  Example: RabbitMQ

- **Pull** → Consumer fetches messages  
  Example: Kafka

---

## ❓ 6. What is ACK in message queues?

ACK = acknowledgment that message was processed.

If consumer fails before ACK → message is redelivered.

---

## ❓ 7. Delivery semantics

| Mode | Meaning |
|---|---|
| At-most-once | no retries |
| At-least-once | retries → duplicates possible |
| Exactly-once | no loss + no duplicates (complex) |

Defaults:
- Kafka → `at-least-once`
- RabbitMQ → `at-most-once` unless ACK enabled

---

## ❓ 8. What is Dead Letter Queue (DLQ)?

DLQ stores messages that failed after max retries.
Good for auditing + debugging failures.

---

## ❓ 9. Retry mechanisms

Typically include:
- retry with delay (backoff)
- retry limit
- DLQ fallback

Example backoff:
