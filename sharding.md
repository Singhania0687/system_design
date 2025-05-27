Great! Let’s now move to the next topic in Phase 4.

---

# ✅ PHASE 4 – PART 12: **Data Partitioning (Sharding)**

Partitioning (commonly referred to as **sharding**) is the process of **splitting large datasets** into smaller, more manageable chunks (called **shards**) that can be distributed across different machines or locations.

---

## 🚀 Why Partition or Shard Data?

| Reason                | Benefit                                    |
| --------------------- | ------------------------------------------ |
| Handle large datasets | Distributes data storage across machines   |
| Improve performance   | Reduces query load on a single server      |
| Increase availability | Failure in one shard doesn’t affect others |
| Enable scalability    | Scale horizontally by adding more machines |

---

## 📚 Types of Partitioning

### 1️⃣ **Horizontal Partitioning (Sharding)**

* Each table row goes to a different shard.
* All shards have the same schema but different data rows.

```text
Users Shard 1: ID 1 - 10,000
Users Shard 2: ID 10,001 - 20,000
Users Shard 3: ID 20,001 - 30,000
```

✅ **Best For**: Large tables with similar row structures

---

### 2️⃣ **Vertical Partitioning**

* Split columns into different tables or databases.

```text
User Profile DB: name, email, phone
User Activity DB: last_login, purchase_history
```

✅ **Best For**: Microservices, isolating sensitive data (like PII)

---

## 🔢 Sharding Strategies

### 📌 1. **Hash-Based Sharding**

* Hash the sharding key (e.g., `user_id`) and assign based on result.

```cpp
int shard = hash(user_id) % total_shards;
```

✅ Pros:

* Uniform distribution
* Prevents hotspots

❌ Cons:

* Difficult to add/remove shards dynamically (hashes change)
* Complex rebalancing

---

### 📌 2. **Range-Based Sharding**

* Divide data by value range (e.g., user IDs or timestamps)

```text
Shard 1: user_id 1–10000
Shard 2: user_id 10001–20000
```

✅ Pros:

* Simple to implement
* Range queries are fast

❌ Cons:

* Can lead to **hotspots** if data is not evenly distributed

---

### 📌 3. **Directory-Based Sharding (Lookup Table)**

* Maintain a centralized map of keys to shard locations.

```text
Shard Map: user_id 12345 -> Shard 2
```

✅ Pros:

* Fully flexible, dynamic

❌ Cons:

* Single point of failure
* Adds latency

---

### 📌 4. **Geo-Based Sharding**

* Partition by location (e.g., country, region)

✅ Useful for:

* GDPR/Regulations
* Faster access from local data centers

---

## 🔄 Resharding

Resharding is moving data between shards (e.g., when you scale from 4 to 8 nodes).

* **Offline Resharding**: Temporarily stop traffic (not ideal).
* **Online Resharding**: Use consistent hashing or live migration.

---

## 🛠 Real-Life Examples

| System        | Partitioning Strategy      |
| ------------- | -------------------------- |
| MongoDB       | Hash or range-based shards |
| Cassandra     | Consistent hashing         |
| HBase         | Range-based sharding       |
| Elasticsearch | Hash-based index shards    |

---

## ❓ Interview Questions

| Question                                                   | What It Tests                         |
| ---------------------------------------------------------- | ------------------------------------- |
| “Difference between horizontal and vertical partitioning?” | Understanding of partitioning types   |
| “Challenges in sharding?”                                  | Knowledge of rebalancing, hot keys    |
| “How does hash-based sharding affect resharding?”          | Practical understanding of trade-offs |
| “How would you implement sharding in MongoDB?”             | Tech-specific knowledge               |

---

## 📝 Summary

| Term                | Description                                |
| ------------------- | ------------------------------------------ |
| Horizontal Sharding | Split rows across multiple databases       |
| Vertical Sharding   | Split columns across services/databases    |
| Hash Sharding       | Uses hash of key to decide shard           |
| Range Sharding      | Based on key range (e.g., timestamps, IDs) |
| Directory Sharding  | Maintains map of keys to shards            |
| Resharding          | Redistributing data during scaling         |

---
