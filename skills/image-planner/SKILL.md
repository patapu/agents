---
name: image-planner
version: 1
agent: image-planner
---

Invoke `image-planner` as the first step in any image-generation request, including when `reel-creator` or `reel-editor-handoff` emits an IMAGE REQUEST block. Pass it the image request or any reference files (mood boards, brand guidelines, design briefs). The agent designs a structured CONCEPT BLUEPRINT covering subject, style, composition, lighting, mood and atmosphere, palette, negative space and constraints, and technical constraints (aspect ratio, text-in-image risk for gpt-image-1 embedded text). It is strictly read-only — it does not write prompts, call APIs, or invoke downstream agents. The blueprint is the sole input `image-prompt-writer` needs to produce a polished prompt.

## Notes

- The agent emits a CONTEXT WRITE REQUEST block at the end of every invocation; the main agent must persist it.
- If the request involves text embedded in the generated image, the agent will flag the gpt-image-1 text-rendering reliability risk in the blueprint.
