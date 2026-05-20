---
name: skill-auditor
version: 1
agent: skill-auditor
---

Invoke `skill-auditor` at the start of the skill-update pipeline. Pass it no special inputs — it reads `.claude/skills/**` to enumerate every SKILL.md, reads `.claude/agents/orchestrator.md` to obtain the current agent roster, and then checks each SKILL.md for stale agent references (skill references an agent no longer in the roster), missing coverage (roster agents with no skill), convention drift (frontmatter, heading structure, or terminology deviations), and orphaned skill directories (directory exists but no SKILL.md). It returns a structured AUDIT REPORT with findings grouped by category. It is strictly read-only and never proposes fixes — that is `skill-updater`'s job.

## Notes

- The pipeline order is: skill-auditor → skill-updater → skill-reviewer.
- Pass the full AUDIT REPORT verbatim to `skill-updater` as its input.
