---
name: reel-thai-wordplay
version: 1
agent: reel-thai-wordplay
---

Invoke `reel-thai-wordplay` as an optional specialist step before `reel-hook-writer`, but only when the CONCEPT BRIEF or the user explicitly requests Thai wordplay (มุขเล่นคำ) content. Pass it the anchor word or topic from the brief. The agent reads the language-rules feedback file, generates 3–5 pun seed candidates using real Thai wordplay paths (เสียงพ้อง, ผวนคำ, double meaning, compound puns), runs a self-check rubric on each seed (genuine phonetic link, real-world objects and functions verified, all words exist in Thai, payoff loops back to anchor), discards any failing seed, and returns a structured PUN SEED PACK with a recommended seed for `reel-hook-writer`. Do not invoke for news, education, lifestyle, motivation, or general talking-head reels that do not centre on wordplay.

## Notes

- The agent emits a CONTEXT WRITE REQUEST block at the end of every invocation; the main agent must persist it.
- The recommended seed from the PUN SEED PACK is passed directly to `reel-hook-writer` as its input.
