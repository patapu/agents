---
name: orchestrator
version: 1
agent: orchestrator
---

Invoke `orchestrator` as the mandatory first step for every user prompt — no exceptions, including trivial single-line edits, simple questions, and conversational replies that touch the project. Pass it the user's full request verbatim. The agent reads only the "Specialists you know about" roster (not project source code) to determine which agent(s) handle each piece of work, then returns a structured PLAN naming the responsible agent per step. Simple tasks receive a 1-step plan; multi-step tasks list agents in workflow order. When a needed specialist is absent from the roster it returns a 1-step plan invoking `team-builder`. It never does the work itself — it only plans. After receiving the PLAN the main agent dispatches to the named agents in sequence.

## Notes

- Every user prompt must be routed through orchestrator before any other tool is called. Bypassing it — even once — breaks the audit trail.
- On continuation tasks (prior task_id provided), orchestrator reads `.context/project/pitfalls.md`, team lessons, the prior handoff, and agent known-mistakes before producing the plan.
