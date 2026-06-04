# 🧠 Git & GitHub: Visual Memory Cheat Sheet

> **🎨 Visual Learning Legend:**
> <span style="color: #28a745;">🟢 **Green / Safe / Create**</span> (Building new things)
> <span style="color: #ffc107;">🟡 **Yellow / Stage / Observe**</span> (Checking status, preparing)
> <span style="color: #007bff;">🔵 **Blue / Sync / Remote**</span> (Talking to GitHub)
> <span style="color: #dc3545;">🔴 **Red / Danger / Undo**</span> (Changing history, fixing mistakes)
> *Note: Replace `<text-in-brackets>` with your actual names.*

---

## 🟡 1. The "Where Am I?" Commands (Observation)
*Always use these to avoid flying blind.*

* 👁️ **`git status`**
  * **What it does:** Shows modified files, staged files, and your current branch.
* 📖 **`git log`**
  * **What it does:** Shows the timeline of your past commits. (Press `q` to exit).

---

## <span style="color: #28a745;">🟢 2. The Daily Flow (Local Work)</span>
*The repetitive loop you will do every single day.*

* 📦 **`git add <file-name>`** (or **`git add .`** for all)
  * **What it does:** Puts your changed files into the "staging area" (the shipping box).
* 🏷️ **`git commit -m "Describe your changes here"`**
  * **What it does:** Seals the box and permanently saves a snapshot to your local history.

---

## <span style="color: #007bff;">🔵 3. Remote Collaboration (GitHub Sync)</span>
*How your computer talks to the cloud.*

* 📥 **`git pull origin <branch-name>`**
  * **What it does:** Downloads and integrates new changes from GitHub into your computer. *(Always do this before you start working!)*
* 📤 **`git push origin <branch-name>`**
  * **What it does:** Uploads your local commits to GitHub.
* 👯 **`git clone <ssh-or-https-url>`**
  * **What it does:** Downloads an entire existing repository from GitHub to your machine for the first time.

---

## <span style="color: #28a745;">🟢 4. Branching (Safe Sandboxes)</span>
*Never work directly on the main code. Always build a sandbox.*

* 🌿 **`git branch <new-branch-name>`**
  * **What it does:** Creates a new parallel universe for your code.
* 🔀 **`git switch <branch-name>`**
  * **What it does:** Teleports you into that specific branch.
  * *Speed Code:* `git switch -c <new-branch>` (Creates AND teleports in one move).
* 🤝 **`git merge <branch-name>`**
  * **What it does:** Combines the finished sandbox code back into your main branch.

---

## <span style="color: #dc3545;">🔴 5. Time Travel & Fixes (The "Oops" Handlers)</span>
*Tools for when things go wrong.*

* ⏪ **`git revert <commit-hash>`**
  * **What it does:** Safely un-does a mistake by creating a *new* commit that does the exact opposite. (Safe for teams).
* 🗑️ **`git restore <file-name>`**
  * **What it does:** Throws away uncommitted changes in a specific file, returning it to how it looked at your last commit.
* 🙈 **`git stash`**
  * **What it does:** Temporarily hides your messy, unfinished work so you can switch branches cleanly.
  * *To get it back:* Use **`git stash pop`**.

---

### 💡 Pro-Tip for AI & Future Tech:
Always create a **`.gitignore`** file before your first commit. Never let API keys, `.env` files, or massive AI datasets (`.pt`, `.csv`) accidentally upload to GitHub!
