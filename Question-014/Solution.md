# ✅ Solution

## Correct Answer

## **C. `systemctl enable nginx`**

The requirement is:

> **"Ensure Nginx starts automatically after every server reboot."**

The correct command is:

```bash
systemctl enable nginx
```

This creates the necessary **systemd symlinks**, ensuring the service starts automatically whenever the server boots.

---

## Example

Enable the service:

```bash
systemctl enable nginx
```

Example output:

```text
Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service
```

Now the boot process looks like this:

```text
Server Boots
      │
      ▼
systemd Starts
      │
      ▼
Nginx Starts Automatically ✅
```

---

## What `systemctl enable` Helps You Do

With a single command, you can:

- ✅ Configure a service to start automatically during system boot
- ✅ Create the required systemd symlinks
- ✅ Ensure the service starts after every reboot
- ✅ Improve service availability after planned or unplanned restarts
- ✅ Eliminate the need to manually start the service after boot

---

## 💡 Real-World DevOps Workflow

After deploying a web server, a typical workflow looks like this:

```text
Deploy Application
      │
      ▼
Check Service Status
      │
      ▼
Enable Auto Start
      │
      ▼
Restart the Service
      │
      ▼
Verify Service Status
```

Example:

```bash
systemctl status nginx
systemctl enable nginx
systemctl restart nginx
systemctl status nginx
```

> **Note:** Enabling a service configures it to start automatically on future boots. It does **not** start the service immediately.

---

## 🚨 Common Mistake

Many beginners think:

```bash
systemctl restart nginx
```

will make the service start automatically after every reboot.

It won't.

`restart` only restarts the service **right now**. It does **not** modify the boot configuration.

To enable automatic startup after reboot, use:

```bash
systemctl enable nginx
```

---

## ❌ Why the Other Options Are Incorrect

### A.

```bash
systemctl stop nginx
```

- ❌ Stops the service immediately.
- ❌ Does not configure automatic startup.

### B.

```bash
systemctl restart nginx
```

- ✅ Restarts the service immediately.
- ❌ Does not enable the service during system boot.

### D.

```bash
systemctl disable nginx
```

- ❌ Removes the automatic startup configuration.
- ❌ Prevents the service from starting automatically after reboot.

---

## 🎯 Interview Tip

Remember these essential `systemctl` commands:

```bash
systemctl start nginx
```

👉 Start the service now.

```bash
systemctl stop nginx
```

👉 Stop the service now.

```bash
systemctl restart nginx
```

👉 Restart the service now.

```bash
systemctl enable nginx
```

👉 Configure the service to start automatically after every reboot.

```bash
systemctl disable nginx
```

👉 Disable automatic startup during boot.

Understanding the difference between **starting** a service and **enabling** a service is a very common Linux and DevOps interview topic.

---

## 🚨 Real Production Tip

If you want to **start the service immediately** and also **enable it for future reboots**, use:

```bash
systemctl enable --now nginx
```

This single command:

- ✅ Starts the service immediately.
- ✅ Configures it to start automatically after every server reboot.

It's a common command used by Linux Administrators, SREs, and DevOps Engineers during production deployments.

---

## 🎯 Key Takeaway

When you want a service to **start automatically after every server reboot**, use:

```bash
systemctl enable <service-name>
```

If you also want to **start the service immediately**, use:

```bash
systemctl enable --now <service-name>
```

Understanding the difference between **`start`**, **`restart`**, and **`enable`** is a fundamental Linux administration skill and an important DevOps interview topic.
