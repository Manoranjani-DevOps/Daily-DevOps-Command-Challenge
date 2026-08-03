# ✅ Solution

## Correct Answer

## **B. `docker stats`**

The requirement is:

> **"Show me the CPU and memory usage of running containers in real time."**

The correct command is:

```bash
docker stats
```

This command provides a live stream of resource usage for all running containers.

---

## Example Output

```text
CONTAINER ID   NAME      CPU %   MEM USAGE / LIMIT
ab12cd34       myapp     82.4%   512MiB / 2GiB
ef56gh78       redis      5.2%    45MiB / 1GiB
```

---

## What `docker stats` Helps You Identify

With a single command, you can monitor:

- ✅ CPU usage
- ✅ Memory usage
- ✅ Network I/O
- ✅ Block I/O
- ✅ Number of PIDs

This makes `docker stats` one of the first commands you'll use when investigating container performance issues.

---

## 💡 Real-World DevOps Workflow

A developer reports:

> **"The container is running, but the application is very slow."**

A typical troubleshooting workflow is:

```text
Check Running Containers
        │
        ▼
docker ps
        │
        ▼
docker stats
        │
        ▼
Identify High CPU or Memory Usage
        │
        ▼
Investigate the Application
```

If you notice:

```text
CPU Usage    : 99%
Memory Usage : 95%
```

You've identified the container that's consuming excessive resources and can begin deeper troubleshooting.

Useful commands during investigation:

```bash
docker ps
docker stats
docker logs <container-id>
docker inspect <container-id>
```

> **Note:** `docker stats` provides live resource usage, making it ideal for identifying containers under heavy load.

---

## 🚨 Common Mistake

Many beginners immediately check:

```bash
docker logs myapp
```

Logs are useful for application errors, but they **don't tell you whether the container is consuming excessive CPU or memory**.

When investigating performance issues, always check resource utilization first.

---

## ❌ Why the Other Options Are Incorrect

### A.

```bash
docker logs myapp
```

- ✅ Displays application logs.
- ❌ Does not show CPU or memory utilization.

### C.

```bash
docker inspect myapp
```

- ✅ Displays container configuration and metadata.
- ❌ Does not provide live resource usage.

### D.

```bash
docker images
```

- ✅ Lists locally available Docker images.
- ❌ Doesn't provide any runtime performance metrics.

---

## 🎯 Interview Tip

Remember these essential Docker commands:

```bash
docker ps
```

👉 View running containers.

```bash
docker stats
```

👉 Monitor live CPU, memory, network, and I/O usage.

```bash
docker logs <container>
```

👉 View application logs.

```bash
docker inspect <container>
```

👉 View container configuration and metadata.

Knowing when to use each command is a common Docker interview topic.

---

## 🚨 Real Production Tip

If `docker stats` shows:

```text
CPU Usage    : 95%+
Memory Usage : 90%+
```

Investigate further:

- 🔍 Is the application processing unusually high traffic?
- 🔍 Is there an infinite loop or inefficient code?
- 🔍 Are memory leaks occurring?
- 🔍 Are container resource limits configured appropriately?
- 🔍 Should the application be scaled horizontally?

Don't restart the container immediately—identify the reason for the high resource usage first.

---

## 🎯 Key Takeaway

When you need to monitor the **real-time CPU and memory usage** of running containers, use:

```bash
docker stats
```

It provides live performance metrics, helping you quickly identify containers under resource pressure and making it an essential command for Docker troubleshooting in production environments.
