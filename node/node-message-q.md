# Node.js With Message Queues -- Interview Notes

## 1. Why do we use Message Queues?

-   Decoupling services
-   Async/background processing
-   Handling traffic spikes
-   Retry & failure isolation
-   Load leveling (backpressure)
-   Scaling workers independently

## 2. Real-world use cases

-   Email sending
-   Payment processing
-   Webhooks
-   Video/image processing
-   Analytics pipelines
-   Notification fan-out
-   IoT messaging
-   Inventory sync

## 3. High-level architecture

Client → Node API → Queue → Worker Service → DB/External System

## 4. Popular queues for Node.js

Redis + BullMQ, RabbitMQ, Kafka, AWS SQS, NATS, MQTT

## 5. Pull vs Push

-   Push: Broker pushes (RabbitMQ)
-   Pull: Consumer fetches (Kafka)

## 6. ACK

ACK = confirm message processed

## 7. Delivery semantics

-   at-most-once
-   at-least-once
-   exactly-once

## 8. Dead Letter Queue (DLQ)

Stores failed messages after retries

## 9. Retry mechanisms

Backoff + retry limit + DLQ

## 10. Choosing queue

Kafka for streams, RabbitMQ for routing, SQS for cloud, BullMQ for jobs

## 11. Worker scaling

Horizontal scaling + concurrency + DLQ + idempotency

## 12. Idempotency

Safe repeated execution (avoid double payments)

## 13. Backpressure

Queue acts as buffer for overload

## 14. MQ vs Event Streaming

Kafka supports replay + partitions

## 15. Priority Queues

Higher priority jobs first

## 16. FIFO & Competing Consumers

FIFO ensures order; competing workers distribute

## 17. Internal pattern

API publishes → Worker consumes

## 18. Coding Q

Send email via queue instead of direct

## 19. Pub/Sub vs Work Queue

Pub/Sub = broadcast, Work Queue = load-balanced

## 20. Fault tolerance

Retries, DLQ, persistent store, idempotency

## 21. Advantages

Scalable, async, fault-tolerant, microservice-friendly

## 22. Disadvantages

Extra infra, monitoring, DevOps overhead

## 23. Monitoring

Queue length, latency, retries, DLQ usage

## 24. Bonus Q

-   How to prevent duplicates?
-   How to scale workers?
-   Kafka partitions?
-   Consumer groups?
