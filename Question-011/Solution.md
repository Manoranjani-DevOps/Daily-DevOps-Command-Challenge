# ✅ Solution

## Correct Answer

## **A. `free -m`**

The complaint is:

> **"The server suddenly ran out of memory."**

The first step is to check the server's memory usage.

Run:

```bash
free -m
```

---

## Example Output

```text
              total   used   free   shared   buff/cache   available
Mem:           7972   7450    120       55          402          310
Swap:          2048   2048      0
```

---

## What `free -m` Helps You Identify

With a single command, you can quickly determine:

- ✅ Total RAM
- ✅ Used RAM
- ✅ Free RAM
- ✅ Available memory
- ✅ Swap usage

This immediately tells you whether the server is under memory pressure.

---

## 💡 Real-World DevOps Workflow

When a server reports high memory usage, follow this troubleshooting workflow:

```text
Memory Alert
      │
      ▼
free -m
      │
      ▼
Check Overall Resource Usage
      │
      ▼
top
      │
      ▼
Identify Memory-Heavy Processes
      │
      ▼
Take Appropriate Action
```

Useful commands during investigation:

```bash
free -m
top
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head
```

> **Note:** Start with `free -m` to confirm memory pressure before investigating which processes are consuming RAM.

---

## 🚨 Common Mistake

Many beginners hear:

> **"The server has an issue."**

…and immediately run:

```bash
df -h
```

While `df -h` is an important command, it displays **disk usage**, **not memory usage**.

Always choose the command based on the resource you're troubleshooting.

---

## ❌ Why the Other Options Are Incorrect

### B.

```bash
df -h
```

- ❌ Displays filesystem and disk usage.
- ❌ Does not provide memory information.

### C.

```bash
pwd
```

- ❌ Displays the current working directory.
- ❌ Not related to system resources.

### D.

```bash
ls -l
```

- ❌ Lists files and directories.
- ❌ Does not display memory usage.

---

## 🎯 Interview Tip

Remember this quick mapping:

| Resource | Command |
|----------|---------|
| 💾 Disk Usage | `df -h` |
| 🧠 Memory Usage | `free -m` |
| ⚙️ CPU & Processes | `top` |
| 🌐 Listening Ports | `ss -tulnp` |

Mastering these basic Linux commands will help you troubleshoot production servers efficiently and answer many common DevOps interview questions.

---

## 🚨 Real Production Tip

If `free -m` shows:

```text
Free Memory : 0 MB
Swap        : 100% Used
```

Investigate further:

- 🔍 Which process is consuming the most memory?
- 🔍 Is there a memory leak?
- 🔍 Has an application recently deployed?
- 🔍 Is the system experiencing Out Of Memory (OOM) kills?
- 🔍 Is additional RAM or application optimization required?

Avoid rebooting the server before identifying the root cause.

---

## 🎯 Key Takeaway

When troubleshooting memory-related issues, always start with **`free -m`**.

It provides a quick, human-readable summary of RAM and swap usage, helping you confirm whether the server is experiencing memory pressure before moving on to process-level investigation.
