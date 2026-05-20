---
name: code-explorer
version: 1
agent: code-explorer
---

Invoke `code-explorer` during the research phase of any coding task — before implementation, planning, or review begins. Pass it a specific query such as a file name, symbol (function, class, type), usage pattern, or directory structure to locate. The agent uses Glob, Grep, and Read in the fewest passes necessary to find what is requested, then returns a structured FINDINGS block with absolute file paths, line ranges, and observed conventions. It is strictly read-only and will not edit anything; if broad exploration is needed ahead of implementation, run `code-explorer` first and hand its findings to `code-planner` or `code-implementer`.

## Notes

- Always provide a specific, targeted query; do not ask the agent to "explore the whole codebase."
- The agent emits a CONTEXT WRITE REQUEST block at the end of every invocation; the main agent must persist it.
