---
name: reel-hyperframes-prep
version: 1
agent: reel-hyperframes-prep
---

Invoke `reel-hyperframes-prep` after `reel-script-writer` has produced a finalized script and before `reel-editor-handoff`, and only when the user has filmed footage that will be processed with HyperFrames-assisted editing. Pass it the absolute path to the footage file, the finalized script from reel-script-writer, an optional corrections list (word-level fixes to apply during transcript cleaning), and an optional project name (default: `my-video`). The agent initialises the HyperFrames project, transcribes the footage audio to `transcript.raw.json`, cleans the transcript against the finalized script and corrections list to produce `transcript.clean.md`, and runs word-level timestamp alignment — returning a HYPERFRAMES PREP REPORT containing the init status, the absolute paths to `transcript.raw.json` and `transcript.clean.md`, word-alignment confirmation, and the next HyperFrames command to run. The agent never overwrites an existing `transcript.raw.json` (it caches and logs a note instead), never rephrases or editorially alters the cleaned transcript beyond what the corrections list and script explicitly authorise, and never skips word alignment — accurate per-word timecodes are mandatory for downstream hyperframe insert placement.

## Notes

- The agent emits a CONTEXT WRITE REQUEST block at the end of every invocation; the main agent must persist it.
- Pass `transcript.raw.json`, `transcript.clean.md`, and the word-alignment confirmation from the HYPERFRAMES PREP REPORT directly to `reel-editor-handoff` as inputs.
