---
name: code-planner
version: 1
agent: code-planner
---

Invoke `code-planner` when a code change is non-trivial and requires deliberate sequencing, architectural reasoning, or explicit tradeoff analysis before any file is touched. Pass it the goal of the change along with the relevant files or context discovered by `code-explorer`. The agent reads only the files central to the change, identifies critical files, correct sequencing, integration points, and risks, and returns a structured PLAN that `code-implementer` can execute directly without further design decisions. It is strictly read-only and produces no code of its own; skip it for simple, self-evident edits.

## Notes

- The agent uses the `opus` model for hard reasoning — invoke it only when architectural tradeoffs are genuinely at stake.
- The agent emits a CONTEXT WRITE REQUEST block at the end of every invocation; the main agent must persist it.
