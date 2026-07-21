# ✅ Solution

## Correct Answer

## **A. `docker logs a91bc23`**

The alert says:

> **"Container is restarting continuously."**

The first question a DevOps Engineer asks is:

> **"Why is the container restarting?"**

Not:

> **"How do I restart it again?"**

The very first command should be:

```bash
docker logs a91bc23
```

---

## Example Output

```text
Error: Database connection failed
```

or

```text
Port 8080 already in use
```

or

```text
Missing environment variable: DB_PASSWORD
```

Now you've identified the **root cause**, making it much easier to troubleshoot and fix the issue.

---

## What `docker logs` Helps You Identify

With a single command, you can quickly determine:

- ✅ Why the container exited or restarted
- ✅ Application startup errors
- ✅ Missing environment variables
- ✅ Database or external service connection failures
- ✅ Port binding conflicts
- ✅ Runtime exceptions and error messages

---

## 💡 Real-World DevOps Workflow

When a container keeps restarting, follow this troubleshooting workflow:

```text
Container Restarting
        │
        ▼
docker ps
        │
        ▼
docker logs <container-id>
        │
        ▼
Identify the Root Cause
        │
        ▼
Fix the Configuration or Application
        │
        ▼
Restart the Container (if required)
```

Useful commands during investigation:

```bash
docker ps
docker logs <container-id>
docker inspect <container-id>
docker exec -it <container-id> /bin/bash
```

> **Note:** `docker exec` works only if the container stays running long enough to attach.

---

## 🚨 Common Mistake

Many beginners immediately run:

```bash
docker restart a91bc23
```

or

```bash
docker stop a91bc23
docker start a91bc23
```

Although restarting the container may temporarily bring it back online, it **doesn't fix the underlying problem**.

A good DevOps Engineer follows this workflow:

```text
Observe
    ↓
Collect Evidence
    ↓
Analyze
    ↓
Fix
```

---

## 🎯 Interview Tip

If an interviewer asks:

> **"A Docker container is restarting continuously. What would you do first?"**

A strong answer is:

```bash
docker logs <container-id>
```

This demonstrates that you investigate the **root cause** before taking corrective action.

---

## 🚨 Real Production Tip

If `docker logs` shows:

```text
Connection refused: database
```

Don't restart the container immediately.

Instead, verify:

- 🔍 Is the database service running?
- 🔍 Are the database host and port correct?
- 🔍 Are the credentials valid?
- 🔍 Is the network connectivity working?
- 🔍 Are the required environment variables configured?

Fix the underlying issue first, then restart the container if necessary.

---

## 🎯 Key Takeaway

When a Docker container is stuck in a restart loop, **always start with `docker logs`**.

It provides the fastest way to identify the root cause of the failure, allowing you to troubleshoot efficiently instead of repeatedly restarting the container without understanding the problem.
