---
name: reel-knowledge-scout
version: 1
agent: reel-knowledge-scout
---

Invoke `reel-knowledge-scout` after `reel-creator` has produced a CONCEPT BRIEF and the genre is education, or the topic is science/tech or psychology/behavior-heavy. It searches Thai sources first (Kapook, Sanook, National Geographic Thailand, Dek-D, The Standard, The Matter, Thai PBS, etc.) and falls back to English sources (Wikipedia, ScienceDirect, peer-reviewed journals, Scientific American, Nature, MIT Technology Review, Psychology Today, etc.) when Thai coverage is thin. It checks the `research/` cache (last 30 days) before searching — cache hits are common for evergreen topics. It returns a KNOWLEDGE BRIEFING with 5–8 facts, each with a one-line "twist seed" (short PAYOFF-beat angle suggestion for `reel-script-writer`). Results are written to `research/<YYYY-MM-DD>/<slug>.md` and logged to `_daily.md` via Bash append. Pass the KNOWLEDGE BRIEFING to `reel-hook-writer` alongside any TREND BRIEFING. `reel-knowledge-scout` runs parallel to `reel-trend-scout` and `reel-news-scout` and does not replace either. Do not use it to write scripts, hooks, captions, or fabricate facts.

## Notes

- Writing the research file is mandatory — returning a briefing without persisting it is treated as a failure.
- The agent writes a context log to `.context/runs/{task_id}/agent-reel-knowledge-scout.md` at the end of every invocation.
