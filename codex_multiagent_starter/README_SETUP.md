# Codex multi-agent starter (no Git required)

1. Copy AGENTS.md, REQUIREMENTS.md, PLAN.md, STATUS.md, DECISIONS.md, docs/ and .codex/ into your project root.
2. Replace the placeholder content in REQUIREMENTS.md with official requirements and approved decisions.
3. Trust the project in Codex so the project-scoped `.codex/config.toml` and custom agents are loaded.
4. Start Codex from that project root. Use `/model` to choose an available main model and `/reasoning` to select xhigh if supported.
5. Run the prompt below in the main Codex session. Use `/subagents` to inspect agent threads, and steer any child through the parent.

## First-run prompt

Read AGENTS.md and REQUIREMENTS.md. Act as the Orchestrator. First review the requirements and draft a milestone plan in PLAN.md, separating confirmed rules from open policy decisions. After the plan is accepted, delegate to the project-scoped builder, reviewer, and recorder agents. Builder owns source/tests/STATUS.md, Reviewer must not edit files, Recorder only edits docs/HANDOFF.md and docs/WORKLOG.md. Use explicit REVIEW_READY milestones rather than reacting to every file change. Return P0/P1 defects to Builder for correction, and only then mark a milestone reviewed. Report the created agents, their current tasks, and the next approval point. Do not invent missing business requirements.

## Important limitations

- Subagents are controlled by their parent: their thread views do not allow the same direct prompt entry as fully independent Codex CLI sessions.
- Standalone role TOML files cannot enforce a different sandbox from the parent; Reviewer read-only is a behavioral instruction only.
- `AGENTS.md` and `.toml` are configuration/instructions, not an always-running scheduler. The parent needs to remain active and explicitly delegate/follow up; no automatic file watcher is included.
- If you require direct input to all worker sessions, use independent Codex sessions in separate terminal panes instead.
