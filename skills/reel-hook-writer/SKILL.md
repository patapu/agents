---
name: reel-hook-writer
version: 1
agent: reel-hook-writer
---

Invoke `reel-hook-writer` after `reel-trend-scout` or `reel-news-scout` has produced a briefing (and after `reel-thai-wordplay` if the wordplay path was taken, and after `reel-trend-verifier` if claim verification was requested or required). Pass it the CONCEPT BRIEF and the trend or news briefing. The agent identifies the core tension, promise, or curiosity gap for the reel and writes 5 distinct hook variants — one each of question, bold-claim, story-open, pattern-interrupt, and stat/proof — scoring each 1–10 for estimated stop-scroll strength and naming a recommended hook. The channel catchphrase "และมันก็แค่นั้นเอง" must not appear in any hook variant — it is reserved for `reel-script-writer`'s CLOSER beat. When a `research/<date>/<slug>-verified.md` file (produced by `reel-trend-verifier`) is passed, the agent asserts `schema_version == 1` before writing any hooks; a `REJECT` recommendation causes the agent to return `HOOK SET REFUSED` with no hooks written, a `PROCEED-WITH-CAUTION` recommendation causes the agent to prepend a `CAUTION NOTICE` listing LOW/UNVERIFIED claims and forbid hook variants whose central premise rests solely on those claims, and under any recommendation the agent never writes a hook whose primary factual premise is a claim labelled `LOW` or `UNVERIFIED`. If no `-verified.md` is provided, the agent proceeds as normal with no behavioural change. Do not use it to write the full script, research trends, or produce captions.

## Notes

- The recommended hook text should be passed verbatim to `reel-script-writer` to use as the SETUP opening line.
- The agent emits a CONTEXT WRITE REQUEST block at the end of every invocation; the main agent must persist it.
