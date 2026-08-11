# ✅ Solution

## Correct Answer

## **B. `git fetch`**

The key requirement is:

> **"Download the latest changes, but DON'T merge them."**

The correct command is:

```bash
git fetch
```

---

## What Happens?

```text
Remote Repository
        │
        ▼
Downloads Latest Commits ✅
        │
        ▼
Updates Remote-Tracking Branches ✅
        │
        ▼
Does NOT Modify Your Current Branch ✅
```

This allows you to review the incoming changes before deciding whether to merge or rebase them.

---

## What `git fetch` Helps You Do

With a single command, you can:

- ✅ Download the latest commits from the remote repository
- ✅ Update remote-tracking branches
- ✅ Keep your current branch unchanged
- ✅ Review incoming changes before merging
- ✅ Decide whether to merge or rebase

This makes `git fetch` one of the safest commands for synchronizing with a remote repository.

---

## 💡 Real-World DevOps Workflow

Before starting work each day, many developers follow this workflow:

```bash
git fetch
git log origin/main
git diff HEAD origin/main
```

After reviewing the changes, they decide how to integrate them:

```bash
git merge origin/main
```

or

```bash
git rebase origin/main
```

> **Note:** `git fetch` gives you full control over when and how remote changes are applied.

---

## 🚨 Common Mistake

Many beginners think:

```bash
git pull
```

only downloads changes.

In reality:

```text
git pull
      │
      ▼
git fetch
      +
git merge
```

So `git pull`:

- ✅ Downloads the latest changes
- ❌ Immediately merges them into your current branch

If you want to inspect changes before merging, always use:

```bash
git fetch
```

---

## ❌ Why the Other Options Are Incorrect

### A.

```bash
git pull
```

- ✅ Downloads remote changes.
- ✅ Automatically merges them into your current branch.
- ❌ Not suitable when you want to review changes first.

### C.

```bash
git clone
```

- ✅ Creates a new local copy of a repository.
- ❌ Not used to update an existing repository.

### D.

```bash
git init
```

- ✅ Initializes a new Git repository.
- ❌ Does not communicate with a remote repository.

---

## 🎯 Interview Tip

Remember this simple distinction:

```text
git fetch
      │
      ▼
"Bring the changes to me."
```

```text
git pull
      │
      ▼
"Bring the changes and apply them."
```

This is one of the most frequently asked Git interview concepts.

---

## 💡 Quick Git Workflow

| Task | Command |
|------|---------|
| Check current changes | `git status` |
| Review file changes | `git diff` |
| View commit history | `git log` |
| Download remote changes | `git fetch` |
| Download & merge changes | `git pull` |
| Upload local commits | `git push` |

---

## 🚨 Real Production Tip

After running:

```bash
git fetch
```

Before merging, always verify:

- 🔍 What new commits are available?
- 🔍 Which files have changed?
- 🔍 Will the merge cause conflicts?
- 🔍 Is a rebase a better option than a merge?

Useful commands:

```bash
git log origin/main
git diff HEAD origin/main
```

Reviewing changes before merging helps prevent unexpected conflicts and keeps your branch history clean.

---

## 🎯 Key Takeaway

When you want to **download the latest changes from a remote repository without modifying your current branch**, use:

```bash
git fetch
```

It updates your remote-tracking branches while leaving your local branch untouched, allowing you to review incoming changes before deciding whether to merge or rebase.
