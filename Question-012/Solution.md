# ✅ Solution

## Correct Answer

## **C. `git log`**

The developer says:

> **"I already committed my changes locally."**

Once changes are committed, they become part of the Git commit history.

To review those commits, run:

```bash
git log
```

---

## Example Output

```text
commit a5f3d2b...
Author: Ammu
Date:   Sun Jul 20

    Fixed payment API timeout issue

commit c8d3f1a...
Author: Ammu

    Added Docker health check
```

Now the developer can:

- ✅ Review recent commits
- ✅ Decide whether to amend the latest commit
- ✅ Reset the commit (if required)
- ✅ Push the commit to the remote repository

---

## What `git log` Helps You Identify

With a single command, you can quickly determine:

- ✅ Commit history
- ✅ Commit messages
- ✅ Author information
- ✅ Commit dates
- ✅ Commit IDs (SHA hashes)

This helps you understand what has already been committed before making further changes.

---

## 💡 Real-World DevOps Workflow

When working with Git, a typical workflow looks like this:

```text
Modify Files
      │
      ▼
git diff
      │
      ▼
git add .
      │
      ▼
git commit
      │
      ▼
git log
      │
      ▼
Review Commit History
      │
      ▼
git push
```

Example:

```bash
git status
git diff
git add .
git commit -m "Fix payment API timeout"
git log
git push origin main
```

> **Note:** Reviewing your commit history before pushing helps ensure that the correct changes and commit messages are ready to be shared with the remote repository.

---

## 🚨 Common Mistake

Many beginners run:

```bash
git status
```

expecting to see their commit history.

However, `git status` only shows the current repository state—it **doesn't display previously committed changes**.

To review commits, always use:

```bash
git log
```

---

## ❌ Why the Other Options Are Incorrect

### A.

```bash
git status
```

- ✅ Shows modified, staged, and untracked files.
- ❌ Does not display commit history.

### B.

```bash
git diff
```

- ✅ Shows line-by-line changes that haven't been committed.
- ❌ Does not show previously committed changes.

### D.

```bash
git fetch
```

- ✅ Downloads the latest changes from the remote repository.
- ❌ Has nothing to do with viewing your local commit history.

---

## 🎯 Interview Tip

Remember this simple Git workflow:

```text
"I modified a file."
        │
        ▼
git diff

"I staged a file."
        │
        ▼
git status

"I committed my changes."
        │
        ▼
git log

"I want the latest changes from GitHub."
        │
        ▼
git fetch
```

Understanding which Git command matches each stage of the workflow is a common Git interview topic.

---

## 🚨 Real Production Tip

Before pushing your commits:

- 🔍 Review the commit history using `git log`
- 🔍 Verify the commit message is meaningful
- 🔍 Confirm that only the intended changes were committed
- 🔍 Check the commit ID if you need to amend or reset the commit

Taking a few seconds to review your commits can prevent unnecessary fixes, reverts, or incorrect changes from reaching the shared repository.

---

## 🎯 Key Takeaway

When you've already committed your changes and want to review your recent commit history, use **`git log`**.

It displays the complete commit history, including commit IDs, authors, dates, and messages, helping you verify your work before pushing it to GitHub.
