# ✅ Solution

## Correct Answer

## **C. `systemctl status nginx`**

You've already proved several important things:

- ✅ You can SSH into the EC2 instance.
- ✅ The instance is running and reachable.
- ✅ The network path for SSH is working.

Then you run:

```bash
curl http://localhost
```

and receive:

```text
curl: (7) Failed to connect to localhost port 80: Connection refused
```

This tells you that **nothing is listening on port 80**.

The next logical step is to check whether the web server is running:

```bash
systemctl status nginx
```

---

## Example Output

```text
● nginx.service - A high performance web server
   Loaded: loaded (/lib/systemd/system/nginx.service)
   Active: failed (Result: exit-code)
```

or

```text
Active: inactive (dead)
```

or an error indicating that Nginx failed to start due to a configuration issue.

Now you know why the website isn't serving requests.

---

## What `systemctl status nginx` Helps You Identify

With a single command, you can quickly determine:

- ✅ Whether the Nginx service is running
- ✅ Whether the service has failed or stopped
- ✅ Recent service error messages
- ✅ The service exit status
- ✅ Whether further log analysis is required

---

## 💡 Real-World DevOps Workflow

When a website hosted on an EC2 instance becomes unavailable, follow this troubleshooting workflow:

```text
Website Down
      │
      ▼
SSH into the Server ✅
      │
      ▼
curl http://localhost ❌
      │
      ▼
Check Web Server Status
      │
      ▼
Check Service Logs
      │
      ▼
Fix the Root Cause
```

Useful commands during investigation:

```bash
ssh ubuntu@server
curl http://localhost
systemctl status nginx
journalctl -u nginx
ss -tulnp | grep :80
```

> **Note:** Check the service status before attempting to restart it. Understanding *why* the service failed is more valuable than simply restarting it.

---

## 🚨 Common Mistake

Many beginners immediately run:

```bash
systemctl restart nginx
```

or even reboot the EC2 instance.

Restarting the service or server may temporarily restore the application, but it **doesn't identify the underlying problem**.

Always investigate the service status first, then examine the logs if necessary.

---

## 🎯 Interview Tip

A common interview question is:

> **"A website hosted on an EC2 instance is not opening. How would you troubleshoot it?"**

A strong answer is:

```text
1. SSH into the server
2. curl http://localhost
3. systemctl status nginx
4. journalctl -u nginx
5. ss -tulnp | grep :80
```

This demonstrates a logical, production-ready troubleshooting workflow that isolates the root cause step by step.

---

## 🚨 Real Production Tip

If `systemctl status nginx` shows:

```text
Active: active (running)
```

but

```bash
curl http://localhost
```

still returns:

```text
Connection refused
```

Investigate further:

- 🔍 Is Nginx listening on port **80**?
- 🔍 Is the configuration valid (`nginx -t`)?
- 🔍 Is another process using port **80**?
- 🔍 Is the application configured to listen on a different port?
- 🔍 Are firewall or security group rules blocking traffic?

Never assume the service is healthy simply because it's running.

---

## 🎯 Key Takeaway

When `curl http://localhost` returns **"Connection refused"**, your next step should be **`systemctl status nginx`**.

It confirms whether the web server is running and provides valuable information about its current state, helping you determine the next troubleshooting step instead of making assumptions or restarting services blindly.
