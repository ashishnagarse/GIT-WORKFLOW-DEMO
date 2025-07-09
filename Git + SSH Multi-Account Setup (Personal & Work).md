# 🔐 Git + SSH Multi-Account Setup (Personal & Work)

This guide walks you through setting up **two different GitHub accounts** (e.g. personal + work) on a single machine using **SSH keys**, and configuring Git to switch between them per project.

---

## 🧱 Goal

- Manage two GitHub accounts on one machine (e.g., `johndoe` for personal and `doe-enterprise` for work)
- Use separate SSH keys and Git identities
- Avoid credential conflicts

---

## 🔑 Step 1: Generate SSH Keys

### Personal:
```bash
ssh-keygen -t ed25519 -C "john.doe@example.com"
# Save as: /c/Users/youruser/.ssh/id_ed25519_personal
````

### Work:

```bash
ssh-keygen -t ed25519 -C "john.doe@company.com"
# Save as: /c/Users/youruser/.ssh/id_ed25519_work
```

Optionally enter a passphrase for security. you can just press enter to skip it.

---

## 🧠 Step 2: Add SSH Keys to the Agent

Start the agent and add both keys:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519_personal
ssh-add ~/.ssh/id_ed25519_work
```

---

## ⚙️ Step 3: Configure SSH Aliases

Create or edit `~/.ssh/config`:

```bash
nano ~/.ssh/config
```

Add:

```ssh
# Personal GitHub
Host github.com-personal
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_personal
  IdentitiesOnly yes

# Work GitHub
Host github.com-work
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_work
  IdentitiesOnly yes

Save and exit:
In nano: Press Ctrl + O to save, then Enter, then Ctrl + X to exit.
```

---

## 🌐 Step 4: Add Public Keys to GitHub

### Personal:

```bash
cat ~/.ssh/id_ed25519_personal.pub
```

* Go to GitHub → **Settings > SSH and GPG keys** → Add New Key

### Work:

```bash
cat ~/.ssh/id_ed25519_work.pub
```

* Go to GitHub (work account) → Add to SSH keys

---

## 🧪 Step 5: Test SSH Authentication

### Personal:

```bash
ssh -T git@github.com-personal
```

### Work:

```bash
ssh -T git@github.com-work
```

Expected output:

```
Hi johndoe! You've successfully authenticated, but GitHub does not provide shell access.
```

---

## 📁 Step 6: Create and Configure a Git Repo

```bash
mkdir test-project && cd test-project
git init
touch README.md .gitignore
git add .
git commit -m "Initial commit"
```

Set user identity (per repo):

```bash
git config user.name "John Doe"
git config user.email "john.doe@example.com"
```

---

## 🔗 Step 7: Link to the Correct GitHub Remote

### Create a GitHub repo (e.g., `test-project`) on your **personal** GitHub.

Add the remote using the SSH alias:

```bash
git remote add origin git@github.com-personal:johndoe/test-project.git
```

Verify:

```bash
git remote -v
```

---

## 🚀 Step 8: Push Code

```bash
git push -u origin main
```

✅ If everything is configured properly, your project will be pushed to the correct GitHub account.

---

## 🛠️ Common Errors & Fixes

| ❌ Error                                           | ✅ Fix                                                              |
| ------------------------------------------------- | ------------------------------------------------------------------ |
| `Permission denied (publickey)`                   | Remote URL was using `github.com` instead of `github.com-personal` |
| `'origin' does not appear to be a git repository` | Forgot to add a remote                                             |
| `branch has no upstream`                          | Use `git push -u origin main`                                      |
| `GitHub does not provide shell access`            | This is normal — just confirms successful auth                     |

---

## 🧼 Useful Commands

| Purpose              | Command                                          |
| -------------------- | ------------------------------------------------ |
| Check added SSH keys | `ssh-add -l`                                     |
| Check Git identity   | `git config user.name` / `git config user.email` |
| Change remote URL    | `git remote set-url origin <url>`                |
| View SSH config      | `cat ~/.ssh/config`                              |

---

## ✅ You're All Set!

You can now work with:

| Account  | Host Alias            | Remote Format                                 |
| -------- | --------------------- | --------------------------------------------- |
| Personal | `github.com-personal` | `git@github.com-personal:johndoe/repo.git`    |
| Work     | `github.com-work`     | `git@github.com-work:doe-enterprise/repo.git` |

---

Happy Git-ing! 🧑‍💻


