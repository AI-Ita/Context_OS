# First Run — Procedure

*v1.1*

Sets up a freshly installed system: leads a short conversation, fills in `memory.md`, opens the first project, puts the user in a position to work.

**Goal of the procedure:** take the user from "a folder of empty files" to "a system that knows who I am, what I am working on and what I actually need" in a few minutes, without them having to read documentation and without them having to understand how it is built inside.

**When it triggers:** at the start of a session, when `memory.md` is still not filled in (see Step 1). The trigger is the first-run rule in `CLAUDE.md`, not a user command.

**Prerequisites:**
- The system folder connected to the session.

## How to be in this conversation

This applies across every step below, before the steps themselves.

**You lead.** The user has just downloaded some files, does not know what to expect and does not yet know whether to trust this: they are in no position to steer, and if you hand them the wheel they stall. Ask one thing at a time, already knowing where you are going, and carry the conversation to the next step yourself. Do not ask permission to proceed ("would you like me to ask you a few questions?") — proceed.

**Make yourself understood.** In this conversation there are no folder names, file names, "indexes", "propagation", "router". There are: their stuff, their projects, what they need. Technical vocabulary is offered, not imposed (see Step 6).

**Actually listen.** If an answer opens something more interesting than your next question, follow it for a turn before steering back. A well-completed questionnaire is still a questionnaire: what has to stay with the user is the feeling of having been understood.

**Never re-run this procedure on someone who has already done it.** See Step 1: that is the guard, and it is not skipped.

## Steps

### 1. Check that it is actually needed
Read `memory.md`. If the "Identity" section still contains the placeholder text in square brackets, the system is new: carry on.

If it is already filled in, onboarding has already been done: **do not run this procedure and do not mention it**. Answer the user's request normally. Re-running onboarding on someone whose system is in use is the worst error this procedure can produce: it means having lost the state of someone who trusted you.

### 2. Open, without asking permission
Two lines: what you are about to do, how long it takes, what they get out of it. Then go straight into the first question, in the same message.

Do not list the questions in advance and do not announce the structure of the conversation: the user must not brace for a form to fill in.

### 3. The three questions, one per message
Never all at once. Each one fills a specific part of `memory.md`, but that is your business, not theirs: never tell the user which box they are filling.

1. **"Who are you and what do you do?"** — one line, not a CV. → Identity section.
2. **"What are you working on right now? One to three things."** → Active Projects table.
3. **"What do you expect from me? And what is your sore spot today — in staying organised, or in the way you use AI?"** → Goals section, once you have translated it (see below).

The third is the most important of the three and should be treated as such: do not dispatch it with a "got it". The answer almost always arrives as a complaint ("I lose time", "I forget things", "every time I start from scratch"), and your job is to **hand it back to them translated into a concrete goal**, asking for confirmation:

> *"So the real problem isn't taking notes, it's that every conversation restarts from zero. The goal becomes: never explain your context again. Does that land?"*

This is where the user finds out whether they are dealing with something that understood their problem or a questionnaire in disguise. If the answer is vague, ask for a concrete example of a time it happened, instead of moving on.

If the user skips a question, leave the matching section empty and move on: it fills in later.

### 4. The open question
One only, after the three:

> **"Last one, and the most open: tell me everything an assistant should know about you to help you properly. How you work, what wastes your time, what you can't stand, how you want me to talk to you. Messy is fine — sorting it out is my job."**

It exists to collect what the three structured questions cannot anticipate: preferences, constraints, ways of working, personal context. It has no length limit and must not be interrupted.

What comes back is sorted like this: what is operational and changes over time goes into `memory.md`; what describes *how the user is made* — stable preferences, ways of working, things never to do — becomes a note in `00_context/`, which is where it will be re-read from in every future session. If the answer is rich, say so explicitly: what they have just written once, they will never have to write again.

### 5. Fill in `memory.md`
Check the date with a command, never infer it. Write Identity, Goals with the real date window, and one row in Active Projects for each thing mentioned in question 2. Then **show the user what you wrote**: it is the first visible proof that the system exists, not a process detail.

Filling it in removes the placeholder text — and that, and only that, is what stops this procedure from starting again in future (see Step 1).

### 6. Explain what changed, without waiting to be asked
Three lines, in plain language, naming neither folders nor files: from now on what they tell you stays; they do not have to organise anything by hand; when they open a new conversation the system already knows where you both left off.

Then, in a single line, offer the technical level instead of imposing it:

> *"If you want to know where things physically end up and how it's built inside, I'll explain in two minutes. Otherwise it works just the same and you don't need to know."*

If they say yes, then — and only then — name the folders and what each one does. If they say no, do not return to it.

This step is not optional: at this point the user has answered four questions and seen a filled-in file, but still does not know what they get out of it. If you leave them to ask, you have already lost them.

### 7. Open the first project
If the user mentioned at least one project, run `project-kickoff/SKILL.md` for it. If they mentioned more than one, ask which to start with instead of deciding yourself.

### 8. The skills: already set up, or install by hand
If you're on Claude Code, the six skills are already active: `.claude/skills/` ships a ready-to-use copy, nothing to do. If you're not sure whether you're on Claude Code, check with the skill discovery mechanism instead of guessing.

If you're not on Claude Code (claude.ai, app), say so clearly and offer to install them: open the `SKILL.md` file inside each of the six folders in `03_skills/` (all but this one), copy its contents, and paste it into Settings → Skills → "Write skill instructions". Once only, one skill at a time:

- `librarian/` — takes the raw material the user dumps in and turns it into ordered knowledge and projects.
- `project-kickoff/` — opens the next projects.
- `knowledge-pill/` — distils a recurring competence into a file you can call up.
- `system-check/` — checks that the system has not broken.
- `session-log/` — closes a session by recording what came up.
- `system-feedback/` — records problems with the system itself.

The procedures remain readable and editable in `03_skills/`, which is the source: on Claude Code, whoever changes one has to re-copy it into `.claude/skills/` too (it is not linked automatically); on claude.ai/app, reload it from settings.

The procedures remain readable, editable files: whoever changes one updates the active copy by reloading it.

### 9. Provoke the proof
Close by telling the user to end this conversation, open a new one on the same folder and ask "where were we". It is the only demonstration that counts: in a new session, with no context, the assistant already knows who they are and what they are working on.

If they have material of their own somewhere else — notes, documents, saved threads — this is the moment to tell them they can dump it in as it is, without sorting it: the Librarian will split it between knowledge and projects.

---

## Things to Know
- This procedure runs once per installation: Step 1 is the guard that guarantees it, and Step 5 is what makes it final.
- The notes and documents the user already has elsewhere are not imported in this pass: they go into `01_raw/` and get digested with the Librarian, whenever they want. Mention it at Step 9 as a possible next thing.
- Dry register but not cold: the questions exist to understand the user, not to make conversation — and not to fill boxes either.

## History Log
- [2026-07-26] Procedure created.
- [2026-07-26] Added Step 5 ("explain what changed"): in the first real test the user had to ask on their own what the system was for, after completing the interview. Step 7 rewritten: skills are installed directly when the environment allows it, instead of handing the user a manual step.
- [2026-08-04] Rewritten after the first live demo. Added the "How to be in this conversation" section: the system was leading too little and filling in too much. Third question replaced (it was "what do you want to achieve in the next two weeks", too generic) with expectations + sore spot, plus the obligation to hand the problem back translated into a goal. Added the closing open question (Step 4). Step 6: folder and file names are no longer named by default, they are offered. Step 1 hardened on the ban against re-running onboarding for someone who has already done it.
