---
name: reel-trend-scout
version: 1
agent: reel-trend-scout
---

Invoke `reel-trend-scout` after `reel-creator` has produced a CONCEPT BRIEF and before any scripting work begins, when the user wants trend-informed content. Pass it the CONCEPT BRIEF and optionally a channel context file. The agent first checks the `research/` cache (last 7 days) for a matching topic slug before conducting a web search; on a cache miss it searches for trending audio tracks, visual formats, and content themes on Instagram, TikTok, and YouTube Shorts, then writes a new research file to `research/<YYYY-MM-DD>/<slug>.md` and logs a line to `_daily.md` via Bash append. It returns a structured TREND BRIEFING including a Format Fit verdict and fading trends to avoid. Do not use it to write scripts, hooks, captions, or make production decisions.

## Notes

- Writing the research file is mandatory — returning a briefing without persisting it is treated as a failure.
- The agent writes a context log to `.context/runs/{task_id}/agent-reel-trend-scout.md` at the end of every invocation.
