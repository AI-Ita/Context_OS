# skills — index

> The system's procedures: `.md` files that get read and executed. Each carries a YAML block at the top with a name and a description, so it can be uploaded directly as a skill from the assistant's settings and trigger itself on command.
> The cascade towards everything under `03_skills/` starts here.

## Procedures

- **[onboarding-procedure.md](onboarding-procedure.md)** — first run: leads 3+1 questions, fills in `memory.md`, opens the first project. It is triggered by the first-run rule in `CLAUDE.md` while the system is still empty: the only one that is not loaded as a skill.
- **[librarian-procedure.md](librarian-procedure.md)** — sorts `01_raw/` between knowledge and projects: atomic notes in the wiki, folders and state in `10_projects/`, indexes updated, originals archived in `_processed/` and contradictions flagged instead of overwritten.
- **[project-kickoff-procedure.md](project-kickoff-procedure.md)** — opens a new project: folder, `CLAUDE.md`, `memory.md`, row in the active projects table and entry in the index.
- **[knowledge-pill-procedure.md](knowledge-pill-procedure.md)** — distils a recurring competence into an operational file to call up, saved in `00_context/knowledge_pills/`.
- **[system-check-procedure.md](system-check-procedure.md)** — mechanical checks on the system: broken links, orphan files, stale paths, naming, date discrepancies.
- **[session-log-procedure.md](session-log-procedure.md)** — closes a block of work by writing a dated entry in the self-improvement log.
- **[system-feedback-procedure.md](system-feedback-procedure.md)** — writes straight into `99_system/system-feedback.md` when a problem with the structure of the system shows up.

---
*Editing a procedure updates the active copy by reloading it from the settings: the file stays the single source, the skill is only its trigger channel.*
