# First Run — Procedure

*v1.0*

Sets up a freshly installed system: short interview, fills in `memory.md`, opens the first project, puts the user in a position to work.

**Goal of the procedure:** take the user from "a folder of empty files" to "a system that knows who I am and what I am working on" in a few minutes, without them having to read documentation.

**When it triggers:** at the start of a session, when `memory.md` is still not filled in (see Step 1). The trigger is the first-run rule in `CLAUDE.md`, not a user command.

**Prerequisites:**
- The system folder connected to the session.

## Steps

### 1. Check that it is actually needed
Read `memory.md`. If the "Identity" section still contains the placeholder text in square brackets, the system is new: carry on. If it is already filled in, the system is in use: do not run this procedure, and answer the user's request normally.

### 2. Say what you are about to do
One sentence, not a speech: what you do, how many questions you will ask, how long it takes. Then go to the first question.

### 3. Ask three questions, one per message
Never all at once, never more than three in total. Each one fills a specific section of `memory.md`:

1. **"Who are you and what do you do?"** — one line, not a CV. → Identity section.
2. **"What are you working on right now? One to three things."** → Active Projects table.
3. **"What do you want to achieve in the next two weeks? Or what are your goals?"** → Goals section.

If an answer is vague, ask for clarification on that one before moving to the next. If the user skips a question, leave the matching section empty and move on: it fills in later.

### 4. Fill in `memory.md`
Check the date with a command, never infer it. Write Identity, Goals with the real date window, and one row in Active Projects for each thing mentioned in point 2. Then **show the user what you wrote**: it is the first visible proof that the system exists, not a process detail.

### 5. Explain what changed, without waiting to be asked
Three lines, not a manual. Where the material for their work goes (`10_projects/`), where they dump raw notes when they have no time to sort them (`01_raw/`), and the point that matters: they do not have to organise anything by hand, the assistant keeps the state up to date as they tell it what happens.

This step is not optional: at this point the user has answered three questions and seen a filled-in file, but still does not know what they get out of it. If you leave them to ask, you have already lost them.

### 6. Open the first project
If the user mentioned at least one project, run `project-kickoff-procedure.md` for it. If they mentioned more than one, ask which to start with instead of deciding yourself.

### 7. Install the skills
The procedures in `03_skills/` only trigger by themselves once they have been registered as skills. **Try installing them yourself**, if the tool to do so is available in this environment — check first which ones are already present, so you do not duplicate them:

- `librarian-procedure.md` — turns the raw material in `01_raw/` into linked notes in the wiki.
- `project-kickoff-procedure.md` — opens the next projects.
- `knowledge-pill-procedure.md` — distils a recurring competence into a file you can call up.
- `system-check-procedure.md` — checks that the system has not broken.
- `session-log-procedure.md` — closes a session by recording what came up.
- `system-feedback-procedure.md` — records problems with the system itself.

If you cannot install them from here, say so clearly and explain how: assistant settings, Skills section, upload these files one at a time. Once only.

The procedures remain readable, editable files: whoever changes one updates the active copy by reloading it.

### 8. Provoke the proof
Close by telling the user to end this conversation, open a new one on the same folder and ask "where were we". It is the only demonstration that counts: in a new session, with no context, the assistant already knows who they are and what they are working on.

---

## Things to Know
- This procedure runs once per installation: Step 1 is the guard that guarantees it.
- The notes and documents the user already has elsewhere are not imported in this pass: they go into `01_raw/` and get digested with the Librarian, whenever they want. Mention it at Step 8 as a possible next thing.
- Dry register: the user has just downloaded some files and does not yet know whether to trust them. The questions exist to fill in `memory.md`, not to make conversation.

## History Log
- [2026-07-26] Procedure created.
- [2026-07-26] Added Step 5 ("explain what changed"): in the first real test the user had to ask on their own what the system was for, after completing the interview. Step 7 rewritten: skills are installed directly when the environment allows it, instead of handing the user a manual step.
