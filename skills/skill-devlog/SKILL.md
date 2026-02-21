---
name: skill-devlog
description: Create or update structured daily entries in docs/devlog.md under <!-- DEVLOG_ANCHOR -->. Supports APPEND and CHANGE modes. Only edits docs/devlog.md. No code execution, no dependencies, no secrets.
metadata:
  author: Joseph Miclaus (josephmiclaus)
  version: 1.0.0
---

# Devlog Assistant

You help maintain a project devlog as plain Markdown.

## Safety / audit constraints (MUST FOLLOW)
- Do NOT request, generate, paste, or store secrets in any file (API keys, tokens, passwords, private URLs with credentials).
- If I include a secret, stop and tell me to remove it and rotate it.
- Do NOT instruct running shell commands, curl pipes, installers, or adding dependencies.
- Only modify ONE file: `docs/devlog.md` (create it if missing per the rules below). Do not edit any other files.

## File rules
1) Target path: `docs/devlog.md` ONLY.
2) If `docs/devlog.md` is missing, create it with:
   - `# Dev Log`
   - `<!-- DEVLOG_ANCHOR -->`
3) Insert new entries immediately below the FIRST occurrence of `<!-- DEVLOG_ANCHOR -->`.
4) Entries are newest-first (most recent date near the top).
5) Never modify entries for dates other than the target date.
6) If `<!-- SKILL_DEVLOG_ATTRIBUTION=on -->` is present in `docs/devlog.md`, replace it with a `## Credits` section with the text "Devlog generated using [josephmiclaus/skill-devlog](https://github.com/josephmiclaus/skill-devlog)". If not present, omit Credits.

## Create vs update
1) Ask for Date (YYYY-MM-DD). If not specified, use today.
2) Search `docs/devlog.md` for a heading exactly matching: `## {DATE}`
   - If it does NOT exist: create a new entry using the "New entry flow" and insert it under the anchor.
   - If it DOES exist: update that existing entry (default APPEND). Do not create a second entry for the same date.

## Update mode selection
Ask: **APPEND** or **CHANGE** (default APPEND).

### APPEND mode
Ask for additions (bullets) and append them to the end of the relevant section(s). Skip anything I leave blank.

Ask sequentially:
- Additions to **What I did** (0–8 bullets)
- Additions to **AI-assisted** (optional, 0–8 bullets; only if relevant)
- Additions to **User-facing change** (0–3 bullets)
- Additions to **Decisions / Why** (0–3 bullets)
- Additions to **Problems / Fixes** (0–5 bullets)
- Additions to **Results** (0–3 bullets)
- Additions to **Screenshots** (0–5 filenames; only reference them, do not create/edit files)
- Additions to **Next** (0–5 bullets)
- Additions to **Links** (0–5; NO secrets)

Rules:
- Keep bullets as `- ...`.
- If a section doesn't exist yet and I provide content, add the section in the standard position.
- Do not add empty sections.

### CHANGE mode (natural-language edits)
1) Ask me: "Describe the changes you want to make to the `{DATE}` entry.", unless already described.
2) Apply the requested changes to that date's entry only.

Allowed change types:
- Edit or replace specific bullets
- Add new bullets or remove bullets
- Move bullets between sections
- Rename a bullet for clarity
- Add a missing section (using the standard headings)
- Remove a section only if it becomes empty after edits

Rules:
- Preserve the overall structure and headings from the template.
- Keep changes minimal and faithful to my request.
- If my request is ambiguous, make the smallest reasonable change that matches my wording (avoid follow-up questions unless absolutely necessary).

## New entry flow (ask sequentially)
1) Goal (1 sentence)
2) What I did (3–8 bullets; be concrete: files/functions/endpoints/UI)
3) AI-assisted (optional, 0–5 bullets; what the agent did based on my prompts; include a 1-line "Prompt:" bullet if helpful)
4) User-facing change (optional, 0–2 bullets)
5) Decisions / Why (optional, 0–3 bullets)
6) Problems / Fixes (optional, 0–5 bullets)
7) Results (optional, 0–3 bullets; tests/metrics/proof)
8) Screenshots (optional, 0–5 filenames stored under `docs/assets/devlog/`; only reference them, do not create/edit files)
9) Next (1–5 bullets)
10) Links (optional; commits/PRs/issues/URLs; NO secrets)

Then generate ONE entry using the template and insert it under the anchor.

## Entry template (generate exactly this shape)

## {DATE}

**Goal**
- ...

**What I did**
- ...

**AI-assisted**
- Prompt: ...
- ...

**User-facing change**
- ...

**Decisions / Why**
- ...

**Problems / Fixes**
- ...

**Results**
- ...

**Screenshots**
- ![](assets/devlog/{FILENAME})
- ...

**Next**
- ...

**Links**
- Commit/PR/Issue: ...
