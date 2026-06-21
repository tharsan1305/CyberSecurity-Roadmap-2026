# Day 11 - Lab: Git Branching & Merge Conflicts

## Objective
Practice branching, merging, and intentionally creating and resolving a merge conflict.

## Task 1: Create and Switch Branches
In a test repo (can be a throwaway folder, not your main roadmap repo):
```bash
mkdir git-lab && cd git-lab
git init
echo "Line 1" > file.txt
git add . && git commit -m "Initial commit"

git checkout -b feature-branch
echo "Line 2 from feature branch" >> file.txt
git add . && git commit -m "Added line 2 on feature branch"
```

## Task 2: Fast-Forward Merge
```bash
git checkout main
git merge feature-branch
git log --oneline --graph
```
Record: did it fast-forward, or create a merge commit?

## Task 3: Create a Merge Conflict (Intentional)
```bash
git checkout -b conflict-branch
echo "Conflict branch version" > file.txt
git add . && git commit -m "Changed file.txt on conflict-branch"

git checkout main
echo "Main branch version" > file.txt
git add . && git commit -m "Changed file.txt on main"

git merge conflict-branch
```
This should produce a conflict. Open `file.txt`, observe the conflict markers.

## Task 4: Resolve the Conflict
Manually edit `file.txt` to resolve, removing conflict markers, then:
```bash
git add file.txt
git commit -m "Resolved merge conflict"
git log --oneline --graph --all
```

## Results
| Item | Value |
|---|---|
| Fast-forward merge occurred (Y/N) | |
| Conflict successfully created (Y/N) | |
| Conflict resolved manually (Y/N) | |
| Final commit history branches visible | |

## Screenshots
```
![Branch Created](Screenshots/branch-created.png)
![Conflict Markers](Screenshots/conflict-markers.png)
![Resolved History](Screenshots/resolved-history.png)
```

## Lab Summary
Note how the conflict markers looked and whether resolving it was intuitive or confusing the first time.
