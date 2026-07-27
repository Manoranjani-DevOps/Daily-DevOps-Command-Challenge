# ✅ Solution

## Correct Answer

## **A. `git reset HEAD config.yml`**

Current situation:

```bash
git add config.yml
```

The file is now in:

```text
Working Directory   ✅
Staging Area        ✅
Repository          ❌
```

The developer says:

> **"I staged the wrong file, but I don't want to lose my changes."**

The correct command is:

```bash
git reset HEAD config.yml
```

This removes the file from the **staging area** while keeping all your local modifications intact.

The file simply moves from:

```text
Staging Area
      │
      ▼
Working Directory
```

---

## Example

### Before

```bash
git status
```

Output:

```text
Changes to be committed:
    modified: config.yml
```

Run:

```bash
git reset HEAD config.yml
```

### After

```bash
git status
```

Output:

```text
Changes not staged for commit:
    modified: config.yml
```

- ✅ Your changes are still safe.
- ✅ The file has simply been unstaged.

---

## What `git reset HEAD <file>` Helps You Do

With a single command, you can:

- ✅ Remove a file from the staging area
- ✅ Keep all local changes intact
- ✅ Correct accidental staging
- ✅ Review or modify the file before committing
- ✅ Avoid unwanted files in your next commit

---

## 💡 Real-World DevOps Workflow

When working on multiple configuration files, it's common to accidentally stage the wrong one.

A typical workflow looks like this:

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
git add .
      │
      ▼
Oops! Wrong File Staged
      │
      ▼
git reset HEAD <file>
      │
      ▼
Verify with git status
      │
      ▼
Commit the Correct Files
```

Example:

```bash
git status
git diff
git add .
git status
git reset HEAD config.yml
git status
git commit -m "Fix payment service configuration"
git push
```

---

## 🚨 Common Mistake

Many beginners confuse **unstaging** with **deleting**.

Running:

```bash
git rm config.yml
```

or

```bash
rm config.yml
```

can remove the file instead of simply removing it from the staging area.

If you only want to unstage the file while keeping your work, use:

```bash
git reset HEAD config.yml
```

---

## ❌ Why the Other Options Are Incorrect

### B.

```bash
git rm config.yml
```

- ❌ Removes the file from Git tracking.
- ❌ By default, also deletes it from your working directory.

### C.

```bash
rm config.yml
```

- ❌ Deletes the file from your local machine.
- ❌ Does not unstage the file.

### D.

```bash
git clean -f
```

- ❌ Deletes untracked files from the working directory.
- ❌ Has a completely different purpose.

---

## 🎯 Interview Tip

Remember these three Git operations:

```bash
git add
```

👉 Stage changes.

```bash
git reset HEAD <file>
```

👉 Unstage changes while keeping your local modifications.

```bash
git restore <file>
```

👉 Discard local changes and restore the last committed version.

Many candidates confuse **unstaging** with **deleting**. Understanding the difference is a common Git interview topic.

> **💡 Modern Git Tip:**  
> In newer versions of Git, you can also use:

```bash
git restore --staged config.yml
```

This is the newer, more explicit command for unstaging a file.

---

## 🚨 Real Production Tip

Before every commit:

- 🔍 Verify which files are staged using `git status`
- 🔍 Review changes using `git diff`
- 🔍 Unstage any accidental files
- 🔍 Commit only the intended changes

This helps prevent sensitive configuration files, temporary changes, or incomplete work from being committed to the repository.

---

## 🎯 Key Takeaway

When you've accidentally staged the wrong file, use **`git reset HEAD <file>`** to remove it from the staging area **without losing your local changes**.

In modern Git versions, **`git restore --staged <file>`** provides the same functionality with clearer intent, but `git reset HEAD <file>` remains a widely used command that every DevOps Engineer should know.
