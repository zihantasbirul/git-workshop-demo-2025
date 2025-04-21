# Git Introduction Workshop

## Reach here

![QR failed loading!](/qrcode.png)

## Other Links

### [2-Page Git Cheat-Sheet (PDF)](https://raw.githubusercontent.com/radmanesh/git-workshop-demo-2025/refs/heads/main/CheatSheet.pdf)

[Git Introduction Workshop (Word)](https://sooners-my.sharepoint.com/:w:/r/personal/radmanesh_ou_edu/Documents/Git%20Introduction%20Workshop.docx?d=wdc22cdcb84e748809bd5b0f1e101d0c8&csf=1&web=1&e=pX0kRV)

---

## Welcome & Objectives

### What is Git and Why Use It?
- **Distributed version control** (tracks changes, supports collaboration, maintains history)
- Created in 2005 by Linus Torvalds, the creator of Linux
- Compared to SVN and Mercurial:
  - **Distributed architecture**
  - More flexible workflow
- Relevance for graduate students:
  - Efficient tracking of research and development
  - Enables collaboration
  - Operates offline
  - Industry-standard tool

---

## Git Basic Definitions

| Concept | Description |
|---------|-------------|
| **Repository (repo)** | Project tracked by Git, can be local or remote (e.g., GitHub, GitLab). |
| **Commit** | Snapshot of project state at a certain point, with descriptive message. |
| **Branch** | Separate development line; used for features without disturbing main project. |
| **Merge** | Combines changes from different branches. |
| **Clone** | Copies a remote repository to your local machine. |
| **Push/Pull** | Send commits to remote repository / Retrieve updates from remote repository. |
| **Fork** | Personal copy of another user's repository on GitHub/GitLab. |

---

## First-Time Setup

### Installation & Setup
- [Create GitHub account](https://github.com/)
- Install Git ([Windows/Mac/Linux](https://git-scm.com/downloads))
- Configure Git globally:
```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```
- Create and clone repository from GitHub:
```bash
git clone <repo-link>
```

### Starting a Repository
- Initialize local repository:
```bash
git init
```
- File states: **Untracked**, **Staged**, **Committed**

---

## Basic Workflow

### Adding Changes
```bash
git add <file>
git add .
```

### Making a Commit
```bash
git commit -m "commit message"
git status
git log --oneline
```

### Using Git Diff
- View unstaged changes:
```bash
git diff
```
- Diff between commits:
```bash
git diff <commit1> <commit2>
```
- Diff staged changes:
```bash
git diff --staged
```

### Inspecting the Repository
- Check repository status:
```bash
git status
```
- Inspect commit details:
```bash
git show <commit>
```

---

## Branching & Merging

### Why Branching Matters
- Enables isolated feature development
- Keeps main branch stable

### Creating & Switching Branches
- Create and switch branches:
```bash
git branch <branch-name>
git switch <branch-name>
```
- Shortcut to create and switch:
```bash
git switch -c <branch-name>
```

### Merging Changes
- Merge feature branch into main:
```bash
git switch main
git merge <branch-name>
```
- Merge methods:
  - Fast-forward (simple merges)
  - 3-way merge (complex merges)
- Resolve merge conflicts manually:
  - Identify conflicts (`git status`, `git diff`)
  - Edit conflicted files, remove markers, commit resolved changes

### Branching Best Practices
- Short-lived branches for features
- Clear, descriptive branch names
- Use graphical tools (`git log --graph --oneline --all`) for visualization

---

## Working with Remotes

### What Are Remotes?
- Repositories on remote servers (GitHub)
- Supports collaboration via pull requests and issue tracking

### Setting Up SSH Keys
- Create SSH keys:
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
cat ~/.ssh/id_ed25519.pub
```
- Add SSH key to GitHub under account settings

### Adding a Remote
```bash
git remote add origin <URL>
git remote -v
```

### Syncing Changes
- Push commits:
```bash
git push origin <branch-name>
```
- Fetch and merge remote changes:
```bash
git pull origin <branch-name>
```
- Fetch without merging:
```bash
git fetch
```

### Forking vs. Cloning
- **Fork**: Personal GitHub copy (common in open-source)
- **Pull requests**: Propose merging your forked changes into original repository

---

## Common Pitfalls & How to Fix Them

### Merge Conflicts Exercise
- Clone demo repository:
```bash
git clone https://github.com/radmanesh/git-workshop-demo-2025
```
- Create branches:
```bash
git switch -c groupA-branch  # Group A
git switch -c groupB-branch  # Group B
```
- Modify `team.txt`:
  - Group A: Replace "Bob" with "Charlie"
  - Group B: Replace "Bob" with "Dana"

- Commit changes:
```bash
git add team.txt
git commit -m "Changed Bob to Charlie"   # Group A
git commit -m "Changed Bob to Dana"      # Group B
```
- Push changes:
```bash
git push origin groupA-branch
git push origin groupB-branch
```
- Merge on GitHub: Merge Group A’s PR to main
- Group B pulls main and faces conflicts:
```bash
git switch main
git pull origin main
git switch groupB-branch
git merge main  # Resolve conflicts manually
```

### Detached HEAD State
- Occurs checking out specific commit directly
- Recover by switching to a branch:
```bash
git switch main  # or
git switch -c new-branch
```

### Reverting vs. Resetting
- Safely undo a commit:
```bash
git revert <commit>
```
- Rewrite history (with caution):
```bash
git reset --hard <commit>
```

### `.gitignore` Issues
- Ignore files properly:
  - `.gitignore` file
  - Remove already-committed files:
```bash
git rm --cached <file>
```

---

## Copilot Online Queries (Optional)
- View repository history clearly:
```bash
git log --oneline --graph --decorate --all
```
- Document pull requests clearly with messages and comments for detailed collaboration.
