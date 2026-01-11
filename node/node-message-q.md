# Node.js + Message Queues (RabbitMQ + Kafka) --- Interview Notes

## 1. Why Message Queues?

-   Decoupling services
-   Async/background tasks
-   Traffic spike buffering
-   Retry & failure isolation
-   Backpressure control
-   Independent worker scaling
-   Supports batch & stream processing

------------------------------------------------------------------------

## 2. Real use cases

-   Email/SMS notifications
-   Payments & settlements
-   Webhook handling
-   Video/image processing
-   E‑commerce order pipeline
-   IoT event ingestion
-   Analytics & logging
-   Inventory synchronization

------------------------------------------------------------------------

# RabbitMQ (Messaging / Work Queue)

## Concepts

-   Broker-based message queue
-   Supports **Push** model
-   Good for **Work Queues** & **Routing**

## Features

-   Exchanges (direct, topic, fanout, headers)
-   Routing keys
-   Durable queues
-   Ack/Nack
-   Priority queues
-   DLQ support
-   TTL (message expiry)

## RabbitMQ Suitable for:

✔ Microservices\
✔ Notification systems\
✔ Payment workflows\
✔ Retry & routing logic

------------------------------------------------------------------------

# Kafka (Event Streaming Platform)

## Concepts

-   High-throughput distributed log
-   **Pull** consumption model
-   Partition-based parallelism
-   Offsets & Commit logs
-   Replay events (time travel)
-   Retention-based storage

## Kafka Suitable for:

✔ Real-time event pipelines\
✔ Data analytics\
✔ Stream processing (Flink/Spark)\
✔ Event sourcing\
✔ IoT / telemetry\
✔ Banking / Ledger systems

------------------------------------------------------------------------

# Key Differences: RabbitMQ vs Kafka

  Feature            RabbitMQ                  Kafka
  ------------------ ------------------------- ----------------------------
  Model              Message broker            Event streaming
  Consumption        Push                      Pull
  Ordering           FIFO inside queue         Per partition
  Replay             No                        Yes
  Retention          Short                     Long
  Scaling            Limited                   Massive
  Use case           Task distribution         Event pipelines
  Batch processing   Manual                    Built-in
  Exactly-once       Hard                      Supported with idempotency
  Delivery mode      At-most / at-least-once   At-least/exactly-once

------------------------------------------------------------------------

# Node.js Integration

## Node + RabbitMQ libs:

-   `amqplib`
-   `rascal`
-   `amqp10`

## Node + Kafka libs:

-   `kafkajs`
-   `node-rdkafka`
-   `confluent-kafka`

------------------------------------------------------------------------

# Delivery Semantics

### At-most-once

No retries (fast but risky)

### At-least-once

Retries → possible duplicates (most common)

### Exactly-once

No duplicates + no loss (complex; Kafka supports)

------------------------------------------------------------------------

# Backpressure Handling

RabbitMQ → queues buffer tasks\
Kafka → partitions buffer events with high throughput

------------------------------------------------------------------------

# Retry + DLQ

Both support: - Retry attempts - Delayed retry - DLQ (Dead Letter Queue)

------------------------------------------------------------------------

# Batch Processing

Kafka → native batch fetch & commit\
RabbitMQ → time/size batching via consumer logic

------------------------------------------------------------------------

# Scaling Workers

### Horizontal scaling

Add more consumers

Kafka → consumer groups scale automatically\
RabbitMQ → competing consumers pattern

------------------------------------------------------------------------

# Idempotency Importance

Workers must handle duplicate messages safely\
Example: charge payment only once

------------------------------------------------------------------------

# Monitoring & Observability

Track: - queue lag - consumer lag - DLQ size - throughput - retry
counts - processing latency

Tools: - Prometheus + Grafana - Kafka UI / Burrow - RabbitMQ Management
UI

------------------------------------------------------------------------

# Interview Quick Answers

**Q: Why queues?**\
→ async + decoupling + reliability + scaling

**Q: When to use Kafka?**\
→ analytics, streaming, event logs, high throughput

**Q: When to use RabbitMQ?**\
→ task execution, routing, retries, microservices

**Q: Can queues handle batch?**\
✔ Yes (Kafka native, RabbitMQ manual)

**Q: Can events be replayed?**\
Kafka → Yes\
RabbitMQ → No

**Q: Who handles ordering?**\
Kafka → partition key\
RabbitMQ → queue FIFO

------------------------------------------------------------------------

# Summary

  Topic                RabbitMQ    Kafka
  -------------------- ----------- ------------
  Type                 Broker      Log/Stream
  Suitability          Tasks       Events
  Replay               ✖           ✔
  Scaling              Medium      High
  Batch                Manual      Native
  Retention            Short       Long
  Delivery Guarantee   AMO / ALO   ALO / EO

------------------------------------------------------------------------
