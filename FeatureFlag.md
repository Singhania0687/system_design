Absolutely! Let's dive into **Phase 5, Topic 9: Configuration Management** – focusing specifically on **Feature Flags** and tools like **LaunchDarkly**.

---

## 🔧 9️⃣ Configuration Management in System Design

### ✅ What is Configuration Management?

Configuration Management refers to the **practice of handling environment-specific variables and system behaviors** **without redeploying the app**.

This includes:

* Feature toggles
* Secrets and environment variables
* App-level config files
* Remote config updates

---

## 🎯 Focus: Feature Flags (Toggles)

### 🔹 What Are Feature Flags?

A **Feature Flag** (aka **Feature Toggle**) is a technique to enable or disable a **specific feature** in production **at runtime**.

🔧 Used to:

* Control release of new features
* Perform **A/B testing**
* Enable **canary releases**
* Rollback faulty features instantly

---

### 🧱 Example: Without Feature Flags

```cpp
if (newLoginFeatureEnabled) {
    showNewLoginPage();
} else {
    showOldLoginPage();
}
```

Now, you can toggle `newLoginFeatureEnabled` using a **remote config** — without redeploying the code!

---

## 🔐 Use Cases of Feature Flags

| Use Case                | Description                                   |
| ----------------------- | --------------------------------------------- |
| **Gradual Rollout**     | Enable feature for 10%, 50%, 100% of users    |
| **A/B Testing**         | Split users between two variants of a feature |
| **Kill Switch**         | Turn off buggy features instantly             |
| **User Targeting**      | Enable feature for specific users/groups      |
| **Operational Control** | Toggle background jobs, log levels, etc.      |

---

## 🚀 Popular Feature Flag Tools

| Tool             | Features                                                                |
| ---------------- | ----------------------------------------------------------------------- |
| **LaunchDarkly** | Feature flags, experimentation, user targeting, SDKs for many platforms |
| **Flagsmith**    | Open-source feature flag management                                     |
| **Unleash**      | Self-hosted feature management                                          |
| **Split.io**     | Feature delivery and A/B testing                                        |
| **ConfigCat**    | Easy-to-integrate flagging system                                       |

---

## 🎛️ LaunchDarkly – Overview

**LaunchDarkly** is an enterprise-grade feature flag platform that allows developers to:

✅ Toggle features per user, per region
✅ Roll out features incrementally
✅ Track analytics on how features perform
✅ Integrate with CI/CD pipelines

---

### 🔌 Example: LaunchDarkly in C++ (via REST API)

LaunchDarkly has official SDKs for many languages, but for C++ you may need to **integrate via their REST API**.

#### Step 1: Store Feature Flag State (Example JSON)

```json
{
  "key": "new-login-feature",
  "value": true
}
```

#### Step 2: C++ Code to Fetch Feature Flag (Using cURL)

```cpp
#include <iostream>
#include <curl/curl.h>
using namespace std;

static size_t callback(void *contents, size_t size, size_t nmemb, string *output) {
    size_t totalSize = size * nmemb;
    output->append((char *)contents, totalSize);
    return totalSize;
}

bool isFeatureEnabled(string flagKey) {
    CURL *curl;
    CURLcode res;
    string readBuffer;

    curl = curl_easy_init();
    if(curl) {
        string url = "https://app.launchdarkly.com/sdk/latest-flags/" + flagKey;
        struct curl_slist *headers = NULL;
        headers = curl_slist_append(headers, "Authorization: YOUR_SDK_KEY");

        curl_easy_setopt(curl, CURLOPT_URL, url.c_str());
        curl_easy_setopt(curl, CURLOPT_HTTPHEADER, headers);
        curl_easy_setopt(curl, CURLOPT_WRITEFUNCTION, callback);
        curl_easy_setopt(curl, CURLOPT_WRITEDATA, &readBuffer);
        res = curl_easy_perform(curl);
        curl_easy_cleanup(curl);

        return readBuffer.find("\"value\":true") != string::npos;
    }
    return false;
}

int main() {
    if (isFeatureEnabled("new-login-feature")) {
        cout << "Show new login page!" << endl;
    } else {
        cout << "Show old login page!" << endl;
    }
    return 0;
}
```

> ✅ On macOS, install cURL:

```bash
brew install curl
```

---

## 🧠 Best Practices with Feature Flags

| Practice                          | Benefit                                 |
| --------------------------------- | --------------------------------------- |
| Use **clear naming** conventions  | Avoid confusion in code                 |
| **Clean up** old flags            | Prevent tech debt                       |
| Monitor **flag performance**      | Watch for feature impact, crashes, etc. |
| Secure with **role-based access** | Control who can toggle flags            |
| Integrate with **CI/CD**          | Automate rollout strategies             |

---

## 🧪 A/B Testing with Feature Flags

LaunchDarkly and other platforms let you:

* Randomly assign users to A or B
* Track performance metrics
* Make data-driven decisions

---

## 🔥 Kill Switch Use Case

Imagine a new payment feature misbehaves in production:

```cpp
if (featureFlag("enable_new_payment")) {
    useNewPaymentGateway();
} else {
    fallbackToOldGateway();
}
```

You can immediately **turn off** `enable_new_payment` from the dashboard and save production.

---

## ❌ When NOT to Use Feature Flags

| Scenario                    | Reason                                           |
| --------------------------- | ------------------------------------------------ |
| Core architectural decision | Shouldn't toggle deep system behavior            |
| Complex dependency trees    | May cause inconsistent behavior between features |
| Performance-critical paths  | Flag evaluation might add latency                |

---

## 🧠 Interview Questions

| Question                                             | Tests Understanding of            |
| ---------------------------------------------------- | --------------------------------- |
| What are feature flags and how do they help?         | Deployment strategies, resilience |
| How do you manage stale or deprecated flags?         | Tech debt and cleanup practices   |
| How would you implement a kill switch in production? | Real-world incident handling      |
| Compare LaunchDarkly vs ConfigCat vs Unleash.        | Trade-off analysis                |
| Can feature flags be abused? If so, how?             | Design maturity                   |

---

## ✅ Summary

| Topic           | Details                                      |
| --------------- | -------------------------------------------- |
| Feature Flags   | Enable/disable features without code deploys |
| Tools           | LaunchDarkly, Unleash, Flagsmith, Split.io   |
| Use Cases       | Gradual rollouts, kill switches, A/B testing |
| Best Practices  | Naming, cleanup, secure access, monitoring   |
| Common Pitfalls | Flag overload, stale flags, runtime latency  |

---

Would you like to see:

* ✅ How to integrate Feature Flags in a **React frontend or Node.js backend**?
* ✅ A **diagram-based system** showing how LaunchDarkly fits into microservice architecture?
* ✅ Or continue with the **next topic in the System Design roadmap**?
