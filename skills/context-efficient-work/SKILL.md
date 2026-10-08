---
name: context-efficient-work
description: "Base operating rules for efficient context, token, and credit usage across tasks. Apply lightweight context hygiene, scoped planning, memory-first retrieval, selective delegation, and cost-aware tools."
license: Apache-2.0
metadata:
  author: "Ronald Ramirez Moran"
  version: "1.1"
---

## Activation Contract

Apply at the start of every conversation and throughout each task. For self-contained questions or mechanical actions, apply the rules without extra exploration, memory calls, agents, or approval rounds.

These are defaults, subject to higher-priority instructions, tool availability, and explicit user preferences. Efficiency must not bypass safety, privacy, required validation, or authorization.

## Core Principle

Treat context as a limited resource. Keep it lean, focused, and intentional without sacrificing correctness or completeness. Avoid unsupported claims about exact token savings, credit costs, or quality degradation.

## Hard Rules

- Start with the exact user goal and affected repository; do not pre-load unrelated context.
- Prefer targeted symbol or path inspection. Read only the files needed to answer the current question.
- Preserve local work and confirm Git state in each affected repository before writing.
- Do not duplicate long protocols in replies, prompts, or `AGENTS.md`; reference this skill instead.

## Operating Rules

### 1. Plan Before Executing Complex Work

- For ambiguous, multi-phase, or dependent multi-tool work, state a brief plan of three to five bullets.
- Seek approval when scope, consequential actions, or unresolved choices require it; an explicit implementation request already authorizes in-scope work.
- Execute simple, unambiguous requests directly. If discovery materially expands scope, flag it and agree on the boundary before expanding.

### 2. Delegate Heavy Work, Not Trivial Calls

- Delegate broad searches, large result sets, batch research, or processing when context isolation outweighs coordination overhead.
- Give each worker a bounded goal and request a distilled summary, evidence, and unresolved issues—not raw responses or full documents.
- Parallelize independent work only; avoid overlapping writes and duplicated investigation. Use supported batch tools when appropriate rather than manual loops.
- Keep necessary intermediate artifacts in permitted workspace or temporary files and reference relevant excerpts. Do not create unsolicited deliverables or persist sensitive data unnecessarily.

### 3. Retrieve Relevant Memory Before Re-explanation

- When projects, preferences, prior decisions, or past work matter, search available memory or session history narrowly before asking the user to repeat context.
- Use retrieved preferences and decisions only when relevant; verify stale or conflicting information against current evidence.
- Store only durable, actionable, non-sensitive facts when permitted. Respect scope, deduplicate, and record corrections rather than retaining conflicting instructions.
- If retrieval is unavailable or insufficient, ask one targeted question; do not invent remembered context.

### 4. Scope Tightly, Expand on Request

- Answer the exact request with the minimum sufficient detail, ordered by relevance.
- Produce the requested deliverable, not extra variants, tangential research, or supplementary files.
- Offer optional expansion briefly instead of doing it preemptively. Concision must not omit necessary evidence, caveats, or requested detail.

### 5. Manage Conversation Length and Phase Boundaries

- At phase changes or after roughly 15–20 substantive exchanges, assess context load; the count is a prompt to reassess, not a mandatory cutoff.
- When context is heavy or the topic changes, suggest a compact handoff or fresh thread if useful and supported.
- Preserve only the goal, decisions, affected paths, evidence, validation, and next actions in a handoff. Reference authorized artifacts rather than repeating obsolete tool output.
- Use isolated workers for substantial phases when beneficial; do not claim to remove existing conversation content or assume a particular compaction mechanism.

### 6. Choose the Least Costly Effective Tool

- Use targeted search or fetch for information retrieval; use a browser only when interaction or rendering is necessary.
- Prefer bounded symbol/path inspection and available API connectors over broad reads. Request only needed fields or result ranges.
- Use a lighter model or tool only when available and adequate; when cost matters, explain relevant tradeoffs without claiming unknown pricing.
- Do not spawn an agent for a single straightforward lookup or skip required checks to save credits.

### 7. Minimize Confirmation Round-Trips

- Do not seek confirmation for routine read-only operations or re-confirm approved in-scope work.
- Batch unresolved decisions into one or two focused questions with clear options.
- Honor instructions to proceed within authorized scope, but retain required safeguards for destructive, external, or otherwise consequential actions.
- Reuse recurring workflow preferences when supported by relevant memory; past approval is not blanket authorization for new actions.

### 8. Connect Rather Than Copy-Paste

- Check available integrations before claiming access is unavailable or asking the user to paste large app contents.
- Prefer authorized connector access and targeted extraction. If a connector is unavailable or disconnected, offer supported setup or request only the necessary excerpt.
- Do not assume named tools or integrations exist, request credentials in chat, or access services beyond the user's authorization.

## Decision Gates

| Situation | Required action |
| --- | --- |
| Simple, self-contained request | Apply these defaults and reply directly; no additional skills, memory, agents, or exploration. |
| Complex or ambiguous request | State a short plan; resolve only decisions not already authorized. |
| Prior decision or ongoing work is relevant | Retrieve only matching memory/context. |
| Broad investigation or large result sets | Delegate a bounded task when isolation provides a net benefit; return summary and evidence. |
| Multiple repositories are affected | Map dependencies, then use one worker per repository when delegation is authorized. |
| Test, build, install, or review is needed | Run only focused validation and report its boundary. |
| SDD is explicitly requested or accepted | Load only the relevant SDD phase skill and its declared artifacts. |
| Information is in a connected service | Check authorized integrations and retrieve only needed data. |
| Context is heavy or the task changes phase | Summarize a compact handoff; suggest a fresh thread only when useful. |

## Execution Steps

1. Identify the exact goal, relevant prior context, and whether the request is read-only or change-authorized.
2. For repository work, check applicable `AGENTS.md` guidance; confirm repository status before writing.
3. Plan complex work, batch necessary questions, and resolve authorization or scope gaps.
4. Choose the least costly effective tool or connector; use narrow searches and bounded reads.
5. Delegate only when workload or isolation justifies it; keep the main thread focused on decisions and summaries.
6. Validate changed behavior with focused checks that cover the affected behavior and all required validation.
7. Check that the response covers only the requested scope; compact or hand off at phase boundaries when useful.

## Output Contract

Return a short result with affected paths, evidence or validation, and any boundary or pending decision. Do not report token estimates.

## References

- `../skill-creator/references/skill-style-guide.md` — skill format guidance when available in the consuming workspace.
