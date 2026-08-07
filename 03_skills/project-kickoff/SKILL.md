---
name: project-kickoff
description: Opens a new project in the second brain: folder, rules, state file, row in the projects table and entry in the index. Use when starting a new project or line of work.
---

# Birth of a Project — Procedure

*v1.0 — 2026-07-24: created.*

Creates the minimum governance skeleton for a new project in `10_projects/`, from the root conversation, making sure it is immediately reachable from the Router and consistent with the propagation rules.

**Goal of the procedure:** stop projects being born without `CLAUDE.md` and `memory.md`, or without a row in the root table — the two gaps observed most often.

**When it triggers:** manual, every time a new project is born in `10_projects/` — always from the root conversation, never from a project conversation.

**Prerequisites:**
- A session open at root level (kick-off always happens there, never inside a project conversation).
- One clear sentence on what the new project does — if it is not clear, ask before proceeding.

## Steps

### 1. Check it does not already exist
Search (by name, synonyms, domain) whether an existing project or subfolder already covers the same need. If you find something close, propose it before creating from scratch.

### 2. Weigh it up
One question only: **will this project accumulate decisions or state that will need re-reading a week from now?**
- No (a routine that only produces repeated output, with no decisions to revisit) → skip Steps 3-4: the operating file itself is enough, with 2 lines at the top explaining what it is. If it is that light, consider whether it belongs in `03_skills/` as a procedure rather than in `10_projects/` as a project.
- Yes (anything with clients, active channels, decisions that change) → carry on with the full scheme.

### 3. Create the folder and the CLAUDE.md
Copy [[claude-template]] (`99_system/templates/claude-template.md`) into `10_projects/<name>/CLAUDE.md`: role in one line, scope (what belongs here, what does not and where it goes instead), internal structure only if not obvious, inherited root rules made explicit (above all: when this conversation may write to root for macro events).

### 4. Create the memory.md
Copy [[memory-template]] (`99_system/templates/memory-template.md`) into `10_projects/<name>/memory.md`, fill in the header and delete the sections that stay empty.

### 5. Row in the "Active Projects" table
Add the row to the root `memory.md`: correct path, status "Active", next step in one sentence. In the same session — it is a macro event, it is not postponed. This also applies to the "light" projects from Step 2 (no CLAUDE.md or memory.md): the row in the root table is there regardless.

### 6. Entry in `10_projects/projects_index.md`
Add the entry to the projects index, in the same operation. Without it, the project exists on disk but is unreachable through the Router → index → file cascade (Rule 1). These are two distinct writes and both are needed: the table from Step 5 carries the *state*, the index carries the *reachability*.

### 7. archive.md — only when needed
Do not create it at kick-off. It is born the first time a state in `memory.md` is replaced, not added to. It does not apply to light projects (they have no memory.md to replace).

## Optional Resources
- [[claude-template]] — skeleton to copy at Step 3.
- [[memory-template]] — skeleton to copy at Step 4.
- [[operating-manual]] (`99_system/operating-manual.md`) — if you need to revisit the general rules on project birth.

## Things to Know
- If the project is born by moving or merging content that already exists elsewhere in the vault, that alone is not enough: also apply the rule "always links, never free-text paths in references" and check every reference to the old path before considering the birth complete.

## History Log
- [2026-07-24] Procedure created. Born from a real case: several projects in `10_projects/` without `CLAUDE.md` or `memory.md`, and an "Active Projects" table with paths that no longer existed on disk.
- [2026-07-26] Added Step 6 (entry in `projects_index.md`): it was missing entirely, so a project created by following the procedure to the letter was born orphaned from the index despite having its state row in root. Found in a real case, created the same day and left unindexed.
