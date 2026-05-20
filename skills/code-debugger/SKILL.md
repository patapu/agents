---
name: code-debugger
version: 1
agent: code-debugger
---

Invoke `code-debugger` when a bug or unexpected behavior needs root-cause analysis before a fix is written. Pass it a description of what is broken (error message, wrong output, crash, or silent failure). The agent locates relevant files, narrows the blast radius with Glob and Grep, reads the code path involved, and uses Bash to reproduce the failure when possible. It forms and confirms a root-cause hypothesis, then returns a structured DIAGNOSIS block with root cause, evidence, suggested fix direction, confidence level, and ruled-out hypotheses. It does not implement the fix — hand its DIAGNOSIS to `code-implementer`. Do not use it for test writing or code review.

## Notes

- The agent emits a CONTEXT WRITE REQUEST block at the end of every invocation; the main agent must persist it.
- Bash usage is read-only or minimally invasive; no installs or state-mutating commands unless strictly required and reversible.
