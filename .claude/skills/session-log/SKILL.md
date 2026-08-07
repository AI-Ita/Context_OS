---
name: session-log
description: Closes a block of work by writing a dated entry in the self-improvement log. Use for "log this", "write the session log", "close the session", "sum up what we did".
---

# Session Log — Procedure

*v1.1*

Closes a block of work by writing a short, dated entry in the monthly log and returning the same recap in chat.

**Goal of the procedure:** stop losing feedback, decisions and work that otherwise stay only in the conversation or in the assistant's automatic memory, invisible to the user.

**When it triggers:** manual, at the end of a block of work — "log this", "write the session log", "close the session", "sum up what we did".

**Prerequisites:**
- Write access to `00_context/dump/`.
- A conversation in progress to extract the block from: this procedure does not work on an empty or already-closed chat.

## Steps

### 1. Determine the scope ("from when")
Look back through the current conversation and find where the active block of work starts — usually the last clean change of subject, or the last log already written in this session, whichever is more recent. If the boundary is ambiguous (several subjects mixed, no clear break), propose the scope you identified in one line ("Summarising from [X], correct?") and wait for confirmation before writing.

### 2. Filter, then categorise
Threshold first, list second. A line is justified only if it matters for the future: a behaviour to repeat or avoid, a decision that will need re-reading, a fact that changes a project's state. Process details internal to the session (where a file was saved, what format was chosen for a list, technical steps of the build) do not qualify even when true. When in doubt, a session produces 1-2 lines, not 4.

For every fact that clears the threshold, assign a category: `[feedback]` (a correction or preference that changes how the system behaves in future), `[recap]` (what was done, decided or produced, with no future implications), `[other]` (an open thread, a question left unanswered).

### 3. Write into the current month's log
Check the date with a command before naming the file. File: `00_context/dump/YYYY-MM.md` — create it if the month does not exist yet, with the same header already in use. Line format: `- **YYYY-MM-DD [category]:** content in 1-2 lines.`

### 4. Return the recap in chat
Paste into chat the same lines you just wrote, without reformatting or expanding them — it is the same information, not a second summary. No preamble.

---

## Optional Resources
- [[operating-manual]] (`99_system/operating-manual.md`) — only if you need to revisit the general rules of the system, not on every run.

## Things to Know
- If building the recap requires reading long messages or several files, state an estimate of the tokens used and flag whether there is a cheaper way to get the same result.
- Any automatic trigger should be validated over 2-3 manual runs before being introduced: an over-sensitive trigger writes noise into the log (weak or badly categorised entries) that the user then has to clean up by hand — the cost shifts from "the AI writes too little" to "the user has to filter more".
- If it becomes automatic, it has to be coordinated with Rule 14 of `CLAUDE.md` (simultaneous writing to the assistant's automatic memory), otherwise the same line risks being written twice.

## History Log
- [2026-07-23] Procedure created.
- [2026-07-23] Fix to Step 2: the first real test produced 4 lines for a session worth 1 (internal process details logged as if they mattered). Added the relevance threshold before categorisation.
- [2026-07-26] Register made impersonal. Corrected the pointer to the general rules, which referenced a path that was no longer valid.
