# 📘 Phase 1 - Part 5: Database Design

## 🔹 SQL vs NoSQL

| Feature     | SQL                  | NoSQL                |
|-------------|----------------------|-----------------------|
| Schema      | Fixed                | Flexible              |
| Scaling     | Vertical             | Horizontal            |
| Use Case    | Banking, Inventory   | Social, Logs, IoT     |

---

## 🔹 Normalization vs Denormalization

| Type           | When Used                 |
|----------------|---------------------------|
| Normalization  | Write-heavy, transactions |
| Denormalization| Read-heavy, reporting     |

---

## 🔹 Indexing
- Use for fast read performance.
- Avoid over-indexing to reduce write cost.

---

## 🔹 Partitioning vs Sharding

- **Partitioning** = Logical table split
- **Sharding** = Physical DB split

---

## 🔹 CAP Theorem

- **C**onsistency
- **A**vailability
- **P**artition Tolerance  
You can pick **2 of 3**.

---

## 🔹 Replication
- Improves redundancy and read throughput.
- Master-Slave or Master-Master models.

---

## 🧠 Key Takeaway
Design your DB based on:
- Access pattern (read/write heavy?)
- Volume & scalability needs
- Consistency vs Availability trade-offs
