# 🚀 Git Workflow Demo

This repository demonstrates the **step-by-step Git workflow** for solo or team development. Whether you're just getting started or need a reliable routine, this guide will help you stay organized and productive using Git and GitHub.

---

## 📦 Table of Contents

- [Getting Started](#getting-started)
- [Creating a Git Repository](#creating-a-git-repository)
- [Pushing Code to GitHub](#pushing-code-to-github)
- [Daily Workflow](#daily-workflow)
- [Handling Merge Conflicts](#handling-merge-conflicts)
- [Working with Branches](#working-with-branches)
- [Git Cheat Sheet](#git-cheat-sheet)
- [Bonus Tips](#bonus-tips)

---

## 🛠 Getting Started

Make sure Git is installed:

```bash
git --version

## 🧱 Creating a Git Repository

### 📁 If you already have a project folder:

```bash
cd your-project-folder/
git init
```

### 📁 If you want to start fresh:

```bash
mkdir your-project-folder
cd your-project-folder
git init
```

---

## 📝 Create Essential Files

```bash
touch README.md
touch .gitignore
```

Edit them as needed (use any text/code editor).

---

## 🌐 Pushing Code to GitHub

1. Create a new repo on GitHub (don’t initialize it with a README if you already created one locally).
2. Connect local to remote:

```bash
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/yourusername/your-repo.git
git branch -M main
git push -u origin main
```

---

## 🔁 Daily Workflow

### 👇 Before starting work:

Always pull the latest code to avoid conflicts:

```bash
git pull origin main
```

### 💻 Do your work

Make code changes, add new files, etc.

### ✅ Save your changes:

```bash
git add .
git commit -m "Your meaningful commit message"
```

### 📤 Push to GitHub:

```bash
git push origin main
```

---

## ⚔ Handling Merge Conflicts

When push is rejected due to remote changes:

```bash
git pull origin main  # May result in a conflict
```

If you get a conflict:

1. Open conflicted files
2. Resolve manually
3. Then:

```bash
git add .
git commit -m "Resolved merge conflict"
git push origin main
```

---

## 🌿 Working with Branches (Recommended for Teams)

### 🆕 Create a new branch:

```bash
git checkout -b feature/branch-name
```

### 💻 Do your work, then:

```bash
git add .
git commit -m "Describe your feature"
git push origin feature/branch-name
```

Go to GitHub → Create a **Pull Request** → Merge it into `main`.

---

## 📜 Git Cheat Sheet

```bash
# Setup
git init
git remote add origin <repo-url>
git branch -M main

# First Commit
git add .
git commit -m "Initial commit"
git push -u origin main

# Daily Routine
git pull origin main
git add .
git commit -m "Describe your changes"
git push origin main

# Feature Branch
git checkout -b feature/xyz
git push origin feature/xyz
```

---

## 💡 Bonus Tips

* Use `.gitignore` to exclude files/folders from version control (like `node_modules/`, `.env`, etc.)
* Use [GitHub Desktop](https://desktop.github.com/) or VS Code Git GUI for visual assistance.
* Use `git status` often to check the state of your working directory and staging area.
* Use `git log --oneline` for a concise commit history.

---

## 📬 Contact

Maintained by **Ashish Nagarse**
📧 [ashish.nagarse.2202@gmail.com](mailto:ashish.nagarse.2202@gmail.com)

---

> ⚡ Powered by Git — The most trusted version control system in the dev world.

```

---

Let me know if you'd like this saved as a file or tailored to a specific project type (like Node.js, Python, etc.)!
```
