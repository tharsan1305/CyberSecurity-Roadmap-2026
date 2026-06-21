# Day 11 - Git

## Goal
Master version control fundamentals - you're already using Git daily for this roadmap, today formalizes the underlying concepts and adds branching/merging skills.

---

## 1. Basic Commands

```bash
git init                      # initialize a new repo
git add file.txt                # stage a file
git add .                        # stage all changes
git commit -m "message"           # commit staged changes
git push origin main                # push to remote
git pull origin main                 # pull latest from remote
git status                            # check current state
git log                                # view commit history
git log --oneline --graph             # compact visual history
```

## 2. Branching & Merging

A **branch** is an independent line of development, allowing work on features/fixes without affecting the main codebase.

```bash
git branch                       # list branches
git branch feature-x               # create new branch
git checkout feature-x              # switch to branch
git checkout -b feature-y             # create and switch in one step
git switch feature-x                   # modern alternative to checkout

git merge feature-x                # merge feature-x into current branch
```

Merge types:
- **Fast-forward merge**: when no divergent changes exist, Git simply moves the pointer forward
- **Three-way merge**: when both branches have diverged, Git creates a new merge commit combining both histories

## 3. Conflict Resolution

A conflict occurs when Git can't automatically merge changes (e.g., the same line was edited differently in two branches).

```
<<<<<<< HEAD
Your current branch's version
=======
Incoming branch's version
>>>>>>> feature-x
```

Resolution steps:
1. Open the conflicted file, manually choose/combine the correct content
2. Remove the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
3. `git add <file>` to mark as resolved
4. `git commit` to complete the merge

## 4. Git Workflow Strategies

- **Feature Branch Workflow**: each feature/fix gets its own branch, merged into main when complete
- **Gitflow**: more structured, with `main`, `develop`, `feature/*`, `release/*`, `hotfix/*` branches - common in larger teams
- **Trunk-Based Development**: developers commit small, frequent changes directly to `main` (or very short-lived branches), common with strong CI/CD

For this roadmap's solo learning repo, a simple direct-to-main workflow (what you're already doing) is appropriate - branching becomes more valuable in team/collaborative projects.

---

## Interview Questions

**Q1. Difference between `git merge` and `git rebase`?**
Merge combines histories with a new merge commit, preserving the actual history; rebase rewrites commit history by replaying commits on top of another branch, producing a linear history (more advanced, not covered in depth today).

**Q2. What causes a merge conflict?**
When the same part of a file has been changed differently in two branches being merged, and Git cannot automatically determine which version to keep.

**Q3. What's the difference between `git pull` and `git fetch`?**
`git fetch` downloads changes from remote without merging them; `git pull` does a fetch AND merges the changes into your current branch.

**Q4. What is a fast-forward merge?**
A merge where the target branch has no new commits since the source branch diverged, so Git simply moves the branch pointer forward without creating a new merge commit.

## Key Takeaways
- Reinforced core Git commands already used daily in this roadmap
- Learned branching and merging concepts and commands
- Learned how to identify and resolve merge conflicts
- Learned common Git workflow strategies and when each applies
