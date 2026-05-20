---
name: team-builder
version: 1
agent: team-builder
---

Invoke `team-builder` when orchestrator's plan calls for creating a new specialist agent or updating an existing one. Pass it the spec for the new or updated agent (name, when it should be triggered, tools needed, model, and any overlap concerns). The agent checks the existing roster and agent files, drafts the new or updated agent file (full contents) together with the exact diff to apply to `orchestrator.md`'s "Specialists you know about" section, and returns a DRAFT package — it does not write any file at this stage. The DRAFT is then reviewed by `approver`; only after the main agent confirms "approver PASS + user confirmed" does `team-builder` commit the files. Do not invoke it for regular project work — only for evolving the team roster itself.

## Notes

- If the spec is missing the agent name, trigger description, tools, or model, the agent returns CLARIFICATION NEEDED and stops — do not draft without a complete spec.
- After committing, the main agent must instruct the user to restart Claude Code before using the new or updated agent.
