# skills — index

> The system's procedures: one folder per skill, `<name>/SKILL.md` with a YAML block at the top (name and description). This is the readable, editable source. Claude Code does not scan `03_skills/`: it discovers skills from `.claude/skills/`, which in this package already ships a ready copy of the same six folders (cold-tested on 07/08) — so on Claude Code they work with no user action. On claude.ai/app, which doesn't read `.claude/`, install them by copying each `SKILL.md`'s content into a new skill from settings.
> The cascade towards everything under `03_skills/` starts here.

## Procedures

- **[onboarding/SKILL.md](onboarding/SKILL.md)** — first run: leads 3+1 questions, fills in `memory.md`, opens the first project. It is triggered by the first-run rule in `CLAUDE.md` while the system is still empty: the only one that is not installed as a separate skill.
- **[librarian/SKILL.md](librarian/SKILL.md)** — sorts `01_raw/` between knowledge and projects: atomic notes in the wiki, folders and state in `10_projects/`, indexes updated, originals archived in `_processed/` and contradictions flagged instead of overwritten.
- **[project-kickoff/SKILL.md](project-kickoff/SKILL.md)** — opens a new project: folder, `CLAUDE.md`, `memory.md`, row in the active projects table and entry in the index.
- **[knowledge-pill/SKILL.md](knowledge-pill/SKILL.md)** — distils a recurring competence into an operational file to call up, saved in `00_context/knowledge_pills/`.
- **[system-check/SKILL.md](system-check/SKILL.md)** — mechanical checks on the system: broken links, orphan files, stale paths, naming, date discrepancies.
- **[session-log/SKILL.md](session-log/SKILL.md)** — closes a block of work by writing a dated entry in the self-improvement log.
- **[system-feedback/SKILL.md](system-feedback/SKILL.md)** — writes straight into `99_system/system-feedback.md` when a problem with the structure of the system shows up.

---
*Editing a procedure means editing it here, in `03_skills/<name>/SKILL.md`: it's the single source. To reach Claude Code it also needs re-copying onto its twin folder in `.claude/skills/<name>/` (not an automatic link); for claude.ai/app, reload it from settings.*
