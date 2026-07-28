---
name: System Feedback
description: Writes immediately into the structural problems log when the user complains about rules, indexes or conventions of the second brain, and fixes the rule at the source.
---

# System Feedback — Procedure

*v1.0*

Recognises a complaint or correction from the user about the structure or mechanics of the vault itself and writes it straight into `system-feedback.md` — no triage step, no accumulating for a later review.

**Goal of the procedure:** make sure a complaint about the vault's mechanics becomes a written entry in the same exchange in which it is voiced, instead of depending on the memory of the chat.

**When it triggers:** the user complains about or corrects something concerning the rules, indexes, conventions or procedures of the vault — not the work of a specific project (that stays in that project's `memory.md`) and not a personal preference about them or how to work with them (that is [[session-log-procedure]]).

**Prerequisites:**
- Being able to tell a system complaint apart from a session-log case — see `CLAUDE.md` Rule 14 and the header of `system-feedback.md`.

## Steps

### 1. Classify the complaint
Does it concern the structure or mechanics of the vault (rules, indexes, conventions, procedures)? Carry on here. Does it concern the user themselves or how the AI should work with them? Then this is not the procedure — go to [[session-log-procedure]].

### 2. Write the entry, immediately
Check the date with a command (never infer it). Add to `system-feedback.md`, format: `- **YYYY-MM-DD:** [1-2 lines: what is wrong or missing, and what was corrected]`.

### 3. Write the rule where it belongs, in the same operation
If the complaint calls for a new or amended rule: `CLAUDE.md` if it is a structural invariant, `99_system/operating-manual.md` if it is a convention. Logging the intention is not enough — the rule has to be written now, or the complaint comes back.

### 4. Fix the existing files that break the rule
If they are few and identifiable, fix them in the same operation. If the scope is wide (many files, a vault-wide search), report the size of it before proceeding — do not launch a mass cleanup without confirmation.

### 5. Stop
No changes beyond the above without a new request.

## Optional Resources
- [[operating-manual]] (`99_system/operating-manual.md`) — where the conventions fixed at Step 3 live.
- `CLAUDE.md` at root — where the structural rules fixed at Step 3 live.

## Things to Know
- No triage step: recognition and writing happen in the same exchange in which the complaint is voiced.

## History Log
- [2026-07-26] Procedure created.
