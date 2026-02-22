# skill-devlog

Reusable skill package for maintaining a structured development log in `docs/devlog.md`.

## What it does
- Creates a dated entry under `<!-- DEVLOG_ANCHOR -->` when missing.
- Updates an existing same-day entry instead of duplicating it.
- Supports APPEND and CHANGE update flows.
- Keeps edits scoped to `docs/devlog.md` only.

## Install

```bash
npx skills add josephmiclaus/skill-devlog --skill skill-devlog
```

## Setup

### Option A: run the skill once
Run `skill-devlog` once. If `docs/devlog.md` is missing, it creates the file.

### Option B: copy the template manually
Copy `skills/skill-devlog/references/devlog.template.md` to `docs/devlog.md`.

### Passive auto-logging
Merge the snippet at `skills/skill-devlog/references/agents.snippet.md` into your project's `AGENTS.md` (do not overwrite existing project rules).

If your project does not have `AGENTS.md`, create one and paste the snippet content.

For full post-install guidance, see `skills/skill-devlog/references/setup.md`.

## Installer UX messaging (recommended)

After install, show:
- `skill-devlog installed.`
- `To enable passive auto-logging, merge <installed-skill-path>/references/agents.snippet.md into your project AGENTS.md.`
- `No AGENTS.md found? Create one and paste the snippet.`
- `This step is optional; core devlog entry creation/update works without it.`

Example installed path:
- Codex skill folder: `$CODEX_HOME/skills/skill-devlog/references/agents.snippet.md`

## Files the skill is allowed to edit

`docs/devlog.md` ONLY

## Optional attribution marker

If `docs/devlog.md` contains `<!-- SKILL_DEVLOG_ATTRIBUTION=on -->`, the skill may add a **Credits** section to entries.

## License

MIT
