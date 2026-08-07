# Operating Manual — Structure and Rules

> Rules and structure only: this is the reference the maintenance procedures use to know what "right" looks like in the system.
> **Hierarchy:** if this file contradicts the root `CLAUDE.md`, `CLAUDE.md` wins.

---

## 1. Structure

```
system/
├── CLAUDE.md            ← rules + router
├── memory.md            ← current state
├── archive.md           ← history
├── 00_context/          ← identity and personal material
├── 01_raw/              ← raw inbox (+ _processed/)
├── 02_wiki/             ← consolidated knowledge
├── 03_skills/           ← procedures and skills
├── 10_projects/         ← projects
└── 99_system/           ← manuals, templates, system feedback
```

Root holds governance only: no operational work. Every project in `10_projects/` repeats the same three-file governance pattern.

## 2. The three governance files

| File | Holds | Changes |
|---|---|---|
| `CLAUDE.md` | rules, router, scope | almost never |
| `memory.md` | current state, open threads, next step | constantly |
| `archive.md` | what has been replaced, with a date | additions only, at the top |

- Rules never hold state: if a statement can go stale, it belongs in `memory.md` and the router points at it.
- `archive.md` only receives information leaving a `memory.md` because it was replaced. It is not a maintenance log.
- `archive.md` is born at the first replacement, not at kick-off.

## 3. Propagation

- **Micro** (one step, one detail): stays in the project's `memory.md`.
- **Macro** (a project's status, a goal closed, a decision opened or closed, a project born, folders moved or renamed): goes into the root `memory.md` as well, immediately, in the same session. Whoever is working in the project writes to root themselves.
- A move or a rename requires checking every reference to the old path and correcting it.

## 4. Single source of truth

Every fact lives in exactly one `memory.md`, the one at the most specific level. Other levels hold a pointer, never a copy.

## 5. Two-level index

- Main index (`foldername_index.md`): categories and subfolders only, with a description and a counter. Never lists of individual files.
- Category index (`index_<topic>.md`, inside the subfolder): the list of files. Single source of truth for that category.
- A dedicated index once a subfolder passes roughly 4-5 files or nests further; below that threshold, a direct link from the parent index.
- Every file born in an indexed folder is added to the relevant index in the same operation.

## 6. Writing conventions

- **Purpose at the top:** 1-2 lines at the head of every file saying what it is for.
- **References as links,** never free-text paths. If the name is not unique, add the real path in brackets.
- **Description ≠ history:** index entries, procedure steps and operational notes say only what a thing is and does today. Dates, renames and versions live only in the file's changelog or history log.
- **Write what is there, not what is not:** files list real content — what is there, what it does, what belongs there. Never rows or columns dedicated to what is excluded, superseded or absent: an element that does not belong is simply omitted.
- **"Do not do X"** is written only if the opposite mistake would be costly or likely.
- **Absolute dates** in every file that persists.
- **Naming:** `kebab-case.md` for notes, `NN-name.md` for sequenced stages, `_` prefix for service folders.
- **External schemas** (spreadsheet columns, CRM fields, API responses): verify them live on every run. If they do not match and the interpretation is 90%+ certain, proceed and update the file; otherwise stop and ask.
- **Contradictions:** if a new source contradicts (rather than adds to) a statement already written, flag it inline with a callout and leave it there. Do not overwrite: resolving it is the user's call.

## 7. Reading economy

Order of increasing cost: router → targeted search → partial read → full read (small files only). Never scan the whole system. Heavy files are distilled into markdown before they come in; the folders holding them say so and point to the distilled versions.

## 8. Where things go

| Content | Destination |
|---|---|
| Clipping or raw note | `01_raw/` |
| Distilled research on a domain | `02_wiki/<category>/` |
| Framework or method reusable anywhere | `00_context/` |
| Material specific to a project | `10_projects/<project>/resources/` or `inputs/` |
| Finished deliverable | `10_projects/<project>/outputs/` |
| Global executable procedure | `03_skills/` |
| Procedure for a single project | that project's local folder |
| Reminder, to-do | an open thread in `memory.md`. Never an empty file on disk |
| Decision taken, state changed | the `memory.md` at the right level (+ `archive.md` if it replaces something) |

Wiki admission test: "is this still useful if I change project or client?" Yes → `02_wiki/`. No → it stays project material.

## 9. Procedures and skills

- **Procedure (`.md`):** edited directly, in effect on the next read. This is the default.
- **Packaged skill:** the copy that runs is installed separately from the source. Editing the source does not update the installed copy: an explicit reinstall is required. A fix that is not reinstalled does not exist.
- Skill update cycle: edit the source → update the changelog at the top → reinstall → check the expected version appears on the first run.

## 10. Glossary

| Term | Meaning |
|---|---|
| Router | The section of `CLAUDE.md` that says where everything lives |
| Propagation | Taking an event to the right level: micro → project, macro → root |
| Atomic note | One concept, one file, with a cited source and links |
| Macro / micro | Events that change the overall state / details internal to a project |
| Skill deploy | Reinstalling after editing the source |
