# ✅ Solution

## Correct Answer

## **B. `docker inspect myapp`**

The key requirement is:

> **"I want to inspect the container's configuration."**

The keyword here is **configuration**.

The command:

```bash
docker inspect myapp
```

returns a detailed JSON document containing the container's complete configuration.

---

## Example Output

```json
"Env": [
  "DB_HOST=mysql",
  "DB_USER=admin"
],
"Mounts": [
  "/data"
],
"RestartPolicy": {
  "Name": "always"
}
```

---

## What `docker inspect` Helps You Identify

With a single command, you can quickly determine:

- ✅ Environment variables
- ✅ Mounted volumes
- ✅ Network configuration
- ✅ IP address
- ✅ Restart policy
- ✅ Entrypoint
- ✅ Image details
- ✅ Port mappings

This gives you everything you need to verify how the container was configured.

---

## 💡 Real-World DevOps Workflow

When a container exits immediately after starting, follow this troubleshooting workflow:

```text
Container Exits
      │
      ▼
docker ps -a
      │
      ▼
docker logs myapp
      │
      ▼
docker inspect myapp
      │
      ▼
Identify Configuration Issues
      │
      ▼
Fix the Root Cause
```

Useful commands during investigation:

```bash
docker ps -a
docker logs myapp
docker inspect myapp
```

> **Note:** Use `docker inspect` after reviewing the logs to verify the container's configuration, including environment variables, mounts, networking, and restart policy.

---

## 🚨 Common Mistake

Many beginners immediately try:

```bash
docker exec -it myapp /bin/bash
```

However, if the container exits immediately, there is **no running process** to attach to, so the command usually fails.

Always verify the container's status and inspect its configuration before attempting to access it interactively.

---

## ❌ Why the Other Options Are Incorrect

### A.

```bash
docker logs myapp
```

- ✅ Displays application logs.
- ❌ Does not show the container's configuration.

### C.

```bash
docker exec -it myapp /bin/bash
```

- ✅ Opens a shell inside a running container.
- ❌ Fails if the container has already exited.

> **This is the trick in the question.**

### D.

```bash
docker images
```

- ✅ Lists available Docker images.
- ❌ Provides no information about a specific container's configuration.

---

## 🎯 Interview Tip

Remember these essential Docker commands:

```bash
docker ps
```

👉 View running containers.

```bash
docker logs <container>
```

👉 View application logs.

```bash
docker inspect <container>
```

👉 View complete container configuration.

```bash
docker exec -it <container> /bin/bash
```

👉 Open a shell inside a running container.

Understanding the purpose of each command is a common Docker interview topic.

---

## 🚨 Real Production Tip

If `docker inspect` shows:

```json
"RestartPolicy": {
  "Name": "always"
}
```

and the container keeps restarting, investigate further:

- 🔍 What error is shown in `docker logs`?
- 🔍 Are the required environment variables configured?
- 🔍 Are the mounted volumes available?
- 🔍 Is the entrypoint command correct?
- 🔍 Can the container reach its dependent services (database, API, etc.)?

Don't disable the restart policy until you've identified the root cause.

---

## 🎯 Key Takeaway

When you need to inspect a container's **configuration**, use **`docker inspect <container>`**.

It provides detailed information about environment variables, mounts, networking, restart policy, entrypoint, and other configuration settings, making it one of the most valuable commands for troubleshooting Docker containers.
