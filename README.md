# skill-devlog

Reusable skill package for maintaining a structured development log in `docs/devlog.md`.

## What it does
- Creates a dated entry under `<!-- DEVLOG_ANCHOR -->` when missing.
- Updates an existing same-day entry instead of duplicating it.
- Supports APPEND and CHANGE update flows.
- Keeps edits scoped to `docs/devlog.md` only.

## Install

```bash
npx skills add <owner>/skill-devlog --skill skill-devlog
```

## Setup

### Option A: run the skill once
Run `skill-devlog` once. If `docs/devlog.md` is missing, it creates the file.

### Option B: copy the template manually
Copy `skills/skill-devlog/references/devlog.template.md` to `docs/devlog.md`.

### Passive auto-logging
Merge the **Devlog auto-logging** section from this repo's `AGENTS.md` into the project's existing `AGENTS.md` (do not overwrite).

## Files the skill is allowed to edit

`docs/devlog.md` ONLY

## Optional attribution marker

If `docs/devlog.md` contains `<!-- SKILL_DEVLOG_ATTRIBUTION=on -->`, the skill may add a **Credits** section to entries.

## License

MIT
