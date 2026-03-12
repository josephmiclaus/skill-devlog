# skill-devlog

Reusable skill package for maintaining a structured development log in `docs/devlog.md`.

## What it does
- Creates a dated entry under `<!-- DEVLOG_ANCHOR -->` when missing.
- Supports APPEND and CHANGE update flows.
- Updates an existing same-day entry.
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

The passive policy is eligibility-based:
- Auto-log code/docs/config edits, debugging tied to those edits, tests validating those edits, explicit devlog updates, and user-requested durable workspace artifacts.
- Do not auto-log read-only inspection, summarization, search-only work, Q&A, planning, status checks, or reviews with no file changes.
- If a case is ambiguous, ask before updating the devlog.

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

## Required header markers

`docs/devlog.md` should keep this exact header order:

```md
# Dev Log
<!-- SKILL_DEVLOG_ATTRIBUTION=... -->
<!-- Rule: Never paste secrets (API keys/tokens/passwords) into this file. -->
<!-- DEVLOG_ANCHOR -->
```

The skill should preserve these comments in this order and restore them if they are missing or moved.
The skill should preserve the existing `SKILL_DEVLOG_ATTRIBUTION` value exactly as written and should only change that value if the user explicitly asks for it.

## License

MIT
