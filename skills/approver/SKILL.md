---
name: approver
version: 1
agent: approver
---

Invoke `approver` after `team-builder` returns a DRAFT package and before any file is written. Pass it the full DRAFT package (the proposed agent file contents, the `orchestrator.md` diff, and `team-builder`'s rationale). The agent evaluates the draft against criteria covering description quality (specific enough for orchestrator routing, no overlap with existing agents), scope and overlap (cleanly distinct responsibility, extension over fragmentation), tools (minimum viable set, read-only agents must not have Edit/Write/Bash), model choice (haiku/sonnet/opus/inherit appropriateness), orchestrator.md diff correctness, style consistency, and prompt content quality. It returns APPROVAL: PASS, APPROVAL: REVISE (with specific required changes), or APPROVAL: ESCALATE (after 2 revisions without convergence). It is strictly read-only and never edits the draft.

## Notes

- `approver` is not named in orchestrator plan steps — the main agent calls it between `team-builder`'s draft and commit as a mandatory gate.
- After 2 revision rounds without convergence, the agent escalates to the user for arbitration.
