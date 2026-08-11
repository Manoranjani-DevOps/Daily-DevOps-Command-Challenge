# ✅ Solution

## Correct Answer

## **A. `docker stop myapp`**

The key requirement is:

> **"Stop the container gracefully."**

The correct command is:

```bash
docker stop myapp
```

Docker sends a **SIGTERM** signal to the container's main process, giving the application an opportunity to shut down cleanly.

---

## What `docker stop` Allows the Application to Do

During a graceful shutdown, the application can:

- ✅ Finish ongoing work
- ✅ Close active connections
- ✅ Flush pending data
- ✅ Perform cleanup operations
- ✅ Shut down gracefully

The basic flow is:

```text
docker stop
      ↓
Send SIGTERM
      ↓
Application handles shutdown
      ↓
Graceful cleanup
      ↓
Container exits
```

If the container doesn't stop within Docker's configured/default timeout, Docker sends **SIGKILL** to forcefully terminate it.

---

## 💡 Real-World DevOps Workflow

Suppose you're preparing to deploy a new version of an application:

```bash
docker ps
docker stop myapp
docker rm myapp
docker run ...
```

The important point is that **stopping** and **removing** a container are two different operations.

A good DevOps Engineer understands the difference before taking action on a production container.

---

## 🚨 Common Mistake

Many beginners use:

```bash
docker kill myapp
```

when they simply want to stop a container.

Although `docker kill` terminates the container immediately by default, it doesn't provide the same graceful shutdown opportunity as:

```bash
docker stop myapp
```

Always prefer a graceful stop unless there is a specific reason to forcefully terminate the container.

---

## ❌ Why the Other Options Are Incorrect

### B.

```bash
docker rm myapp
```

- ❌ Removes the container.
- ❌ It is not the command for gracefully stopping a running container.
- ❌ Normally, the container must be stopped before it can be removed.

### C.

```bash
docker kill myapp
```

- ❌ Forcefully terminates the container by default.
- ❌ The application doesn't get the normal graceful shutdown opportunity.
- ✅ Useful when a container is stuck or must be terminated immediately.

### D.

```bash
docker restart myapp
```

- ❌ Stops and starts the container again.
- ❌ The requirement is simply to stop the container.

---

## 🎯 Interview Tip

Remember these essential Docker commands:

```bash
docker stop <container>
```

👉 Gracefully stop a container.

```bash
docker kill <container>
```

👉 Forcefully terminate a container by default.

```bash
docker restart <container>
```

👉 Restart a container.

```bash
docker rm <container>
```

👉 Remove a stopped container.

### 🧠 Easy Memory Trick

```text
STOP     → Graceful
KILL     → Forceful
RESTART  → Stop + Start
RM       → Remove
```

Understanding these differences is a common Docker interview topic.

---

## 🚨 Real Production Tip

If:

```bash
docker stop myapp
```

takes too long and the container doesn't exit, don't immediately assume the application is healthy.

Investigate why it isn't shutting down gracefully:

```bash
docker logs myapp
```

You can also inspect the container:

```bash
docker inspect myapp
```

Check whether the application is receiving and handling the shutdown signal correctly.

If necessary, you can then use:

```bash
docker kill myapp
```

as a last resort.

> ⚠️ **Production Rule:** Always prefer graceful shutdown first. Use forceful termination only when the container cannot be stopped normally or immediate termination is required.

---

## 🎯 Key Takeaway

When you need to **gracefully stop a running Docker container**, use:

```bash
docker stop <container>
```

It gives the application an opportunity to finish ongoing work and perform cleanup before the container exits.

**`docker stop` = graceful shutdown.**  
**`docker kill` = forceful termination.**
