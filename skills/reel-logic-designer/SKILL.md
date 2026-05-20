---
name: reel-logic-designer
version: 1
agent: reel-logic-designer
---

Invoke `reel-logic-designer` after at least one scout (`reel-trend-scout`, `reel-news-scout`, or `reel-knowledge-scout`) has produced a briefing and BEFORE `reel-hook-writer`. Pass it the CONCEPT BRIEF (required) and the scout briefing (required — TREND / NEWS / or KNOWLEDGE); optionally pass a user-supplied premise/argument (triggers Validation mode) and/or a PUN SEED PACK from `reel-thai-wordplay` (if the มุขเล่นคำ path is active). In Discovery mode (default, when no user premise is supplied) the agent proposes 2–3 candidate content logics drawn from the scout briefing, evaluates them against the CONCEPT BRIEF's genre/audience/emotion constraints, and recommends the strongest one with reasoning; in Validation mode (when the user has supplied a logic/premise) it checks the supplied logic on four axes — alignment, scout support, argument completeness, and stop-scroll potential — and either passes it through or flags failures with targeted repairs. Either mode returns a CONTENT LOGIC PLAN containing the core claim (one sentence), the 3-step argument structure (Setup premise → Escalation move → Payoff resolution), target emotion at PAYOFF, why-it-works reasoning, and wordplay fit if applicable; Discovery mode includes 2–3 candidates with a Recommended pick, while Validation mode includes per-criterion verdicts plus either the validated logic or a VALIDATION FAILED block with a recovery option. The CONTENT LOGIC PLAN is required input for both `reel-hook-writer` (so hooks land on the actual premise) and `reel-script-writer` (so SETUP/ESCALATION/PAYOFF beats follow the designed logic) — do not invoke `reel-hook-writer` without first obtaining a CONTENT LOGIC PLAN from this agent. The agent does not write hooks, script lines, or catchphrases, and does not perform web research — all factual material must come from the scout briefings.

## Notes

- If a PUN SEED PACK from `reel-thai-wordplay` is present, pass it alongside the CONCEPT BRIEF so the agent can score candidates on pun-landing fit and annotate the PAYOFF beat accordingly.
- The agent emits a CONTEXT WRITE REQUEST block at the end of every invocation; the main agent must persist it.
