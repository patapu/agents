---
name: reel-news-scout
version: 1
agent: reel-news-scout
---

Invoke `reel-news-scout` after `reel-creator` and before `reel-hook-writer` when the user wants news-based or news-informed reel content. Pass it the CONCEPT BRIEF and optionally a channel context file. The agent checks the `research/` cache before searching (news goes stale fast — cache hits are rarer than for trend-scout), then searches trusted Thai sources first (thairath, matichon, Bangkok Post, etc.) and major international outlets only when a story meets strict MAJOR criteria. Each story is verified across at least 2 sources, categorized, and assessed for reel angle potential. Results are written to `research/<YYYY-MM-DD>/<slug>.md` and logged to `_daily.md` via Bash append. Do not use it to write scripts, hooks, captions, or fabricate headlines.

## Notes

- Writing the research file is mandatory — returning a briefing without persisting it is treated as a failure.
- The agent writes a context log to `.context/runs/{task_id}/agent-reel-news-scout.md` at the end of every invocation.
