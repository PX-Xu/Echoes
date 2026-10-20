---
name: ai-notes-inbox-organize
description: Review and organize the raw AI conversation archive in Echoes. Build or refresh a source index, group conversations by topic, identify unprocessed or overlapping sources, and report suggested next steps without changing original transcripts.
---

# AI Notes Inbox Organize

Organize the archive of raw AI conversations so sources are findable and ready for later distillation.

## Scope and safety

- Work only in `<Echoes root>/Inbox/Raw/`, its `Index.md`, and `<Echoes root>/Inbox/Processed/` reports unless the user explicitly expands scope.
- Preserve raw transcript files byte-for-byte. Never rewrite, rename, move, merge, or delete a source transcript.
- Do not create final knowledge notes or classify AI suggestions as the user's beliefs. Use `ai-notes-inbox-distill` for extracting knowledge candidates.
- Do not send conversation contents to external services. Use only information available in the local files.

## Workflow

1. Locate the Echoes project root: a directory named `Echoes` containing `README.md` and `Inbox/`, or the current workspace root if it contains both. If it cannot be found, ask for the path; do not guess.
2. Inventory Markdown files in `Inbox/Raw/`. Read frontmatter and headings first; inspect transcript bodies only as needed to identify topics and status.
3. For each source, record title, platform, captured date, source URL when available, relative file link, topic labels, and processing state. Missing metadata must be `unknown`; never infer platform or dates from content unless clearly explicit.
4. Group sources under a small set of clear topic headings. Prefer existing topic names in the vault when they fit; do not create or move topic folders.
5. Detect exact duplicates by file content/hash if available. Flag likely overlapping conversations based on title and topic; do not call them duplicates unless content confirms it.
6. Determine processing state from explicit frontmatter or matching distillation review notes:
   - `unprocessed`: no review draft or processed marker found.
   - `in-review`: a linked review draft exists with `needs-review` status.
   - `processed`: the source explicitly records completed distillation.
   - `unknown`: state cannot be established.
7. Prepare an index update and a concise report with counts, topic groups, unprocessed sources, review items, likely overlaps, and suggested next actions.
8. Show the proposed changes to `Inbox/Index.md` and any report file before writing. Ask for confirmation before creating or replacing the index/report. If an existing index contains user-authored material, preserve it and propose additions only.
9. After confirmation, write or update the index/report without altering source transcripts. Use `<Echoes root>/Inbox/Processed/` for dated organization reports.
10. Report changed files and unresolved metadata. If no sources exist, create nothing and explain that the inbox is empty.

## Index format

Use plain Markdown with sections:

- Summary and last reviewed date
- By topic: source links with platform, date, and processing state
- Needs processing
- In review
- Processed
- Possible overlaps (explicitly labeled as candidates, not confirmed duplicates)

Keep the index compact. Link to the original raw files using Obsidian wikilinks where filenames allow, and include source URLs when present.

## Relationship to other skills

- `ai-notes-inbox-capture` saves a new source transcript.
- `ai-notes-inbox-organize` indexes and reviews the raw-source collection.
- `ai-notes-inbox-distill` extracts knowledge candidates from selected source conversations and files approved items after confirmation.
