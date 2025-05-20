# 📘 Phase 1 - Part 4: Caching in System Design

## 🔹 What is Caching?
Storing frequently accessed data in fast memory to reduce latency.

---

## 🔸 Benefits
- Improves response time
- Reduces DB/API load
- Enhances scalability

---

## 🔹 Types of Caching

| Type               | Example |
|--------------------|---------|
| In-memory          | Java Maps, Guava, LRUCache |
| Distributed        | Redis, Memcached |
| CDN/Edge Caching   | Cloudflare, Akamai |
| DB Cache           | Query Cache in MySQL/Postgres |

---

## 🔹 Caching Strategies

| Strategy         | Description |
|------------------|-------------|
| Read Through     | Auto fetches from DB on miss |
| Write Through    | Writes to cache + DB |
| Write Behind     | Write to cache first, then DB |
| Cache Aside      | App decides to fetch/store in cache |

---

## 🔹 Invalidation Techniques

| Method           | When Used |
|------------------|-----------|
| TTL              | Auto expire cache |
| LRU              | Evict old unused |
| Manual Invalidate| Developer logic |
| Write Invalidate | On DB update/delete |

---

## 🔹 Tools

- **Redis** – Persistent, fast, advanced features
- **Memcached** – Lightweight, no persistence
- **CDNs** – Cache static files
- **In-memory** – App-level cache for small scale

---

## 🧠 Key Takeaway
Use caching wisely to optimize performance. But beware of **stale data** and invalidation pitfalls!
