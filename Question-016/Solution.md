# ✅ Solution

## Correct Answer

## **D. `uptime`**

The requirement is simple:

> **"How long has the server been running since its last reboot?"**

The correct command is:

```bash
uptime
```

This command provides a quick overview of the server's uptime and current system load.

---

## Example Output

```text
10:15:42 up 15 days, 4:32, 2 users, load average: 0.25, 0.40, 0.35
```

---

## What `uptime` Helps You Identify

With a single command, you can immediately determine:

- ✅ Current system time
- ✅ Server uptime
- ✅ Number of logged-in users
- ✅ Load average (1, 5, and 15 minutes)

This makes `uptime` one of the quickest ways to assess a Linux server's overall health.

---

## 💡 Real-World DevOps Workflow

During a production incident, one of the first questions is:

> **"Did the server recently reboot?"**

A typical troubleshooting workflow is:

```text
Production Alert
        │
        ▼
SSH into the Server
        │
        ▼
uptime
        │
        ▼
Check Uptime & Load Average
        │
        ▼
Investigate Further (if required)
```

If the output shows:

```text
up 5 minutes
```

You immediately know the server has rebooted recently.

This could explain why:

- Services are still starting
- Scheduled jobs haven't run yet
- An outage occurred after a reboot
- The system is still recovering

---

## 🚨 Common Mistake

Many beginners think `uptime` only displays how long the server has been running.

However, it also displays the **system load average**, which is an important performance metric.

Example:

```text
load average: 1.25, 0.95, 0.80
```

Ignoring the load average means missing valuable information about the server's workload.

---

## ❌ Why the Other Options Are Incorrect

### A.

```bash
ps -ef
```

- ✅ Lists all running processes.
- ❌ Does not show server uptime.

### B.

```bash
free -m
```

- ✅ Displays memory usage.
- ❌ Does not provide uptime information.

### C.

```bash
df -h
```

- ✅ Displays disk usage.
- ❌ Does not tell you how long the server has been running.

---

## 🎯 Interview Tip

A common interview question is:

> **"What do the three load average values shown by `uptime` represent?"**

They represent the average system load over the last:

- ✅ 1 minute
- ✅ 5 minutes
- ✅ 15 minutes

A consistently high load average may indicate that:

- CPU resources are overloaded.
- Processes are waiting for CPU time.
- The system is under heavy resource pressure.

Remember this quick Linux command mapping:

| Need to Check | Command |
|---------------|---------|
| 🕒 Server Uptime | `uptime` |
| 💾 Disk Usage | `df -h` |
| 🧠 Memory Usage | `free -m` |
| ⚙️ CPU & Processes | `top` |
| 📋 Running Processes | `ps -ef` |
| 🌐 Listening Ports | `ss -tulnp` |

---

## 🚨 Real Production Tip

If `uptime` shows:

```text
load average: 18.50, 17.80, 16.95
```

on a server with **4 CPU cores**, investigate further:

- 🔍 Is the CPU overloaded?
- 🔍 Which processes are consuming the most CPU?
- 🔍 Is the server experiencing unusually high traffic?
- 🔍 Are applications stuck or waiting on resources?
- 🔍 Should the workload be optimized or scaled?

Use commands such as:

```bash
top
```

or

```bash
ps -eo pid,ppid,cmd,%cpu --sort=-%cpu | head
```

to identify the processes responsible for the high system load.

---

## 🎯 Key Takeaway

When you need to know **how long a Linux server has been running** since its last reboot, use:

```bash
uptime
```

In addition to server uptime, it also displays the current system time, logged-in users, and load averages, making it one of the most valuable commands for quickly assessing a server's health during production troubleshooting.
