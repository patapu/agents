---
name: image-prompt-writer
version: 1
agent: image-prompt-writer
---

Invoke `image-prompt-writer` after `image-planner` has produced a CONCEPT BLUEPRINT. Pass it the blueprint. The agent converts the blueprint into an optimized OpenAI gpt-image-1 prompt (300–500 characters), leading with the subject, embedding style markers and lighting/composition/mood cues early, and appending a PRECISION block at the end for countable or non-dominant color-placement constraints that gpt-image-1 most often under-renders when left inline. It does not fire the webhook — it returns the finished PROMPT text with a handoff note to pass it to `n8n-builder` for generation. Do not use it to revise an existing prompt based on feedback — that is `image-prompt-editor`'s job.

## Notes

- The agent emits a CONTEXT WRITE REQUEST block at the end of every invocation; the main agent must persist it.
- If the blueprint requests text in the image, the agent flags the gpt-image-1 embedded-text reliability risk before proceeding.
