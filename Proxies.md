# 📘 Phase 1 – Part 13: Proxies

## 🔹 Proxy Basics

- A **proxy** sits between client and server
- Types:
  - **Forward Proxy** – client-side
  - **Reverse Proxy** – server-side

---

## 🔹 Reverse Proxy = System Design Super Tool

- SSL Termination
- Load Balancing
- Caching
- Smart Routing
- Security

---

## 🔹 Tools

- NGINX
- HAProxy
- Squid (forward proxy)
- Envoy (modern, used in service mesh)
- Apache Traffic Server

---

## 🔹 Reverse Proxy vs Load Balancer

| Feature       | Reverse Proxy | Load Balancer |
|---------------|---------------|---------------|
| Caching       | ✅             | ❌            |
| SSL Termination | ✅           | ⚠️ Sometimes  |
| Layer         | L7            | L4 or L7      |

