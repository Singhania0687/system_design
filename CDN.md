# 📘 Phase 1 - Part 8: CDN & Edge Caching

## 🔹 Why Use CDN?

- Reduce latency
- Global delivery
- Offload origin server
- DDoS protection

---

## 🔹 What Can Be Cached?

- Static assets (JS, CSS, images)
- Public API responses
- HTML with headers

---

## 🔹 CDN Caching Headers

```http
Cache-Control: public, max-age=3600
ETag: "file-version"
Vary: Accept-Encoding
```

---

## 🔹 Tools

- Cloudflare
- AWS CloudFront
- Akamai
- Fastly

---

## 🔹 Invalidation

- Purge specific URL
- Purge all (use carefully!)
- `stale-while-revalidate` for background freshness

