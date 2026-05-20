---
name: reel-production
version: 1
agent: reel-production
---

Invoke `reel-production` as the final QA gate before publishing, or after any individual reel artefact is produced and needs to be checked. Pass it any subset of pipeline artefacts: CONCEPT BRIEF, TREND BRIEFING, NEWS BRIEFING, HOOK SET, SCRIPT, EDITOR HANDOFF, and/or CAPTION & HASHTAG PACKAGE. The agent applies genre-aware channel rules (catchphrase placement, no CTA after catchphrase, 4-beat script structure, duration and word budget, hook set composition, hashtag mix) and cross-artefact consistency checks (genre lock, chosen hook in script, trend items referenced, caption opener matches hook, clip map covers all beats, format fit not contradicted), returning a REEL PRODUCTION REVIEW grouped by severity: critical, major, minor, nit. It is strictly read-only and will not edit artefacts. On every review the agent automatically Globs `research/<date>/<slug>-verified.md` for the reel's slug — no caller action is required. If a `-verified.md` is found, the agent asserts `schema_version == 1` and applies verification QA findings: CRITICAL if a LOW/UNVERIFIED claim appears unhedged in voiceover; MAJOR if `recommendation == PROCEED-WITH-CAUTION` but no hedging language is present in the SCRIPT; MAJOR if `recommendation == REJECT` and a SCRIPT artefact exists. If no `-verified.md` is found, the agent raises MINOR findings when the genre is `news` or when the SCRIPT or NEWS BRIEFING contains statistics or named numerical claims — these MINOR flags are advisory prompts to run `reel-trend-verifier` before publishing, not hard blocks.

## Notes

- The agent emits a CONTEXT WRITE REQUEST block at the end of every invocation; the main agent must persist it.
- If zero findings, the agent returns a short "ready to publish" verdict instead of severity sections.
