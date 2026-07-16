# ✅ Solution

## Correct Answer

**A. `top`**

When a server becomes slow, you don't yet know the root cause. The issue could be due to:

* 🔥 High CPU usage
* 💾 Memory exhaustion
* ⚠️ A runaway process
* 📈 High load average

The first step is to get a **real-time overview of the system**, and the best command for this is:

```bash
top
```

---

## Example Output

```text
top - 10:15:01
Tasks: 312 total
%Cpu(s): 98.5 us
MiB Mem : 7980 total, 120 free
Load average: 14.52
```

---

## What `top` Helps You Identify

With a single command, you can quickly view:

* ✅ CPU utilization
* ✅ Memory usage
* ✅ Load average
* ✅ Processes consuming the most system resources

---

## 💡 Real-World DevOps Workflow

Start your troubleshooting with:

```bash
top
```

If further investigation is needed, use the following commands:

```bash
htop      # Better interactive view (if installed)
ps -ef    # List all running processes
free -m   # Check memory usage in MB
vmstat    # View system performance statistics
iostat    # Monitor CPU and disk I/O statistics
```

---

## 🚨 Common Mistake

Many beginners immediately run:

```bash
df -h
```

However, **disk usage is not always the cause of a slow server**.

A better troubleshooting approach is:

1. Identify which system resource is under pressure (CPU, memory, processes, or load).
2. Use the appropriate command to investigate further.
3. Resolve the actual bottleneck instead of making assumptions.

---

## 🎯 Key Takeaway

When troubleshooting a slow Linux server, **always begin with `top`**. It provides a real-time snapshot of system performance and helps you quickly determine whether the issue is related to CPU, memory, load, or a resource-intensive process.
