# ✅ Solution

## Correct Answer

## **A. `ps -ef`**

The requirement is simple:

> **"Show me all running processes on the server."**

The correct command is:

```bash
ps -ef
```

This command displays every running process on the Linux system.

---

## Example Output

```text
UID        PID   PPID  C STIME TTY      TIME     CMD
root         1      0  0 Jul20 ?        00:00:02 /sbin/init
root       865      1  0 Jul20 ?        00:00:01 sshd
ubuntu    4521   4500 98 10:15 ?        00:12:45 java -jar payment-api.jar
mysql     1020      1  1 Jul20 ?        00:01:20 mysqld
```

---

## What `ps -ef` Helps You Identify

With a single command, you can quickly determine:

- ✅ All running processes
- ✅ Process ID (PID)
- ✅ Parent Process ID (PPID)
- ✅ User running the process
- ✅ Command used to start the process

This makes `ps -ef` one of the most commonly used Linux troubleshooting commands.

---

## 💡 Real-World DevOps Workflow

A user reports:

> **"The application is consuming high CPU."**

A DevOps Engineer might investigate like this:

```text
top
   │
   ▼
Identify High CPU Process
   │
   ▼
ps -ef
   │
   ▼
ps -fp <PID>
```

For example:

```bash
ps -fp 4521
```

This displays detailed information about the specific process you're investigating.

Useful commands during investigation:

```bash
top
ps -ef
ps -fp <PID>
```

> **Note:** `top` helps identify resource-intensive processes, while `ps` provides detailed process information.

---

## 🚨 Common Mistake

Many beginners try to manually search through hundreds of running processes.

Instead, combine `ps` with `grep` to quickly locate a specific application.

Example:

```bash
ps -ef | grep nginx
```

or

```bash
ps -ef | grep java
```

This is a common practice in production environments.

---

## ❌ Why the Other Options Are Incorrect

### B.

```bash
free -m
```

- ✅ Displays memory usage.
- ❌ Doesn't list running processes.

### C.

```bash
df -h
```

- ✅ Displays disk usage.
- ❌ Doesn't provide process information.

### D.

```bash
uptime
```

- ✅ Shows server uptime and load average.
- ❌ Doesn't display running processes.

---

## 🎯 Interview Tip

Know the purpose of these essential Linux commands:

```bash
ps -ef
```

👉 List all running processes.

```bash
top
```

👉 Monitor CPU, memory, and processes in real time.

```bash
ps -fp <PID>
```

👉 Display detailed information about a specific process.

These commands are frequently used together during production troubleshooting.

---

## 🚨 Real Production Tip

When troubleshooting a production application:

1. Identify the high CPU or memory process using:

```bash
top
```

2. View complete process details:

```bash
ps -fp <PID>
```

3. If necessary, stop the process gracefully:

```bash
kill <PID>
```

Only use:

```bash
kill -9 <PID>
```

if the process refuses to terminate normally.

---

## 🎯 Key Takeaway

When you need to **view all currently running processes** on a Linux server, use:

```bash
ps -ef
```

It provides a complete list of active processes, including their PID, PPID, owner, and startup command, making it an essential command for Linux administration, DevOps, and production troubleshooting.
