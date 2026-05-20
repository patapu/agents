---
name: image-prompt-editor
version: 1
agent: image-prompt-editor
---

Invoke `image-prompt-editor` to revise an existing image prompt based on reviewer feedback (from `image-reviewer`) or direct user notes. Pass it the original prompt, the feedback or findings, and optionally the original CONCEPT BLUEPRINT as the reference target. The agent diagnoses what in the prompt caused the reported issue (wrong style, composition off, colors wrong, RENDERED GAP not captured, etc.), applies minimal targeted edits while preserving phrasing that was working, maintains or adds a PRECISION block for constraints gpt-image-1 under-renders, and returns an ORIGINAL / REVISED diff plus a handoff note to pass the revised prompt to `n8n-builder` for re-generation. Do not use it to write a prompt from scratch — that is `image-prompt-writer`'s job.

## Notes

- The agent emits a CONTEXT WRITE REQUEST block at the end of every invocation; the main agent must persist it.
- If the feedback would require gutting more than 50% of the prompt, the agent flags that a full rewrite via `image-prompt-writer` may be more appropriate.
