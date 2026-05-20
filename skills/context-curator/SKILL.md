---
name: context-curator
version: 1
agent: context-curator
---

Invoke `context-curator` only via orchestrator — never self-schedule it. Orchestrator triggers it when either threshold is crossed: 50 or more uncurated run directories exist in `.context/runs/`, or 7 or more calendar days have elapsed since the last curation date in `.context/curator-log.md`. It also bootstraps the `.context/` directory tree (runs/, agents/, teams/, project/, templates/, archive/) on first run if the tree does not exist. Pass it no special inputs — it reads the runs directory, cross-references the curator-log, promotes recurring error patterns (seen in 3 or more distinct runs) to `project/pitfalls.md`, raises CRITICAL FLAGS for pitfalls that have recurred 3 or more times total (requiring a system prompt fix, not just another log entry), archives run directories older than 30 days, and appends a curation entry to `curator-log.md`.

## Notes

- The agent does not write agent files in `.claude/agents/` — that is `team-builder`'s job.
- When critical flags are raised, the CURATION REPORT ends with an ACTION REQUIRED notice naming which agents need system prompt updates.
