You're right, and thank you for your patience. Based on the previous parts already provided, here's the continuation of the **System Design Roadmap** after Load Balancers, Rate Limiting, and Caching:

---

## 📊 PHASE 1 – PART 17+: **Scalability Patterns**

Now we move to advanced and essential **architecture patterns** used to scale distributed systems.

---

### 🔹 1. **Service Discovery**

#### ✅ What is it?

In a microservices architecture, service instances often change (scale in/out, crash, etc.). Service Discovery helps services find and talk to each other dynamically.

#### 💡 Types:

* **Client-side discovery**: Clients query the registry (e.g., Netflix Eureka)
* **Server-side discovery**: Load balancer queries registry on behalf of client

#### ⚖️ Tools:

* Consul
* Netflix Eureka
* Etcd
* Kubernetes DNS

---

### 🔹 2. **Distributed Transactions / Saga Pattern**

#### ✅ Problem:

In microservices, how do you maintain consistency across services?

#### ✨ Solution:

Use **Sagas**: A sequence of local transactions where each has a compensating action.

* **Choreography**: Services listen to events
* **Orchestration**: Central controller coordinates the flow

---

### 🔹 3. **Event-Driven Architecture (EDA)**

#### ✅ What is it?

Components communicate via events (messages) instead of direct calls.

#### 🏛 Use Cases:

* Decoupled services
* Async communication
* Real-time systems (chat, notifications)

#### ⚖️ Tools:

* Kafka, RabbitMQ, NATS
* AWS SNS/SQS

---

### 🔹 4. **Message Queues & Pub/Sub Systems**

#### ✅ Problem:

If one service is slow or down, you don't want to lose data.

#### 💡 Solution:

Use a message broker:

* Message Queues (RabbitMQ, ActiveMQ)
* Log-based brokers (Kafka)

---

### 🔹 5. **Database Sharding**

#### ✅ Why?

To scale databases horizontally when vertical scaling is too expensive or slow.

#### 📊 Sharding Techniques:

* Range-based sharding
* Hash-based sharding
* Directory-based sharding

---

### 🔹 6. **Data Consistency Patterns**

* **Eventual consistency**
* **Strong vs. Weak consistency**
* **CAP Theorem**: Consistency, Availability, Partition Tolerance

---

### 🔹 7. **CQRS (Command Query Responsibility Segregation)**

#### ✅ What is it?

Separate read and write models for better performance and scaling.

* Write to a command model
* Read from a separate query model

---

### 🔹 8. **API Gateway**

#### ✅ Role:

* Unified entry point for all clients
* Authentication, logging, rate limiting, routing

#### ⚖️ Tools:

* Kong, NGINX, Express Gateway, AWS API Gateway

---

### 🔹 9. **Service Mesh**

#### ✅ Why?

Advanced networking for microservices (traffic control, observability, security)

#### ⚖️ Tools:

* Istio
* Linkerd
* Envoy

---

### 🔹 10. **Logging, Monitoring, and Observability**

#### 🏛 Tools:

* Logs: ELK Stack, Loki
* Metrics: Prometheus, Grafana
* Tracing: Jaeger, Zipkin

---

### 🔹 11. **Failover and Redundancy**

* Active-Passive or Active-Active setups
* Use health checks and auto-restarts
* Use redundant systems to tolerate failures

---

### 🔹 12. **Disaster Recovery & Backups**

* Backup databases & persistent storage
* Use Multi-AZ / Multi-region deployments
* RPO (Recovery Point Objective), RTO (Recovery Time Objective)

---

Would you like me to now continue with **PHASE 2: Design Patterns in System Design** (e.g., Strangler Fig, Bulkhead, Circuit Breaker, Sidecar, etc.) or jump into **real-world case studies (Design Netflix, WhatsApp, etc.)**?
