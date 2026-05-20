---
name: reel-caption-tagger
version: 1
agent: reel-caption-tagger
---

Invoke `reel-caption-tagger` after `reel-script-writer` has finalized the script (or after `reel-editor-handoff` if that step was used). Pass it the finalized script and optionally the editor handoff brief. The agent writes a platform-appropriate post caption — opening line restating the hook value, 1–2 sentences of body context, and the channel catchphrase "และมันก็แค่นั้นเอง" as the closing line (nothing follows) — and selects a hashtag mix of 9–15 tags split into three buckets: 3–5 high-volume (>1 M posts), 3–5 mid-volume (100 K–1 M), and 3–5 niche (<100 K), with a placement note for the target platform (Instagram, TikTok, or YouTube Shorts). Do not use it to rewrite or critique the script, or to produce more than one caption variant unless explicitly asked.

## Notes

- The agent emits a CONTEXT WRITE REQUEST block at the end of every invocation; the main agent must persist it.
- The caption's final line must always be the catchphrase; no CTA or additional content follows it.
