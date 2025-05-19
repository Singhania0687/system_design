# 📘 Phase 1 - Part 2: Key System Design Attributes

## 🔹 1. Scalability

**Definition**: Ability to handle increased load.

**Types**:
- Vertical Scaling (scale-up): Add resources to one server
- Horizontal Scaling (scale-out): Add more servers

**Example**: Netflix uses horizontal scaling on AWS.

---

## 🔹 2. Availability

**Definition**: Uptime capability of a system.

**Availability % vs Downtime**:

| Availability | Downtime per year |
|--------------|-------------------|
| 99%          | 3.65 days         |
| 99.9%        | 8.76 hours        |
| 99.99%       | 52 minutes        |
| 99.999%      | 5 minutes         |

**Techniques**:
- Load balancer
- Failover
- Redundancy

---

## 🔹 3. Reliability

**Definition**: Returns correct results even under stress or partial failure.

**Techniques**:
- Replication
- Retry logic
- Circuit breaker pattern

---

## 🔹 4. Maintainability

**Definition**: Ease of updates and debugging.

**Practices**:
- Modular architecture
- Microservices
- Documentation
- CI/CD

---

## 🧠 Summary

| Attribute     | Goal                            |
|---------------|----------------------------------|
| Scalability    | Handle growing load              |
| Availability   | Maximize uptime                  |
| Reliability    | Ensure correctness               |
| Maintainability| Enable easy updates/fixes        |
