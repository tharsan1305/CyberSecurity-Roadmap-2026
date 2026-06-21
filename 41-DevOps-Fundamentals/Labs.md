# Day 41 - Lab: DevOps Loop Mapping (Conceptual Exercise)

## Objective
Since DevOps fundamentals are largely conceptual (tool-specific labs come in Topics 43-51), today's lab maps your own roadmap repo workflow onto formal DevOps concepts.

## Task 1: Map Your Existing Workflow to CI/CD Concepts
Looking at your daily roadmap routine (study -> notes -> git add/commit/push), identify:
- What's your "Integration" step? (commit/push)
- What would "automated testing" look like for a notes repo? (e.g., a script checking all required files exist)
- What would "Continuous Deployment" mean for this repo? (e.g., auto-publishing notes to a website)

## Task 2: Write a Simple CI Validation Script (Practical Mini-Project)
Write a bash script that checks your roadmap repo for completeness - a simple form of "automated testing" for documentation:
```bash
#!/bin/bash
# check_repo_completeness.sh
MISSING=0
for dir in */; do
    if [[ "$dir" =~ ^[0-9]+- ]]; then
        for file in Notes.md Labs.md Resources.md; do
            if [ ! -f "$dir$file" ]; then
                echo "MISSING: $dir$file"
                MISSING=1
            fi
        done
    fi
done

if [ $MISSING -eq 0 ]; then
    echo "All topic folders complete!"
else
    echo "Some files are missing - see above."
fi
```
Run this against your actual roadmap repo.

## Task 3: Design a GitHub Actions Workflow for This Check
Using what you learned in Topic 12, design (don't need to fully implement yet) a GitHub Action that runs this completeness check automatically on every push.

## Results
| Item | Value |
|---|---|
| CI/CD mapping exercise completed (Y/N) | |
| Completeness script written (Y/N) | |
| Missing files found in your repo | |
| GitHub Action design sketched (Y/N) | |

## Lab Summary
Note how many topic folders (if any) were missing files when you ran the completeness check - this is a practical, real use of "automated testing" applied to your own learning repo.
