---
name: System Check
description: Mechanical checks on the second brain: broken links, orphan files, stale paths, non-conforming naming, dates not propagated. Use for "check the system", "run a cleanup", "check the vault".
---

# System Check — Procedure

*v1.0*

Scans the vault for mechanical, deterministic breakage — broken links, orphans, stale paths, non-conforming naming, badly propagated dates — without touching organisational judgement.

**Goal of the procedure:** catch structural breakage with a repeatable check, instead of discovering it by accident.

**When it triggers:** on demand ("run a system check", "check the vault"), or called as a first phase by a broader review procedure.

**Prerequisites:**
- The whole vault root mounted, not a specific project.

## Steps

### 1. Check the date
Get the real date with a command, never infer it from the latest entries in the files — it is needed to date every line of the report.

### 2. Map the structure
List (do not read) all `CLAUDE.md`, `memory.md`, `archive.md`, `index_*.md` and `*_index.md` files in the vault, including every level of `10_projects/`. This is the list the checks below run against — structure only, not content.

### 3. Broken or ambiguous links
For every wikilink `[[ ]]` or path link found in the mapped files: verify it resolves to exactly one file. Flag both links to nothing and ambiguous ones (several files with the same name in the vault).

### 4. Orphan files
Files inside an indexed folder (`02_wiki/*`, `03_skills/`, etc.) that appear in no index of their category — unreachable through the cascade even though they exist on disk (Rule 1 of `CLAUDE.md`). Flag them.

### 5. Stale paths
References to paths that no longer exist on disk (folders renamed, moved, flattened). Compare the paths written in the files against the real tree.

### 6. Non-conforming naming
Files that break the current conventions (kebab-case for wiki notes, the two-level `*_index.md` / `index_<category>.md` scheme for folders, and so on — the list lives in `99_system/operating-manual.md` §6).

### 7. Macro/micro discrepancies (dates)
For every project in the "Active Projects" table of the root `memory.md`: compare the "Last updated" date with the one in that project's own `memory.md`. Flag every mismatch — a candidate for missed propagation.

## Final report
A list by category (broken links, orphans, stale paths, naming, date discrepancies), each with the file and line involved. **No changes applied in this run — findings only.** Corrections are decided with the user, step by step or in one batch.

---

## Things to Know
- Mechanical and deterministic checks only, zero organisational judgement: assessments like "this folder is growing, consider a dedicated index" or "these projects have stalled" do not belong in this procedure.
- It reports, it does not correct: fixes are decided with the user after the report.

## History Log
- [2026-07-26] Procedure created.
