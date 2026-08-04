---
name: Librarian
description: Sorts the raw material in 01_raw/ between knowledge and projects - creates atomic notes in the wiki, opens or feeds project folders, updates the indexes and archives the originals. Use for "run the librarian", "empty the inbox", "process the raw files", "I dumped some stuff in there".
---

# Librarian — Procedure

*v1.1*

Bridges raw material and the ordered system: `01_raw/` is the chaotic inbox where the user dumps things without thinking about it, `02_wiki/` the library of knowledge, `10_projects/` the home of projects. It extracts value from raw files and sends it where it belongs.

**Goal of the procedure:** empty the inbox while producing reusable knowledge *and* project scaffolding, without losing the source and without blowing up the reading cost.

**When it triggers:** when the user asks to process the inbox, or reports having documents and notes piled up to turn into something structured.

**Prerequisites:**
- Material in `01_raw/`.

## Steps

### 1. Extract clean text
Files in `01_raw/` may include heavy HTML and PDFs: reading them whole burns the context. Extract the text first with whatever tools the environment offers — a conversion command, or a short script written on the spot — and work on the extract.

`.txt`, `.md` and `.csv` files under 50 KB can be read directly, with no intermediate step.

If a file will not extract, leave it where it is, flag it in the final report and carry on with the others.

### 2. Sort before you digest
Raw material is not all of the same nature, and sending all of it to the wiki is the most common mistake. Before creating anything, split what you have read into three piles:

- **Domain knowledge** — still useful even if the user changes project or client. Goes to the wiki: Steps 3-5.
- **Project material** — only makes sense inside a specific piece of work: briefs, decisions, requirements, state, a client's material. Goes to `10_projects/`: Step 6.
- **Personal context** — how the user works, preferences, stable constraints, ways of thinking that are reusable regardless of subject (a copywriting structure, a sales method). Goes to `00_context/`, not the wiki: flag it to the user instead of creating it among the notes.

The test that decides between the first two: **"is this still useful if I change project or client?"** Yes → knowledge. No → project.

A single file can feed more than one pile: a work dump often holds both the state of a project and a reusable technique. You split it, you do not choose.

If a pile is ambiguous, ask — once, with your proposal already formed, not an open question for every file.

### 3. Identify the concepts
On the material in the "knowledge" pile only. Find the distinct concepts that deserve a note of their own: frameworks, checklists, procedures, insights, terminology, data.

**Atomicity — one concept, one file.** If a document covers several separate subjects, it produces several notes. Five small notes beat one huge one. The deciding question: "what will I want to search for this information under, six months from now?" — every different answer is a different note.

**Value threshold:** only what is actionable, informative or citable goes in. Navigation, footers, disclaimers and repetition stay out.

**Contradictions:** if a new source contradicts — rather than adds to — a statement already written in an existing note, do not overwrite. Add a callout at the top of the affected section and leave it there: resolving it is the user's job, not yours.

```
> [!contradiction] [1 line: what is being contradicted]
> Old statement ([source]): ...
> New statement ([source]): ...
```

### 4. Create the notes
One `.md` file per concept, in `02_wiki/` or in the right thematic subfolder. Check which categories actually exist before assuming; create a new one only if the subject is genuinely different from those present.

File name: `descriptive-kebab-case.md`.

```markdown
# [Concept Title]

[Dense, direct summary: key points, concrete numbers, specific techniques.
Only what is explicitly in the source — never inferences presented as facts.
Bullet points instead of long paragraphs.]

## Connections
- [[related-note]]

---
**Source:** `original-file-name`
```

The Connections section goes in only if notes it genuinely links to already exist. No invented links to fill space.

### 5. Update the wiki indexes, both levels
**Category index** (`02_wiki/<category>/index_<category>.md`) — this is where the real list goes: add the entry under the right topic (create it if missing) and update the header, note count and date. If the category index does not exist yet, create it:

```markdown
# Master Index — <Category>

> N notes | Last updated: YYYY-MM-DD

### [Topic]
- [[note-name]] — one-line description
```

**Root index** (`02_wiki/wiki_index.md`) — only two operations allowed. If you created a new category, add its row under "Categories". If the category already existed, update only the note count. The root index never lists individual files.

### 6. Build or feed the projects
On the material in the "project" pile. For every project recognised in the raw material:

**The project does not exist yet** → run `project-kickoff-procedure.md`, which creates the folder, the rules, the state file, the table row and the index entry. Do not improvise a folder structure of your own: the kick-off procedure exists for this, and it guarantees the project is born reachable rather than orphaned.

Then pour the material into the folder you just created: whatever describes the current state goes into the project's `memory.md`, the documents themselves stay as files inside the folder.

**The project already exists** → do not recreate it. Update its `memory.md` with whatever the raw material says that is new, and add the documents to its folder. If the material replaces a previous state rather than adding to it, the old content goes into `archive.md` before being overwritten.

**Recognising a project that was never declared:** a dump may contain work the user has never mentioned to you. If the material describes something with a goal, decisions and a state that evolves, it is a project even if nobody called it one. Propose it to the user before creating it — a project born by mistake costs more than one that was missed.

**When to stop:** if more than three new projects emerge from the material at once, do not open them all. Present the list and let the user say which to start with.

### 7. Archive the originals
Move successfully processed files into `01_raw/_processed/`. Originals are never deleted: they are the backup that makes every digestion reversible. Only files that caused problems stay in `01_raw/`.

### 8. Final report
Concise, split by destination: notes created and where, projects opened or updated, material sent to `00_context/`, files archived, files left behind and why, indexes updated.

---

## Things to Know
- The sorting in Step 2 is what makes this procedure useful on a real dump: the user throws in everything they have, without splitting it, and expects the system to work out where each thing goes.
- A file that feeds both the wiki and a project is still archived once, at the end.

## History Log
- [2026-07-26] Procedure created.
- [2026-08-04] Added upstream sorting (Step 2) and project building (Step 6). Previously the procedure could only produce wiki notes, and the case "the user dumps project-related material into `01_raw/`" ended in a question to the user rather than an action: project material had no route to becoming scaffolding.
