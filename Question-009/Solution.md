# ✅ Solution

## Correct Answer

## **C. `git diff`**

The key requirement is:

> **"Review the exact line-by-line changes before committing."**

The command you need is:

```bash
git diff
```

---

## Example Output

```diff
- server.port=8080
+ server.port=9090

- logging.level=INFO
+ logging.level=DEBUG
```

This clearly shows:

- ✅ Which lines were removed
- ✅ Which lines were added
- ✅ Exactly what will be committed if the changes are staged

Reviewing your changes before committing helps catch mistakes and prevents unnecessary code from reaching the repository.

---

## What `git diff` Helps You Identify

With a single command, you can quickly determine:

- ✅ Every line that has been modified
- ✅ Newly added lines
- ✅ Removed lines
- ✅ Configuration changes
- ✅ Code changes before staging or committing

---

## 💡 Real-World DevOps Workflow

Before every commit, a disciplined Git workflow looks like this:

```text
Modify Files
      │
      ▼
git status
      │
      ▼
git diff
      │
      ▼
Review Changes
      │
      ▼
git add .
      │
      ▼
git commit
      │
      ▼
git push
```

Example:

```bash
git status
git diff
git add .
git status
git commit -m "Fix payment bug"
git push
```

> **Note:** `git diff` acts as your final review before staging and committing changes.

---

## 🚨 Common Mistake

Many beginners only run:

```bash
git status
```

While it shows **which files have changed**, it **doesn't show what actually changed inside those files**.

Always review your modifications using:

```bash
git diff
```

before staging and committing your work.

---

## ❌ Why the Other Options Are Incorrect

### A.

```bash
git log
```

- ❌ Displays the commit history.
- ❌ Shows changes that have already been committed.
- ❌ Does not display your current local modifications.

### B.

```bash
git status
```

Example:

```text
Modified:
  app.py
  config.yml
```

- ✅ Shows which files have been modified.
- ❌ Does not display the line-by-line changes inside those files.

### D.

```bash
git branch
```

- ❌ Lists available branches.
- ❌ Indicates the current branch.
- ❌ Has nothing to do with reviewing file changes.

---

## 🎯 Interview Tip

Remember these three Git commands:

```bash
git status
```

👉 Which files have changed?

```bash
git diff
```

👉 What changed inside those files?

```bash
git log
```

👉 What has already been committed?

Understanding the difference between these commands is a common Git interview topic.

---

## 🚨 Real Production Tip

Before every commit:

- 🔍 Review your modified files using `git status`
- 🔍 Inspect the actual code changes using `git diff`
- 🔍 Stage only the required changes
- 🔍 Verify everything before committing

This practice helps prevent accidental commits, configuration mistakes, and unnecessary code changes from reaching production.

---

## 🎯 Key Takeaway

When you need to review **exactly what has changed** before committing, use **`git diff`**.

It provides a clear, line-by-line comparison of your local modifications, making it an essential command for writing clean, accurate, and production-ready commits.
