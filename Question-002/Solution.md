# ✅ Solution

## Correct Answer

## **B. `ss -tulnp | grep :8080`**

This question is designed to test **practical troubleshooting skills**.

Both commands may seem correct, but one is more efficient.

The best first step is to verify whether the application is actually listening on **port 8080**.

```bash
ss -tulnp | grep :8080
```

---

## Why is B Better than A?

### Option A

```bash
netstat -tuln
```

✅ Displays network connections.

However:

- ❌ Shows all connections, making it harder to find what you're looking for.
- ❌ Doesn't display process information unless additional options (such as `-p`) are used.
- ❌ `netstat` is considered a legacy command on many modern Linux distributions.

---

### Option B

```bash
ss -tulnp | grep :8080
```

This command directly answers the question.

---

## Example Output

```text
LISTEN 0 511 *:8080 users:(("java",pid=2456,fd=123))
```

---

## What `ss -tulnp | grep :8080` Helps You Identify

With a single command, you can immediately determine:

- ✅ Whether port **8080** is listening
- ✅ Which process owns the port
- ✅ The Process ID (PID)
- ✅ The socket state (**LISTEN**)

This is the command commonly used by Linux Administrators, SREs, and DevOps Engineers on modern Linux systems.

---

## 💡 Real-World DevOps Workflow

Start your troubleshooting with:

```bash
ss -tulnp | grep :8080
```

If no output is returned, continue your investigation using:

```bash
systemctl status <service-name>
ps -ef | grep java
journalctl -u <service-name>
firewall-cmd --list-ports
```

---

## 🎯 Interview Tip

If you're asked:

> **"How do you check whether an application is listening on port 8080?"**

A strong answer is:

```bash
ss -tulnp | grep :8080
```

On older systems, you may still see:

```bash
netstat -tulnp
```

However, **`ss` is the modern replacement for `netstat`** and is generally preferred.

---

## 🚨 Real Production Tip

If the command returns **no output**, investigate further.

Ask yourself:

- 🔍 Did the application start successfully?
- 🔍 Is it listening on a different port?
- 🔍 Did the application fail to bind to port **8080**?
- 🔍 Is the service actually running?
- 🔍 Is a firewall blocking the port?

---

## 🎯 Key Takeaway

When troubleshooting application connectivity issues, always verify that the application is **actually listening on the expected port** before investigating network or firewall problems.

Using **`ss -tulnp | grep :8080`** quickly confirms whether the application is bound to the port and identifies the process responsible.
