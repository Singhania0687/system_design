# 📘 Phase 1 – Part 12: Load Balancers

## 🔹 Why Load Balancers?

- ⚖️ Distribute traffic
- 💥 Auto-healing (removes dead servers)
- 🔒 Acts as a security layer
- 📈 Enables horizontal scaling

---

## 🔹 LB Strategies

- Round Robin
- Least Connections
- IP Hash
- Weighted

---

## 🔹 L4 vs L7

| Layer | Protocols | Examples       |
|-------|-----------|----------------|
| L4    | TCP/UDP   | AWS NLB        |
| L7    | HTTP/HTTPS| AWS ALB, NGINX |

---

## 🔹 Features

- Sticky Sessions
- Health Checks
- SSL Termination
- Rate Limiting
- Global Routing

---

## 🔹 Tools

- NGINX, HAProxy, Envoy, Traefik
- AWS ALB, NLB
- Route 53 for DNS-based LB
