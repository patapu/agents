---
name: code-implementer
version: 1
agent: code-implementer
---

Invoke `code-implementer` when a clear spec or plan is in hand and actual code needs to be written or modified. Pass it the implementation spec or the PLAN from `code-planner`, together with any relevant findings from `code-explorer`. The agent reads neighboring code first to match existing naming conventions and style, makes the smallest set of changes that satisfies the spec using Edit (existing files) or Write (new files only when required), and returns a list of changed files plus a short summary. Do not use it for writing tests, making design decisions, or running builds — those belong to `code-tester`, `code-planner`, and `code-reviewer` respectively.

## Notes

- If the spec is ambiguous about architecture, the agent will stop and report the ambiguity rather than guess.
- The agent writes a context log to `.context/runs/{task_id}/agent-code-implementer.md` at the end of every invocation.
