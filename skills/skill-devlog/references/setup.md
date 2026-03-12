# skill-devlog setup

Use this file after installing `skill-devlog` from a skill installer.

## 1) Enable core devlog behavior

Choose one:
- Run `skill-devlog` once. If `docs/devlog.md` is missing, it will be created.
- Or copy `references/devlog.template.md` to `docs/devlog.md`.
- The devlog should keep the template header comments in the same order as the template; the skill restores them if they are missing or moved.

## 2) Enable passive auto-logging policy (optional but recommended)

Merge `references/agents.snippet.md` into your project `AGENTS.md`.
- Do not overwrite existing project rules.
- If `AGENTS.md` does not exist, create it and paste the snippet.
- The snippet only auto-logs eligible work. Read-only inspection, Q&A, planning, and similar non-mutating tasks are excluded by default.
- Ambiguous investigative work should ask before updating the devlog.

## 3) Recommended installer success message

- `skill-devlog installed.`
- `To enable passive auto-logging, merge <installed-skill-path>/references/agents.snippet.md into your project AGENTS.md.`
- `No AGENTS.md found? Create one and paste the snippet.`
- `This step is optional; core devlog entry creation/update works without it.`
