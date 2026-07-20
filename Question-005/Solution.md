# ✅ Solution

## Correct Answer

## **A. `du -sh /*`**

The command:

```bash
df -h
```

confirms that the disk is full.

```text
Filesystem      Size  Used Avail Use%
/dev/xvda1       20G   20G     0G 100%
```

However, **`df` only tells you that the filesystem is full—it doesn't tell you what is consuming the space.**

The next step is:

```bash
du -sh /*
```

---

## Example Output

```text
8.0G   /var
5.2G   /home
4.5G   /opt
500M   /tmp
```

Now you know that **`/var`** is consuming the most disk space.

Investigate further:

```bash
du -sh /var/*
```

You might discover:

```text
6.5G   /var/log
```

Then drill down even further:

```bash
ls -lh /var/log
```

or

```bash
du -sh /var/log/*
```

This helps you pinpoint the exact files or directories consuming disk space.

---

## What `du -sh /*` Helps You Identify

With a single command, you can quickly determine:

- ✅ Which top-level directory is consuming the most disk space
- ✅ Where to begin your investigation
- ✅ The size of each directory in a human-readable format
- ✅ The next location to drill down for detailed analysis

---

## 💡 Real-World DevOps Workflow

When an application team reports that the disk is full, a typical troubleshooting workflow is:

```text
Application Down
       │
       ▼
SSH into the Server
       │
       ▼
df -h
       │
       ▼
du -sh /*
       │
       ▼
Identify the Largest Directory
       │
       ▼
Find the Largest Files
       │
       ▼
Take Appropriate Action
```

---

## 🚨 Common Mistake

Many beginners stop after running:

```bash
df -h
```

While it confirms that the filesystem is full, it **doesn't reveal what is consuming the disk space**.

Always follow it with:

```bash
du -sh /*
```

to identify the largest directories before taking any action.

---

## ❌ Why the Other Options Are Incorrect

### B.

```bash
pwd
```

- ❌ Displays only the current working directory.
- ❌ Provides no information about disk usage.

### C.

```bash
free -m
```

- ❌ Displays memory usage.
- ❌ Not related to disk space.

### D.

```bash
ps -ef
```

- ❌ Lists running processes.
- ❌ Doesn't help identify disk usage.

---

## 🎯 Interview Tip

A common Linux disk troubleshooting sequence is:

```bash
df -h
```

➡️ Check which filesystem is full.

```bash
du -sh /*
```

➡️ Identify which top-level directory is consuming the most space.

```bash
du -sh /var/*
```

➡️ Narrow down the exact location.

This step-by-step approach is widely used by Linux Administrators, SREs, and DevOps Engineers during production incidents.

---

## 🎯 Key Takeaway

When a Linux filesystem becomes full, **`df -h`** tells you **which filesystem** has the problem, while **`du -sh /*`** tells you **which directories are consuming the space**.

Using these commands together helps you quickly locate the source of the issue and resolve disk space problems efficiently in production environments.
