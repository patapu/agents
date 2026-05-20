---
name: reel-editor-handoff
version: 1
agent: reel-editor-handoff
---

Invoke `reel-editor-handoff` as an optional step after `reel-script-writer` has produced a finalized script and the user has finished filming and can provide raw clip context (clip file names, take numbers, timestamps, preferred takes). Pass it the finalized script and the clip notes. The agent maps each script beat (SETUP / ESCALATION / PAYOFF / CLOSER) to the corresponding clip segment, specifies subtitle timing and style (with the CLOSER catchphrase "และมันก็แค่นั้นเอง" styled bold, centered, and larger than all other subtitle text), lists audio cues (background track, volume, sound effects), and specifies transitions and export settings, returning a structured EDITOR HANDOFF document. When the editing brief calls for a generated visual (custom thumbnail, lower-third, end-card), it also emits an optional IMAGE REQUEST block to be routed to `image-planner`. The agent is also usable in pre-production planning mode when only a CONCEPT BRIEF exists and no finalized script or clip footage is available yet — in this mode it produces a planning-level brief with provisional beat descriptions rather than confirmed take IDs. The caller must explicitly state which mode applies (post-production or pre-production planning) when invoking the agent. Do not use it to rewrite the script or write captions.

## Notes

- The agent emits a CONTEXT WRITE REQUEST block at the end of every invocation; the main agent must persist it.
- For post-production mode, invoke only when filming is complete and a finalized script is available; for pre-production planning mode, a CONCEPT BRIEF alone is sufficient and filming need not be complete.
- When filmed footage exists and HyperFrames-assisted editing is intended, `reel-hyperframes-prep` must run before this agent; pass its outputs (`transcript.raw.json` path, `transcript.clean.md` path, word-alignment confirmation) as inputs to this agent.
