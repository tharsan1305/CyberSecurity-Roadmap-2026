# Day 12 - Lab: GitHub Collaboration Features

## Objective
Practice forking, pull requests, issues, and a basic GitHub Actions workflow.

## Task 1: Fork a Public Repo
1. Find any small public repo on GitHub (e.g., a simple "awesome-list" repo)
2. Click "Fork" to create your own copy
3. Clone it locally:
```bash
git clone https://github.com/<your-username>/<repo>.git
```

## Task 2: Make a Change and Open a PR
```bash
cd <repo>
git checkout -b my-first-contribution
echo "- Added by [your-name]" >> README.md
git add . && git commit -m "Test contribution"
git push origin my-first-contribution
```
Go to GitHub, open a Pull Request from your branch. (You don't need to wait for it to be merged - the goal is practicing the PR creation flow. You can also close it without merging if it's just a practice fork.)

## Task 3: Create Issues on Your Own Roadmap Repo
On your `CyberSecurity-Roadmap-2026` repo:
1. Create an Issue: "Complete Active Directory Pentesting labs"
2. Add a label (e.g., "in-progress")
3. Create a Project Board (Kanban) with columns: To Do / In Progress / Done
4. Add the issue to the board

## Task 4: Add a Basic GitHub Action
In your roadmap repo, create `.github/workflows/check.yml`:
```yaml
name: Repo Check
on: [push]
jobs:
  check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Confirm push
        run: echo "Push detected, workflow running successfully"
```
Push this file and check the "Actions" tab on GitHub to see it run.

## Results
| Item | Value |
|---|---|
| Fork created (Y/N) | |
| PR opened (Y/N) | |
| Issue created on own repo (Y/N) | |
| Project board created (Y/N) | |
| GitHub Action ran successfully (Y/N) | |

## Screenshots
```
![Pull Request](Screenshots/pull-request.png)
![Issue Created](Screenshots/issue-created.png)
![GitHub Action Run](Screenshots/github-action.png)
```

## Lab Summary
Note how the PR review interface felt, and what you'd want to automate next with GitHub Actions.
