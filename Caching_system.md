# 📘 Phase 1 - Part 7: Caching Systems

## 🔹 Why Cache?

- Reduces latency
- Offloads database
- Improves UX & performance

---

## 🔹 Types of Cache

| Type           | Example     |
|----------------|-------------|
| In-Memory      | Redis       |
| Client-side    | Browser     |
| Distributed    | Clustered Redis |
| CDN            | CloudFront  |

---

## 🔹 Strategies

- Read-Through
- Cache-Aside (Lazy load)
- Write-Through
- Write-Around
- Write-Back (risky)

---

## 🔹 Eviction Policies

- LRU (Least Recently Used)
- LFU (Least Frequently Used)
- FIFO
- Random

---

## 🔹 Invalidation

- TTL (Time-To-Live)
- Manual
- Write-through sync

---

## 🔹 Tools

- Redis (most common)
- Memcached
- Varnish
- CloudFront
