# 📘 Phase 1 - Part 9: Rate Limiting & Throttling

## 🔹 Why Rate Limit?

- Avoid abuse & overload
- Prevent DoS attacks
- Ensure fairness
- Control API usage

---

## 🔹 Key Algorithms

- Fixed Window
- Sliding Window (Log/Counter)
- Token Bucket ✅ burst-friendly
- Leaky Bucket ✅ smooth flow

---

## 🔹 Redis-based Example

```python
ZADD user:{ip} timestamp timestamp
ZREMRANGEBYSCORE user:{ip} 0 (timestamp - window)
ZCARD user:{ip}
```

---

## 🔹 Libraries

- Node.js: express-rate-limit, rate-limiter-flexible
- Python: Flask-Limiter
- Nginx: limit_req_zone
