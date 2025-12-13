Got it 👍
Here’s a **complete, beginner-to-pro Git + GitHub command list with a clear step-by-step workflow** to **host files on GitHub**. This will cover **first-time setup**, **uploading files**, **updating files**, and **daily usage**.

I’ll keep it **practical**, exactly how you’d use it in real projects.

---

# 🔹 PART 1: One-Time Setup (Only Once)

### 1️⃣ Install Git

* Download: [https://git-scm.com/](https://git-scm.com/)
* Verify installation:

```bash
git --version
```

---

### 2️⃣ Configure Git (Important – One Time)

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@gmail.com"
```

Check config:

```bash
git config --list
```

---

# 🔹 PART 2: Create Repository on GitHub (Website)

1. Go to **github.com**
2. Click **New Repository**
3. Enter:

   * Repository name
   * Description (optional)
   * Public / Private
4. Click **Create Repository**

⚠️ **Do NOT initialize with README** if uploading existing files (recommended)

---

# 🔹 PART 3: Upload Files to GitHub (Local → Remote)

## ✅ Workflow Summary

```text
Create folder → git init → git add → git commit → git branch → git remote → git push
```

---

## Step-by-Step Commands

### 1️⃣ Create Project Folder

```bash
mkdir my-project
cd my-project
```

OR navigate to your existing project folder:

```bash
cd path/to/your/project
```

---

### 2️⃣ Initialize Git

```bash
git init
```

---

### 3️⃣ Check Status

```bash
git status
```

---

### 4️⃣ Add Files to Staging Area

Add all files:

```bash
git add .
```

Add specific file:

```bash
git add filename.txt
```

---

### 5️⃣ Commit Files

```bash
git commit -m "Initial commit"
```

---

### 6️⃣ Set Main Branch

```bash
git branch -M main
```

---

### 7️⃣ Connect Local Repo to GitHub

Copy repo URL from GitHub, then:

```bash
git remote add origin https://github.com/username/repository-name.git
```

Verify:

```bash
git remote -v
```

---

### 8️⃣ Push Files to GitHub 🚀

```bash
git push -u origin main
```

✔️ Files are now hosted on GitHub

---

# 🔹 PART 4: Add More Files Later (Very Common)

### 1️⃣ Add New Files / Modify Existing Ones

(just create or edit files)

---

### 2️⃣ Check Changes

```bash
git status
```

---

### 3️⃣ Stage Changes

```bash
git add .
```

---

### 4️⃣ Commit Changes

```bash
git commit -m "Added new files"
```

---

### 5️⃣ Push to GitHub

```bash
git push
```

---

# 🔹 PART 5: Daily Git Commands (Most Used)

| Command               | Purpose                 |
| --------------------- | ----------------------- |
| `git status`          | Check changes           |
| `git add .`           | Stage all files         |
| `git commit -m "msg"` | Save snapshot           |
| `git push`            | Upload to GitHub        |
| `git pull`            | Download latest changes |
| `git log`             | View commit history     |

---

# 🔹 PART 6: Branching Commands (Important)

### Create New Branch

```bash
git branch feature-1
```

Switch Branch

```bash
git checkout feature-1
```

OR (new way)

```bash
git switch feature-1
```

Create & Switch Together

```bash
git checkout -b feature-1
```

---

### Merge Branch into Main

```bash
git checkout main
git merge feature-1
```

---

# 🔹 PART 7: Undo & Fix Mistakes

### Unstage File

```bash
git reset filename
```

---

### Undo Last Commit (keep changes)

```bash
git reset --soft HEAD~1
```

---

### Discard Local Changes (Danger ⚠️)

```bash
git checkout -- filename
```

---

### Delete Branch

```bash
git branch -d branch-name
```

---

# 🔹 PART 8: Clone Existing GitHub Repo

```bash
git clone https://github.com/username/repo-name.git
```

---

# 🔹 PART 9: .gitignore (Very Important)

Create `.gitignore` file:

```txt
node_modules/
target/
.env
*.log
```

Add it:

```bash
git add .gitignore
git commit -m "Added gitignore"
git push
```

---

# 🔹 PART 10: GitHub Authentication (New Rule)

GitHub **does NOT allow password login**.

### Use **Personal Access Token (PAT)**:

1. GitHub → Settings → Developer Settings → Tokens
2. Generate token
3. Use token as **password** when pushing

OR

### Use SSH (Recommended)

```bash
ssh-keygen -t ed25519 -C "your_email@gmail.com"
```

Add key to GitHub → SSH keys

---

# 🔹 FINAL MENTAL MODEL (Remember This)

```text
Working Directory → Staging Area → Commit → GitHub
```

Commands:

```bash
git add → git commit → git push
```

---

If you want, next I can:
✅ Give **Git commands for interview**
✅ Create **1-page Git cheat sheet PDF**
✅ Explain **Git visually (diagrams)**
✅ Show **real-world workflow used in companies**

Just tell me 👌
