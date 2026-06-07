# Universal Agent Handoff Specification (`HANDOFF.md`)

A platform-agnostic markdown convention for preserving session state between AI
agent runs.

`HANDOFF.md` is intentionally small. It is a project-level, session-level file:
use it to record the work currently in motion, the verification command that
proves the state, and the exact next instruction for the next agent.

In this repository, `HANDOFF.md` is the canonical template. It should remain
universal and unbound to any one app, repo, branch, or agent session.

It does not replace more durable systems such as long-term memory, issue
trackers, or workspace-wide heartbeat files. Those systems can coexist with this
spec; `HANDOFF.md` should point to them when they matter for the current task.

## Philosophy

When an AI agent times out, loses context, or hands work to another model, the
user should not have to reconstruct the task from scratch.

This spec keeps continuity in plain markdown because language models and humans
both read it well. The file should protect:

1. The goal and the reason behind important choices.
2. The exact interrupted work item.
3. Dead ends and blind spots that would waste the next session.
4. The verification command that confirms the handoff is still true.

Keep the file boring, current, and easy to diff.

## How to Use

1. Put `HANDOFF.md` in the root of each project that needs session continuity.
2. Add the `.agentrules` instructions to the agent's workspace config, custom
   instructions, or imported global rules.
3. At session start, read `HANDOFF.md` before planning or editing.
4. Before ending a multi-step session, update `HANDOFF.md` with the current
   state, blockers, and next instruction.

For multi-project work, prefer one `HANDOFF.md` per project root. Keep
cross-project durable context in a separate memory or workspace-level file and
link to it from the relevant project handoff only when needed.

When maintaining this template repository, do not fill `HANDOFF.md` with the
current editing session. Keep task-specific state in the consuming project that
copied the template.

## Conflict Handling

This spec is file-based, so it cannot guarantee writes from multiple agents will
not collide. Agents should follow a simple merge discipline:

1. Read the current `HANDOFF.md` immediately before writing.
2. Preserve newer unrelated checklist items and blind spots.
3. If two entries conflict, keep both facts and mark the conflict in `Known
   Blind Spots`.
4. Update `Last Updated` only after merging the latest file contents.

When available, normal Git conflict markers, editor locks, or repository-level
review should be treated as the source of truth.

## Master Template

```markdown
# AGENT HANDOFF STATE

Schema Version: 1

## High-Level Objective
* **Core Goal:** [Clear, single-sentence summary of the ultimate deliverable]
* **Target Domain/Format:** [e.g., Web app, spreadsheet, market report]
* **Style Constraints:** [e.g., Minimal prose, strict validation, existing design system]
* **Key Decisions & Rationale:** [Choices made and why they should persist]

## Session Metadata
* **Last Updated:** [YYYY-MM-DD HH:MM:SS UTC]
* **Previous Agent/Model:** [e.g., Codex, Claude, Gemini, OpenClaw]
* **Current Status:** [Success / In-Progress / Interrupted / Blocked]

## Environment & Source Context
* **Active Working Files:** [Files, directories, or documents currently in scope]
* **Sources/Data Inputs Used:**
  * `input_file.ext` -> [What has already been parsed or extracted]
* **Git Branch & Commit:** [e.g., Branch `main`, HEAD at `a1b2c3d`]
* **Running Services/Ports:** [e.g., Vite dev server on localhost:3000]
* **Verification Command:** [Mandatory command or explicit `Manual: ...` check]
* **Hard Constraints:** [Environment limits, dependency restrictions, policy constraints]

## Progress Ledger

### Completed Milestones
- [x] Phase 1 baseline established.
- [x] Primary structure and constraints validated.

### In-Flight / Interrupted
- [ ] Currently executing [Task X]. [Exact file, line, section, or logical block]

### Remaining Backlog
- [ ] Immediate next milestone.
- [ ] Final polishing and verification.

## Known Blind Spots & Dead Ends
* **Gaps/Issues:** [Failed approaches, rate limits, missing data, or unresolved risks]
* **Assumptions Made:** [Implicit choices the next agent should verify if relevant]
* **Conflicts:** [Concurrent write conflicts or competing interpretations, if any]

## Instructions for the Next Agent
> Review the In-Flight section, open the active working files, run the
> verification command to confirm the project state, and resume from the exact
> interrupted step. Keep the solution minimal and match the surrounding project
> conventions.
```
