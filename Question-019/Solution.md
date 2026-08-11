# ✅ Solution

## Correct Answer

## **A. `kubectl get pods -o wide`**

The requirement is:

> **"Which Kubernetes node is my Pod running on?"**

The command is:

```bash
kubectl get pods -o wide
```

The `-o wide` option provides additional information about each Pod, including the **Node** where it is running.

---

## Example Output

```text
NAME          READY   STATUS    IP            NODE
payment-api   1/1     Running   10.0.1.15     worker-node-2
frontend      1/1     Running   10.0.1.16     worker-node-1
redis         1/1     Running   10.0.1.17     worker-node-3
```

---

## What `kubectl get pods -o wide` Helps You Identify

With a single command, you can quickly determine:

- ✅ Pod Name
- ✅ Ready Status
- ✅ Pod Status
- ✅ Pod IP
- ✅ **Node where the Pod is running**

The key difference is the **`NODE`** column provided by `-o wide`.

---

## 💡 Real-World DevOps Workflow

When investigating where a Pod is running, start with:

```bash
kubectl get pods -o wide
```

Example:

```text
payment-api   1/1   Running   10.0.1.15   worker-node-2
```

Then, if the Pod is experiencing issues, investigate the node:

```bash
kubectl describe node worker-node-2
```

You can check for:

- 🔍 CPU pressure
- 🔍 Memory pressure
- 🔍 Disk pressure
- 🔍 Node conditions
- 🔍 Running workloads
- 🔍 Scheduling issues

---

## 🚨 Common Mistake

Many beginners run:

```bash
kubectl get nodes
```

This shows the available Kubernetes nodes, but it doesn't tell you **which Pod is running on which node**.

When the question is specifically about a Pod's location, use:

```bash
kubectl get pods -o wide
```

---

## ❌ Why the Other Options Are Incorrect

### B.

```bash
kubectl get nodes
```

Shows the Kubernetes nodes:

```text
NAME
worker-node-1
worker-node-2
worker-node-3
```

- ✅ Useful for checking node status.
- ❌ Doesn't tell you which Pod is running on which node.

### C.

```bash
kubectl get svc
```

- ✅ Shows Kubernetes Services.
- ❌ Not used to identify the node hosting a specific Pod.

### D.

```bash
kubectl get deploy
```

- ✅ Shows Kubernetes Deployments.
- ❌ Doesn't directly show the node where a specific Pod is running.

---

## 🎯 Interview Tip

Remember these Kubernetes commands:

```bash
kubectl get pods
```

👉 Basic Pod information.

```bash
kubectl get pods -o wide
```

👉 Pod information **+ IP + Node**.

```bash
kubectl describe pod <pod-name>
```

👉 Detailed information about a specific Pod.

### 🔥 Bonus

If you already know the Pod name and want to see its node directly:

```bash
kubectl get pod payment-api -o wide
```

Or use:

```bash
kubectl get pod payment-api -o jsonpath='{.spec.nodeName}'
```

This returns only the node name.

---

## 🚨 Real Production Tip

If a Pod is behaving differently from other replicas, first identify which node it is running on:

```bash
kubectl get pods -o wide
```

Then inspect the node:

```bash
kubectl describe node worker-node-2
```

You can also inspect the specific Pod:

```bash
kubectl describe pod payment-api
```

This helps determine whether the issue is related to the Pod itself or the underlying Kubernetes node.

---

## 🎯 Key Takeaway

When you need to know **which Kubernetes node is hosting a Pod**, use:

```bash
kubectl get pods -o wide
```

The `-o wide` output includes the **NODE** column, making it one of the quickest commands for locating Pods during Kubernetes troubleshooting.
