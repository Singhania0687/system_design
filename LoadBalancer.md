# 📘 Phase 1 - Part 3: Load Balancing in System Design

## 🔹 What is Load Balancing?
Distributes incoming traffic to multiple backend servers to avoid overloading one server.

---

## 🔸 Benefits
- High availability
- Better performance
- Scalability
- Enhanced security

---

## 🔹 Types of Load Balancing

| Type               | Example        |
|--------------------|----------------|
| Hardware LB        | F5, Citrix     |
| Software LB        | Nginx, HAProxy |
| Cloud LB           | AWS ELB        |

---

## 🔹 Algorithms

| Algorithm          | Description                             |
|--------------------|-----------------------------------------|
| Round Robin        | Sequential distribution                 |
| Least Connections  | Least active connection wins            |
| IP Hash            | Same user → same server                 |
| Weighted RR        | High-capacity servers get more traffic  |
| Random             | Chooses server randomly                 |

---

## 🔹 L4 vs L7 Load Balancing

| Feature     | L4 Load Balancer      | L7 Load Balancer         |
|-------------|------------------------|---------------------------|
| Protocol    | TCP/UDP                | HTTP/HTTPS                |
| Routing     | Based on IP/Port       | Based on URL, headers     |
| Examples    | HAProxy, NLB           | Nginx, ALB, Envoy         |

---

## 🔹 Health Checks
LBs perform checks like `/health` to see if a server is alive. Unhealthy servers are removed temporarily.

---

## 🧠 Summary

- Use load balancers to distribute traffic.
- L4: Fast and basic, L7: Smart and context-aware.
- Use health checks, sticky sessions, weighted algorithms as needed.
