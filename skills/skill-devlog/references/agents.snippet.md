## Devlog auto-logging
- Auto-log only eligible work: code/docs/config edits, debugging tied to those edits, tests validating those edits, explicit devlog-maintenance requests, or user-requested durable workspace artifacts.
- Record eligible agent work under **AI-assisted**.
- Include a short bullet: `Prompt: "<short summary of the user prompt>"` when it helps explain the logged work.

## Do not log
- Read-only devlog inspection, including "what's next?" or task/status queries.
- Summarization, search-only work, Q&A, planning, or reviews/findings with no file changes.
- Any task where the agent only inspected existing state or answered in chat.
- Trivial formatting-only changes.

## Ask first if ambiguous
- If the task is investigative or advisory and may be worth documenting but did not clearly change project state, ask before updating the devlog.

## Security
- Never include secrets in devlog content.
