---
name: code-reviewer
version: 1
agent: code-reviewer
---

Invoke `code-reviewer` to review a code diff or set of changed files for correctness, style, security issues, and regressions before the changes land. Pass it the changed file paths. The agent reads every changed file in full, evaluates each change through four lenses (correctness, security, style/conventions, regressions), gathers cross-file context when a finding requires it, and returns a REVIEW block with findings grouped by severity: critical, major, minor, and nit. It is strictly read-only and will not propose full rewrites — it points at exact problems and locations for `code-implementer` to resolve. Use it in parallel with `code-tester` after implementation.

## Notes

- The agent emits a CONTEXT WRITE REQUEST block at the end of every invocation; the main agent must persist it.
- Omit severity sections that have no findings; if there are none at all the agent returns "REVIEW: no issues found."
