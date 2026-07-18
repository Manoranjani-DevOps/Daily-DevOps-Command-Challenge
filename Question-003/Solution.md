# ✅ Solution

## Correct Answer

## **B. `tail -f /var/log/app.log`**

The requirement is:

> **"Continuously monitor new log entries."**

The `tail -f` command displays the last few lines of a log file and keeps following the file, showing new log entries in real time as they are written.

```bash
tail -f /var/log/app.log
```

---

## Example

```text
10:01 User Login
10:02 Payment Started
10:03 Payment Successful
10:04 User Logout
```

As new logs are generated, they appear automatically:

```text
10:05 Order Created
10:05 Payment Failed
10:06 Retry Successful
```

No need to rerun the command—it's ideal for real-time monitoring.

---

## What `tail -f` Helps You Identify

With a single command, you can:

- ✅ Monitor log files in real time
- ✅ View new log entries as they are written
- ✅ Troubleshoot application issues instantly
- ✅ Verify deployments without repeatedly opening the log file

---

## 💡 Real-World DevOps Workflow

During a production deployment, engineers often monitor multiple terminals simultaneously.

**Terminal 1**

```bash
kubectl rollout status deployment/payment-api
```

**Terminal 2**

```bash
tail -f /var/log/nginx/access.log
```

**Terminal 3**

```bash
tail -f /var/log/nginx/error.log
```

This helps verify that the deployment is progressing successfully while monitoring live application traffic and errors.

---

## 🚨 Common Mistake

Many beginners use:

```bash
cat /var/log/app.log
```

This simply prints the contents of the file once and exits.

It does **not** display new log entries as they are written.

---

## 💡 Bonus Commands

To display the last **100 lines** and continue monitoring:

```bash
tail -100f /var/log/app.log
```

Or, using the more explicit syntax:

```bash
tail -n 100 -f /var/log/app.log
```

Both commands are commonly used in production environments when you need more log history before following new entries.

---

## 🎯 Interview Tip

If you're asked:

> **"How do you monitor an application's log file in real time?"**

A strong answer is:

```bash
tail -f /var/log/app.log
```

If you need more historical log lines before monitoring begins:

```bash
tail -n 100 -f /var/log/app.log
```

---

## 🚨 Real Production Tip

While troubleshooting production issues, monitor multiple logs simultaneously.

For example:

- 🔍 Application logs
- 🔍 Nginx access logs
- 🔍 Nginx error logs
- 🔍 System logs

Watching these together helps quickly identify whether failures are caused by the application, web server, or infrastructure.

---

## 🎯 Key Takeaway

When you need to **continuously monitor a log file**, always use **`tail -f`**.

It displays the latest log entries and automatically updates the output as new events occur, making it one of the most commonly used commands for real-time troubleshooting in Linux, DevOps, and SRE environments.
