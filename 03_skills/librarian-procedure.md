---
name: Librarian
description: Turns the raw material in 01_raw/ into linked atomic notes in the wiki, updates the indexes and archives the originals. Use for "run the librarian", "empty the inbox", "process the raw files".
---

# Librarian — Procedure

*v1.0*

Bridges the two knowledge zones: `01_raw/` is the chaotic inbox, `02_wiki/` the ordered library. It extracts value from raw files and turns it into atomic notes, linked and traceable.

**Goal of the procedure:** empty the inbox while producing reusable knowledge, without losing the source and without blowing up the reading cost.

**When it triggers:** when the user asks to process the inbox, or reports having documents and notes piled up to turn into structured knowledge.

**Prerequisites:**
- Material in `01_raw/`.

## Steps

### 1. Extract clean text
Files in `01_raw/` may include heavy HTML and PDFs: reading them whole burns the context. Extract the text first with whatever tools the environment offers — a conversion command, or a short script written on the spot — and work on the extract.

`.txt`, `.md` and `.csv` files under 50 KB can be read directly, with no intermediate step.

If a file will not extract, leave it where it is, flag it in the final report and carry on with the others.

### 2. Identify the concepts
Find the distinct concepts that deserve a note of their own: frameworks, checklists, procedures, insights, terminology, data.

**Atomicity — one concept, one file.** If a document covers several separate subjects, it produces several notes. Five small notes beat one huge one. The deciding question: "what will I want to search for this information under, six months from now?" — every different answer is a different note.

**Value threshold:** only what is actionable, informative or citable goes in. Navigation, footers, disclaimers and repetition stay out.

**What does not belong in the wiki:** a way of thinking that is reusable regardless of the subject (a copywriting structure, a sales method) is not domain knowledge — it is a framework, and it lives in `00_context/`. Flag it to the user instead of creating it here.

**Contradictions:** if a new source contradicts — rather than adds to — a statement already written in an existing note, do not overwrite. Add a callout at the top of the affected section and leave it there: resolving it is the user's job, not yours.

```
> [!contradiction] [1 line: what is being contradicted]
> Old statement ([source]): ...
> New statement ([source]): ...
```

### 3. Create the notes
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

### 4. Update the indexes, both levels
**Category index** (`02_wiki/<category>/index_<category>.md`) — this is where the real list goes: add the entry under the right topic (create it if missing) and update the header, note count and date. If the category index does not exist yet, create it:

```markdown
# Master Index — <Category>

> N notes | Last updated: YYYY-MM-DD

### [Topic]
- [[note-name]] — one-line description
```

**Root index** (`02_wiki/wiki_index.md`) — only two operations allowed. If you created a new category, add its row under "Categories". If the category already existed, update only the note count. The root index never lists individual files.

### 5. Archive the originals
Move successfully processed files into `01_raw/_processed/`. Originals are never deleted: they are the backup that makes every digestion reversible. Only files that caused problems stay in `01_raw/`.

### 6. Final report
Concise: notes created and where, files archived, files left behind and why, indexes updated.

---

## Things to Know
- If the material in `01_raw/` clearly belongs to a single project and is not general domain knowledge, ask the user whether they would rather file it in that project's folder than in the wiki.

## History Log
- [2026-07-26] Procedure created.
