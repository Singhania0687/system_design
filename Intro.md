# 📌 Phase 1 - Part 1: What is System Design?

## 🔹 Definition
System Design is the process of defining the architecture, components, modules, interfaces, and data for a system to satisfy specified requirements.

It involves:
- **High-Level Design (HLD)** — Big-picture architecture
- **Low-Level Design (LLD)** — Component-level view

---

## 🎯 Why is System Design Important?

| Reason         | Description                              |
|----------------|------------------------------------------|
| Scalability     | Handle growing users/data/traffic       |
| Reliability     | System continues to work on failures     |
| Maintainability | Easy to update, extend, and debug        |
| Performance     | Fast, responsive systems                 |
| Cost-Effective  | Efficient use of cloud/infrastructure    |

---

## 🔹 HLD vs LLD

| Feature   | High-Level Design (HLD)               | Low-Level Design (LLD)                |
|-----------|----------------------------------------|----------------------------------------|
| Focus     | System architecture & components       | Code structure, classes, DB schema     |
| Details   | Load balancers, DB, caches, queues     | API contracts, function details        |
| Audience  | Architects, senior engineers           | Developers                             |
| Example   | Use Redis as cache                     | Implement LRU in a Cache class         |

---

## 📘 Common Terminologies

| Term            | Meaning                               |
|-----------------|----------------------------------------|
| **Latency**      | Delay before response (ms)            |
| **Throughput**   | Requests handled per second           |
| **Load**         | Concurrent users or requests          |
| **Availability** | Uptime of the system (e.g. 99.99%)    |
| **Fault Tolerance** | System works even if parts fail     |
| **Redundancy**   | Backup components to prevent failures |

---

## 🔧 Use Case: Scalable URL Shortener

| Requirement         | Design Choice              |
|---------------------|----------------------------|
| Shorten long URLs   | Hashing + database         |
| Handle high traffic | Load balancer + cache      |
| Fast redirection    | CDN to serve cached links  |
