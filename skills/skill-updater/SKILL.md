---
name: skill-updater
version: 1
agent: skill-updater
---

Invoke `skill-updater` after `skill-auditor` returns an AUDIT REPORT. Pass it the full AUDIT REPORT. The agent works through issues in this order: stale references (removes or replaces retired agent names in SKILL.md files), convention drift (edits only the deviating frontmatter key, heading, or terminology without rewriting surrounding content), missing coverage (creates new SKILL.md stubs under `.claude/skills/{agent-name}/SKILL.md` with frontmatter containing `name`, `version: 1`, and `agent` fields; a description paragraph; and a `## Notes` section), and orphaned directories (adds a SKILL.md stub with `status: orphaned` frontmatter). It reads each corresponding agent file in `.claude/agents/` to write accurate descriptions. It never audits, never approves its own changes, and never modifies `.claude/agents/` or `orchestrator.md`.

## Notes

- After all edits the agent returns a CHANGES SUMMARY (Files edited, Files created, Edits Applied, Files Created, Skipped).
- Pass the CHANGES SUMMARY to `skill-reviewer` as the next pipeline step.
