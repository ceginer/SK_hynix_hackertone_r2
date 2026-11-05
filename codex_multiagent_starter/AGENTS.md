# Project instructions — Codex Orchestrator

## Goal
Deliver a correct, runnable, documented implementation of REQUIREMENTS.md. Coordinate a Builder, Reviewer and Recorder in parallel whenever useful; **this file is an instruction document, not a background scheduler**.

## Roles and ownership
- **Parent (Orchestrator)**: resolve ambiguities with the user/stakeholder, own PLAN.md and DECISIONS.md, delegate work, collect findings, approve milestones, integrate results.
- **builder**: own application source, tests and STATUS.md. Implement one approved milestone, test it, mark REVIEW_READY and report its ID to parent.
- **reviewer**: read-only behavior; inspect stable milestones assigned by parent; report P0/P1/P2 findings. Never edit any files.
- **recorder**: own only docs/HANDOFF.md and docs/WORKLOG.md. Record verified progress and decisions.

## Work protocol (no Git required)
1. Parent reads REQUIREMENTS.md and records open questions. Do not invent stakeholder constraints.
2. Parent drafts PLAN.md as small, independently reviewable milestones; ask user for approval where a business decision is needed.
3. Parent spawns builder for the first approved milestone and asks reviewer to independently assess the PLAN/requirements while builder works. Recorder may create an initial handoff skeleton.
4. Builder reports `REVIEW_READY: Mxx` with files changed, test commands and results. Stable files must remain untouched while under review.
5. Parent assigns that milestone to reviewer. A milestone is not accepted merely because it was implemented.
6. If reviewer reports P0/P1 issues, parent sends the concrete findings to builder and requests a new verification pass. Parent assigns follow-up review as needed.
7. Parent asks recorder to update verified records after a stable decision or completed milestone. Parent may let builder work on another independent milestone while reviewer checks the previous one.
8. Parent provides concise progress updates and takes steering instructions from user. If the user changes the goal, reassess PLAN and message the affected existing agents.

## Rules for shared files
- Do not concurrently edit the same file.
- Do not read half-written code as though it were final. Use explicit `REVIEW_READY` milestones, not every file save, as triggers.
- Record business decisions in DECISIONS.md; Git history is not required.
- Distinguish verified test results, reported claims and open questions.
- Do not perform destructive actions, deploy, push, or install unapproved external tools.

## Final deliverables
Runnable code, test evidence, README/setup instructions, docs/HANDOFF.md, and an explicit limitations section.
