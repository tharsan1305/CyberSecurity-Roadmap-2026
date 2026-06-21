# Day 12 - GitHub

## Goal
Go beyond basic push/pull (already practiced daily) into collaboration features - forking, pull requests, issues, and CI/CD via GitHub Actions.

---

## 1. Repositories & Forking

A **Fork** creates your own copy of someone else's repository under your account, allowing you to make changes independently without affecting the original.

Typical open-source contribution flow:
```
1. Fork the original repo to your account
2. Clone YOUR fork locally
3. Make changes, commit, push to your fork
4. Open a Pull Request from your fork back to the original repo
```

```bash
git clone https://github.com/<your-username>/<forked-repo>.git
git remote add upstream https://github.com/<original-owner>/<repo>.git
git fetch upstream
git merge upstream/main      # keep your fork updated with the original
```

## 2. Pull Requests & Code Review

A **Pull Request (PR)** proposes merging changes from one branch (or fork) into another, with a review process before merging.

PR workflow:
1. Push your branch to GitHub
2. Open a PR via the GitHub UI, comparing your branch against the target (e.g., main)
3. Reviewers comment, request changes, or approve
4. Once approved, the PR is merged (often via "Squash and Merge" or "Merge Commit")

Good PR practices: clear title/description, small focused changes, linking related issues.

## 3. Issues & Project Boards

**Issues** track bugs, feature requests, or tasks within a repo - each can be assigned, labeled, and linked to PRs.

**Project Boards** (GitHub Projects) provide Kanban-style tracking (To Do / In Progress / Done) for issues and PRs - useful for managing your own roadmap progress too.

## 4. GitHub Actions (CI/CD)

Automate workflows (testing, building, deploying) triggered by repo events (push, PR, schedule).

Example workflow file (`.github/workflows/test.yml`):
```yaml
name: Run Tests
on: [push]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Run a script
        run: echo "Tests would run here"
```

This is directly relevant to the DevSecOps phase later in the roadmap (security scanning in CI/CD pipelines).

## 5. Collaboration Workflow

Typical team workflow combining all the above:
```
Issue created -> Branch created -> Work committed -> PR opened -> 
Code reviewed -> CI checks pass (GitHub Actions) -> PR merged -> Issue closed
```

---

## Interview Questions

**Q1. What is a Pull Request?**
A request to merge changes from one branch/fork into another, including a review process before the merge happens.

**Q2. Difference between a Fork and a Branch?**
A Fork is a separate copy of the entire repository under a different account; a Branch is a parallel line of development within the same repository.

**Q3. What are GitHub Actions used for?**
Automating workflows like testing, building, and deploying code, triggered by repository events such as pushes or pull requests.

**Q4. What's the typical open-source contribution workflow?**
Fork the repo, clone your fork, make changes on a branch, push to your fork, then open a PR back to the original repository.

## Key Takeaways
- Learned forking and the open-source contribution workflow
- Learned Pull Request creation and code review process
- Learned Issues and Project Boards for task tracking
- Learned GitHub Actions basics for CI/CD automation
- Understood the full collaboration workflow combining these features
