---
name: Knowledge Pill
description: Distils a recurring competence into a dense operational file to call up when needed, saved in 00_context/knowledge_pills/. Use for "make me a pill on X", "create a cartridge".
---

# Knowledge Pill — Procedure

*v1.1*

Turns a competence you need repeatedly into a single operational file, to hand the assistant when that competence is needed — instead of explaining it again every time.

**Goal of the procedure:** stop rebuilding the same reasoning every session. A pill is borrowed competence: you call it up, apply it, put it away.

**When it triggers:** when the user asks for a pill on a topic, or when you notice the same thing has been explained again across several sessions.

**Prerequisites:**
- A defined topic and at least one real source to distil from — a document, a piece of research, a manual, a set of notes.

## Steps

### 1. Check it really is a pill
A pill is a **method reusable regardless of the subject**: a copywriting structure, a sales method, a way of running an interview. If instead it is research or data on a specific domain (a market, an algorithm, a sector), it is not a pill: it is domain knowledge and lives in `02_wiki/`.

The test: "is this still useful if I completely change project or client?" Yes → pill. No → wiki.

If a nearby pill already exists, propose extending it instead of creating a second one.

### 2. Gather the sources
Documents, research, transcripts, notes. A pill written from memory is worth as much as an opinion: it needs real material to distil from. If the sources are not there, say so and stop instead of filling the file with generalities.

### 3. Distil, do not summarise
A summary reports what the source says. A pill says **what to do**. The difference is between "the author argues objections should be pre-empted" and "list the three most likely objections before presenting the price".

File structure:

```markdown
# [Name of the competence]

[1-2 lines: what this pill is for and when to call it up.]

## When it applies
[The concrete situations where this competence is needed — not generic: at least one example tied to the user's real work, not just the abstract category.]

## How it works
[The method as steps or operating principles. Dense: no introductions,
no repetition, no historical context. Only what you execute.]

## Typical mistakes
[Only the ones that actually cost something — not an exhaustive list.]

---
**Sources:** [what it was distilled from]
```

### 4. Save and index
File in `00_context/knowledge_pills/`, named in `kebab-case.md`. Add the entry to the folder index in the same operation: a pill that is not indexed will never be called up, and a pill never called up does not exist.

### 5. Clarity check
Before closing, explain in your own words — not by pasting the file — what the pill does, when it applies and how it is triggered, with an example tied to the user's real context. This is not a formality: if the user says they did not understand, the file needs revising (example too abstract, "when it applies" not concrete), not just re-explaining out loud.

### 6. State how to use it
Close by telling the user the exact phrase that calls it up in a future session — for example "read the pill on X and apply it to this text". A pill is only worth something if the user knows how to trigger it.

---

## Things to Know
- A pill replaces a repeated line of reasoning, not a reference document. If it runs past two or three pages, it is probably two pills.
- Pills age: when one is used and turns out to be inaccurate, it gets corrected immediately instead of worked around in conversation.
- **Triggering is never automatic.** A pill does not invoke itself: it stays silent until the user (or a skill that calls it explicitly) asks for it to be read and applied. If during a conversation you notice a repeated pattern that would deserve a pill, existing or new, that is conversational proactivity (Rule 9 of CLAUDE.md) — not a mechanism of the pill itself.

## History Log
- [2026-07-26] Procedure created.
- [2026-07-27] v1.1 — Added Step 5 "Clarity check" (the user had not understood what a pill did or when it applied, after one was created from dense text with no concrete example). Template: "When it applies" now requires an example tied to real context, not just the abstract category. Clarified in "Things to Know" that a pill never triggers automatically.
