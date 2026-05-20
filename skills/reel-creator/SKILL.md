---
name: reel-creator
version: 1
agent: reel-creator
---

Invoke `reel-creator` as the very first step in every reel pipeline run, before any research or scripting begins. Pass it the user's raw idea or topic (and optionally a channel notes or memory file). The agent checks the done-topics ledger at `C:\Users\Pakorn\.context\reel\done-topics-ledger.md` to avoid exact duplicate topics, then commits to a genre (news, education, lifestyle, motivation, entertainment, comedy, or user-defined), a specific angle, a target emotion, a format, and an audience cue, returning a structured CONCEPT BRIEF. When the brief inherently requires a generated visual, the agent also emits an optional IMAGE REQUEST block that should be routed to `image-planner`. Do not use it to write hooks, scripts, captions, or conduct trend/news research — those belong to downstream agents.

## Notes

- If an exact duplicate topic is detected, the agent returns a DUPLICATE NOTICE instead of a CONCEPT BRIEF and waits for the user to choose an alternative before any downstream agent is invoked.
- The agent emits a CONTEXT WRITE REQUEST block at the end of every invocation; the main agent must persist it.
