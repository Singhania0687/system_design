# 📘 Phase 1 - Part 6: Message Queues & Async Communication

## 🔹 What is a Message Queue?

- Decouples producer & consumer
- Handles temporary message storage
- Enables retry, scaling, fault-tolerance

---

## 🔹 Use Cases

- Email/SMS sending
- Video rendering
- Logging & telemetry
- Order systems
- IoT pipelines

---

## 🔹 Tools

| Tool      | Type              |
|-----------|-------------------|
| Kafka     | Distributed log   |
| RabbitMQ  | Queue broker      |
| SQS       | Cloud queue       |
| Redis     | Fast memory queue |
| NATS      | Lightweight pub/sub |

---

## 🔹 Key Concepts

- **Producer**: Sends messages
- **Consumer**: Processes messages
- **Broker**: Manages queue
- **DLQ**: Stores failed messages

---

## 🔹 Patterns

- Pub/Sub
- Producer-Consumer
- Retry & DLQ
