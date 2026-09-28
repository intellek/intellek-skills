---
name: context-efficient-work
description: "Trigger: multirepo, broad analysis, SDD, memory, delegation, tests, review. Load only the context needed for scoped repository work."
license: Apache-2.0
metadata:
  author: "intellek"
  version: "1.0"
---

## Activation Contract

Load for multi-repository work, broad codebase analysis, SDD, persistent-memory retrieval, delegation, test/build execution, or review. Do not load for a self-contained question or a one-file mechanical action.

## Hard Rules

- Start with the exact user goal and affected repository; do not pre-load unrelated context.
- Prefer targeted symbol or path inspection. Read only the files needed to answer the current question.
- Preserve local work and confirm Git state in each affected repository before writing.
- Do not duplicate long protocols in replies, prompts, or `AGENTS.md`; reference this skill instead.

## Decision Gates

| Situation | Required action |
| --- | --- |
| Simple, self-contained request | Reply without skills, memory, agents, or exploration. |
| Prior decision or ongoing work is relevant | Retrieve only matching memory/context. |
| Understanding needs more than three files | Delegate one narrowly scoped mapping task. |
| Multiple repositories are affected | Map dependencies, then use one worker per repository when delegation is authorized. |
| Test, build, install, or review is needed | Run only focused validation and report its boundary. |
| SDD is explicitly requested or accepted | Load only the relevant SDD phase skill and its declared artifacts. |

## Execution Steps

1. State the scope and whether the request is read-only or change-authorized.
2. Check the nearest `AGENTS.md` and repository status only for affected paths.
3. Use narrow searches and bounded reads; stop once evidence answers the goal.
4. Delegate only work that would otherwise require broad reading, multi-file preparation, or execution isolation.
5. Validate the changed behavior with the smallest relevant command or structural readback.

## Output Contract

Return a short result with affected paths, evidence or validation, and any boundary or pending decision. Do not report token estimates.

## References

- `../skill-creator/references/skill-style-guide.md` — skill format guidance when available in the consuming workspace.
