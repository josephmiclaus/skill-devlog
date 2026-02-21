# AGENTS.md Template (merge into your project root)

This file is a template. Copy or merge this section into your project's existing `AGENTS.md`. Do not overwrite existing project rules.

## Devlog auto-logging
- If the agent performs meaningful work (code edits, decisions, bug fixes, tests, docs), it MUST APPEND an entry to today's devlog using `skill-devlog`.
- Record agent work under **AI-assisted**.
- Include a short bullet: `Prompt: "<short summary of the user prompt>"`.

## Do not log
- Trivial formatting-only changes.

## Security
- Never include secrets in devlog content.
