# ✅ Solution

## Correct Answer

## **C. `lsof -i :8080`**

The problem isn't just checking whether **port 8080** is open.

The goal is to identify **which process is currently using that specific port**.

The following command provides exactly that information:

```bash
lsof -i :8080
```

---

## Example Output

```text
COMMAND   PID   USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
java      3245  root   45u  IPv4        TCP *:8080 (LISTEN)
```

---

## What `lsof -i :8080` Helps You Identify

With a single command, you can immediately determine:

- ✅ Process name (**java**)
- ✅ Process ID (**PID 3245**)
- ✅ The port in use (**8080**)
- ✅ The socket state (**LISTEN**)

Now you know exactly which process is preventing your application from starting.

---

## 💡 Real-World DevOps Workflow

Start by identifying the process using the port:

```bash
lsof -i :8080
```

Find more details about the process:

```bash
ps -fp 3245
```

If it's an unwanted process, stop it gracefully:

```bash
kill 3245
```

Only if the process refuses to terminate:

```bash
kill -9 3245
```

> ⚠️ **Production Rule:** Never use `kill -9` as your first option. Always try a normal `kill` first so the application can shut down gracefully.

---

## 🚨 Common Mistake

Many beginners immediately use:

```bash
kill -9 <PID>
```

Although this forcefully terminates the process, it doesn't allow the application to perform cleanup operations.

Always identify the process first and attempt a graceful shutdown before using `kill -9`.

---

## 🎯 Interview Tip

These three commands are commonly used when troubleshooting ports:

### Check listening ports

```bash
ss -tulnp
```

👉 Shows listening ports along with the associated processes on modern Linux systems.

### Older alternative

```bash
netstat -tulnp
```

👉 Similar to `ss`, but commonly found on older Linux distributions.

### Find the process using a specific port

```bash
lsof -i :8080
```

👉 Best when you want to identify **which process is using a specific port**.

If an interviewer asks:

> **"Which process is using port 8080?"**

A strong answer is:

```bash
lsof -i :8080
```

---

## 🚨 Real Production Tip

If your application fails to start because the port is already in use:

- 🔍 Identify the process using the port.
- 🔍 Verify whether it is the expected application.
- 🔍 Stop the unwanted process gracefully.
- 🔍 Restart your application and confirm that it successfully binds to the required port.

This approach minimizes downtime and avoids accidentally terminating critical services.

---

## 🎯 Key Takeaway

When troubleshooting **port conflicts**, use **`lsof -i :8080`** to identify exactly which process is using the port.

It provides the process name, PID, and socket details, allowing you to quickly determine why your application cannot bind to the required port and take the appropriate action.
