# ✅ Solution

## Correct Answer

## **D. `journalctl -u nginx`**

You already know:

```bash
systemctl status nginx
```

returned:

```text
Active: failed (Result: exit-code)
```

This tells you **that the Nginx service has failed**, but it doesn't tell you **why**.

The next step is to inspect the service logs:

```bash
journalctl -u nginx
```

---

## Example Output

```text
nginx: [emerg] bind() to 0.0.0.0:80 failed
```

or

```text
nginx: invalid configuration in /etc/nginx/nginx.conf
```

or

```text
Permission denied
```

Now you have the **actual root cause**, allowing you to fix the issue instead of guessing.

---

## What `journalctl -u nginx` Helps You Identify

With a single command, you can quickly determine:

- ✅ Why the Nginx service failed
- ✅ Configuration errors
- ✅ Port binding conflicts
- ✅ Permission issues
- ✅ Startup failures
- ✅ Recent service log entries

---

## 💡 Real-World DevOps Workflow

When a website suddenly becomes unavailable, follow this troubleshooting workflow:

```text
Website Down
      │
      ▼
systemctl status nginx
      │
      ▼
journalctl -u nginx
      │
      ▼
Identify the Error
      │
      ▼
Fix the Root Cause
      │
      ▼
systemctl restart nginx
```

Useful commands during investigation:

```bash
systemctl status nginx
journalctl -u nginx
nginx -t
systemctl restart nginx
```

> **Note:** Always validate the Nginx configuration with `nginx -t` before restarting the service after making configuration changes.

---

## 🚨 Common Mistake

Many beginners immediately run:

```bash
systemctl restart nginx
```

or even:

```bash
reboot
```

Restarting or rebooting may temporarily restart services, but it **doesn't fix configuration errors, port conflicts, or permission issues**.

Always identify the **root cause** before taking corrective action.

---

## 🎯 Interview Tip

When you see:

```text
Active: failed (Result: exit-code)
```

Your next thought should be:

```bash
journalctl -u nginx
```

You can also use:

```bash
systemctl status nginx -l
```

to display more detailed status information, including longer error messages.

---

## 🚨 Real Production Tip

If the logs show:

```text
nginx: [emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)
```

Don't restart Nginx repeatedly.

Instead:

- 🔍 Identify which process is using port **80**
- 🔍 Stop or reconfigure the conflicting service
- 🔍 Verify the Nginx configuration
- 🔍 Restart Nginx and confirm it starts successfully

This approach minimizes downtime and avoids unnecessary troubleshooting.

---

## 🎯 Key Takeaway

When a service shows **`Active: failed (Result: exit-code)`**, don't guess the cause.

Start with **`journalctl -u <service-name>`** to inspect the service logs and identify the exact reason for the failure. This evidence-based approach is a fundamental troubleshooting practice for Linux Administrators, SREs, and DevOps Engineers.
