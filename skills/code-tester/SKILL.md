---
name: code-tester
version: 1
agent: code-tester
---

Invoke `code-tester` after `code-implementer` has made changes and before any change is considered complete. Pass it the changed or new source files. The agent locates the existing test framework (pytest, jest, vitest, go test, etc.), writes tests covering the happy path, edge cases, and error paths, runs the full relevant test suite via Bash, and returns a structured TESTS block with pass/fail status. It may make minimal production-code edits for testability (e.g. dependency injection hooks) but will not add features. After up to 3 fix iterations it reports persistent failures as-is. Do not use it for feature implementation, code review, or root-cause analysis of pre-existing bugs.

## Notes

- Must be used before any code change is considered complete.
- The agent writes a context log to `.context/runs/{task_id}/agent-code-tester.md` at the end of every invocation; on failure it also appends a summary to `.context/agents/code-tester/known-mistakes.md`.
