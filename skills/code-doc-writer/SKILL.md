---
name: code-doc-writer
version: 1
agent: code-doc-writer
---

Invoke `code-doc-writer` to write or update documentation for code — README files, API/usage docs, and inline comments that capture non-obvious WHY reasoning. Pass it the source files to document or the doc files to update. The agent always reads the relevant source files first (never assumes prior context), locates existing docs with Glob before creating new ones, updates in place when a file already exists, and writes docs that accurately reflect what the code actually does. It is read-only on source files and write-only on doc files; it will not fix bugs, suggest refactors, or write test files unless the task explicitly requests a test plan document.

## Notes

- If the code contradicts an existing doc, the agent updates the doc to match the code.
- The agent writes a context log to `.context/runs/{task_id}/agent-code-doc-writer.md` at the end of every invocation.
