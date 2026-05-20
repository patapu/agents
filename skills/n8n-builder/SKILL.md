---
name: n8n-builder
version: 1
agent: n8n-builder
---

Invoke `n8n-builder` when the user wants to create, inspect, validate, or modify an n8n workflow, or when `image-prompt-writer` or `image-prompt-editor` hands off a prompt for webhook firing. For workflow construction, pass it the spec or existing workflow JSON; the agent searches for relevant nodes with `mcp__n8n__search_nodes`, reads SDK references with `mcp__n8n__get_sdk_reference`, builds the workflow JSON with `mcp__n8n__create_workflow_from_code`, and validates with `mcp__n8n__validate_workflow` (up to 3 iterations). For image generation, pass it the PROMPT text; the agent verifies `N8N_WEBHOOK_BASE_URL` is set, POSTs to `/webhook/openai-image-gen`, and surfaces the `image_url`, `revised_prompt`, and availability of `image_b64`. It does not edit project source code or design application architecture.

## Notes

- The agent emits a CONTEXT WRITE REQUEST block at the end of every invocation; the main agent must persist it. On failure, the main agent must also append a summary to `.context/agents/n8n-builder/known-mistakes.md`.
- Do not invent node names — the agent always searches or looks up SDK references first.
