# Day 41 - DevOps Fundamentals

## Goal
Understand DevOps culture and practices before the tool-specific topics (Jenkins, Docker, Kubernetes, Terraform) that follow.

---

## 1. CI/CD Concepts

**CI (Continuous Integration)**: developers frequently merge code changes into a shared repository, with automated builds/tests run on every change - catches integration issues early.

**CD (Continuous Delivery/Deployment)**:
- **Continuous Delivery**: code is automatically prepared for release but requires manual approval to deploy to production
- **Continuous Deployment**: code automatically deploys to production with no manual gate, after passing all automated checks

```
Code commit -> Build -> Automated Tests -> (Delivery: manual approval) -> Deploy -> Monitor
```

## 2. Automation Philosophy

Core DevOps principle: anything done manually and repeatedly should be automated - reduces human error, increases speed, and creates consistency.

This applies across the whole roadmap you've covered so far: Ansible/Terraform (infrastructure), Jenkins (builds/tests), shell scripting (Topic 15), network automation (Topic 23).

## 3. Version Control Integration

CI/CD pipelines are triggered by version control events (push, pull request, tag) - Git (Topic 11) and GitHub (Topic 12) are the foundation everything else in this phase builds on.

```
git push -> triggers CI pipeline -> runs tests -> if pass, triggers CD -> deploys
```

## 4. Monitoring & Feedback Loops

DevOps isn't just "build and deploy" - it includes continuous monitoring of production systems and feeding that information back into development (ties to NOC/SOC monitoring concepts from earlier, and SIEM coming up at Topic 52).

The "DevOps Loop" concept: Plan -> Code -> Build -> Test -> Release -> Deploy -> Operate -> Monitor -> (back to Plan)

---

## Interview Questions

**Q1. Difference between Continuous Delivery and Continuous Deployment?**
Continuous Delivery requires manual approval before production deployment; Continuous Deployment deploys automatically with no manual gate, after automated checks pass.

**Q2. Why is automation central to DevOps philosophy?**
It reduces human error, increases deployment speed/frequency, and creates consistent, repeatable processes compared to manual operations.

**Q3. What typically triggers a CI/CD pipeline?**
Version control events - most commonly a `git push` or pull request creation/merge.

**Q4. Why does monitoring matter in a DevOps context, not just deployment?**
It closes the feedback loop - production issues discovered via monitoring inform future development priorities and reveal problems automated tests didn't catch.

## Key Takeaways
- Learned CI/CD concepts and the difference between Continuous Delivery and Deployment
- Understood the automation-first DevOps philosophy
- Learned how version control integrates with CI/CD triggers
- Learned the DevOps loop concept connecting development to operations/monitoring
