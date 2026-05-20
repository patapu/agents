---
name: skill-reviewer
version: 1
agent: skill-reviewer
---

Invoke `skill-reviewer` after `skill-updater` returns a CHANGES SUMMARY. Pass it the full CHANGES SUMMARY. The agent reads each modified or created SKILL.md from disk, verifies that stale references are fully resolved (no retired agent name remains), new stubs are well-formed (frontmatter contains at minimum `name`, `version`, and `agent` keys; body has at least a description paragraph and a `## Notes` section), no unintended content was altered, and every agent name in every skill file matches the current roster (re-reads `orchestrator.md` to confirm). It returns either REVIEW: PASS (all checks clear) or REVIEW: REVISE (with specific required fixes). It is strictly read-only and never edits any file.

## Notes

- The pipeline order is: skill-auditor → skill-updater → skill-reviewer.
- On REVISE, return the findings to `skill-updater` for a second pass.
