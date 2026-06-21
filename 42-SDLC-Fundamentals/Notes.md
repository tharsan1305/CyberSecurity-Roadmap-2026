# Day 42 - SDLC Fundamentals

## Goal
Understand the Software Development Life Cycle - the broader process DevOps/CI/CD operates within, and where security fits (setting up DevSecOps, Topic 51).

---

## 1. SDLC Phases

```
1. Planning       - define requirements, scope, feasibility
2. Design          - architecture, system design, data models
3. Development       - actual coding/implementation
4. Testing            - unit, integration, security testing
5. Deployment           - releasing to production
6. Maintenance            - bug fixes, updates, ongoing support
```

Security relevance: the later security is addressed in this cycle, the more expensive and disruptive it is to fix - this is the core argument behind "Shift-Left Security" (Topic 51).

## 2. Agile vs Waterfall

**Waterfall**: linear, sequential - each phase completes fully before the next begins. Predictable but inflexible to changing requirements.

**Agile**: iterative, incremental - work happens in short cycles (sprints), with continuous feedback and adaptation.

```
Waterfall: Plan -> Design -> Build -> Test -> Deploy (once, in sequence)
Agile: [Plan -> Build -> Test -> Review] repeated every sprint (2-4 weeks typically)
```

Most modern software teams use Agile (or a hybrid), since it accommodates changing requirements and delivers value incrementally rather than waiting for one large release.

## 3. Sprint Planning Basics

A **Sprint** is a fixed time period (commonly 2 weeks) in which a defined set of work is completed.

Sprint cycle:
```
Sprint Planning -> Daily Standups -> Sprint Review -> Sprint Retrospective -> (next Sprint)
```

- **Sprint Planning**: team selects work items (user stories/tasks) for the sprint from the backlog
- **Daily Standup**: brief daily sync - what was done, what's planned, any blockers
- **Sprint Review**: demo completed work to stakeholders
- **Sprint Retrospective**: team reflects on what went well/poorly, adjusts process

This connects to GitHub Projects/Issues from Topic 12 - many teams literally run sprints using GitHub Projects boards.

---

## Interview Questions

**Q1. Name the 6 phases of SDLC.**
Planning, Design, Development, Testing, Deployment, Maintenance.

**Q2. Difference between Agile and Waterfall?**
Waterfall is linear/sequential with each phase completing before the next; Agile is iterative, working in short sprints with continuous feedback and adaptation.

**Q3. Why does fixing security issues late in the SDLC cost more?**
Issues found in production require more rework (code changes, re-testing, re-deployment, potential incident response) compared to catching them during design or development - this principle drives "Shift-Left Security."

**Q4. What happens during a Sprint Retrospective?**
The team reflects on what went well and what didn't during the sprint, and adjusts their process for future sprints.

## Key Takeaways
- Learned the 6 phases of SDLC
- Learned Agile vs Waterfall methodologies and their trade-offs
- Learned Sprint structure: Planning, Standups, Review, Retrospective
- Connected SDLC phases to where security fits in, setting up DevSecOps (Topic 51)
