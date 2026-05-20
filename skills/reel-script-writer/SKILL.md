---
name: reel-script-writer
version: 1
agent: reel-script-writer
---

Invoke `reel-script-writer` after `reel-hook-writer` has selected a hook. Pass it the CONCEPT BRIEF, the trend or news briefing, and the chosen hook. The agent writes a full timed, scene-by-scene reel script (15–60 seconds, default 30 s) structured in four beats: SETUP (0–5 s using the chosen hook), ESCALATION (building tension appropriate to the declared genre), PAYOFF (peak moment — punchline, reveal, insight, or climax), and CLOSER (final 2–3 s delivering the channel catchphrase "และมันก็แค่นั้นเอง" spoken and on-screen). The word budget targets 25–30 Thai words per 10 seconds. When a `research/<date>/<slug>-verified.md` file (produced by `reel-trend-verifier`) is passed, the agent asserts `schema_version == 1` before writing any script content; a `REJECT` recommendation causes the agent to return `SCRIPT REFUSED` with no script written, while `PROCEED-WITH-CAUTION` or `PROCEED` results in a script written with per-claim voiceover rules applied — claims labelled `MEDIUM` must be hedged with `รายงานว่า...` or `มีรายงานว่า...`, and claims labelled `LOW` or `UNVERIFIED` must not have their specific detail (number, name, date) stated as fact (reference the broader story with explicit hedging only). If no `-verified.md` is provided, the agent proceeds as normal with no behavioural change. Do not use it to write captions or hashtags, invent trending audio not in the briefing, or add any CTA after the catchphrase.

## Notes

- The script's total duration, word count, and production notes must be passed to `reel-editor-handoff` or `reel-caption-tagger` as the next step.
- The agent emits a CONTEXT WRITE REQUEST block at the end of every invocation; the main agent must persist it.
