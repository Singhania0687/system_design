Awesome, Abhishek! Let's dive into:

---

# ✅ **PHASE 2: System Design Patterns**

These patterns are used in distributed systems to ensure **resilience**, **scalability**, **fault tolerance**, and **maintainability**.

---

## 📘 **PART 1: Circuit Breaker Pattern**

---

### 🔹 1. What Is It?

The **Circuit Breaker** pattern prevents an application from trying to perform an action that is likely to fail, allowing it to **fail fast** and **recover gracefully**.

---

### 🔹 2. Analogy

Like a circuit breaker in electrical wiring:

* When too much current (failures) is detected → trip the breaker
* Prevents further damage by **stopping traffic temporarily**

---

### 🔹 3. When to Use

* When **external services** are unreliable
* If you’re seeing **timeout spikes or high failure rates**
* To prevent **cascading failures**

---

### 🔹 4. States of Circuit Breaker

```
+-------------+      failureThresholdExceeded     +------------+
|   CLOSED    | --------------------------------> |   OPEN     |
+-------------+                                   +------------+
       ^                                              |
       |                                              | timeoutExpired
       |                                              v
+-------------+ <-------------------------------- +------------+
| HALF-OPEN   |     testSuccessful                |   OPEN     |
+-------------+                                   +------------+
```

| State         | Meaning                                                                    |
| ------------- | -------------------------------------------------------------------------- |
| **Closed**    | Calls flow normally, failure count is tracked                              |
| **Open**      | Calls are blocked/fail immediately (skip actual call)                      |
| **Half-Open** | Try a few test calls to check if service is back, then close if successful |

---

### 🔹 5. Circuit Breaker Parameters

| Parameter         | Description                               |
| ----------------- | ----------------------------------------- |
| Failure Threshold | Number of failures to trip the breaker    |
| Timeout           | How long to stay open before trying again |
| Success Threshold | How many successes to close breaker       |

---

### 🔹 6. Benefits

✅ Prevents overloading a failing service
✅ Allows recovery without restarts
✅ Improves system stability
✅ Helps in **self-healing** of microservices

---

### 🔹 7. Real Example (Netflix Hystrix - now deprecated but widely known)

Netflix used **Hystrix** for:

* Circuit breaking
* Fallback logic
* Isolation of failures in microservices

Today, many use:

* **Resilience4j** (Java)
* **Polly** (C#)
* **Istio** for service mesh circuit-breaking

---

### 🔹 8. Pseudocode Example

```cpp
enum State { CLOSED, OPEN, HALF_OPEN };

class CircuitBreaker {
    int failureCount = 0;
    int failureThreshold = 5;
    State state = CLOSED;
    time_t lastFailureTime;

public:
    bool allowRequest() {
        if (state == OPEN) {
            if (time(NULL) - lastFailureTime > 30) {
                state = HALF_OPEN;
                return true;
            }
            return false;
        }
        return true;
    }

    void recordSuccess() {
        failureCount = 0;
        state = CLOSED;
    }

    void recordFailure() {
        failureCount++;
        if (failureCount >= failureThreshold) {
            state = OPEN;
            lastFailureTime = time(NULL);
        }
    }
};
```

---

### 🧠 Use Cases

| App Scenario                     | Why Use Circuit Breaker?                  |
| -------------------------------- | ----------------------------------------- |
| Microservices calling each other | To avoid one service bringing down others |
| Payment gateways / APIs          | Avoid retry storms                        |
| IoT or mobile apps               | Handle unstable networks                  |

---

### 📌 Summary Cheatsheet

```
🧯 Circuit Breaker:
- Protects from cascading failures
- Works in 3 states: CLOSED, OPEN, HALF-OPEN
- Use when calling unreliable external services
- Combine with retries and timeouts
```

---


