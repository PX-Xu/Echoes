---
name: ai-notes-inbox-capture
description: Capture useful ideas, plans, tasks, questions, decisions, or references from the current Codex conversation or imported AI chat files into the Echoes Obsidian inbox. Use when the user asks to save, capture, or collect conversation content for Obsidian.
---

# AI Notes Inbox Capture

Capture source material into the Echoes project's `Inbox/Raw/` folder.

## Instructions

1. Locate the Echoes project root. Prefer a directory named `Echoes` containing `README.md` and `Inbox/`; if the current workspace itself contains `README.md` and `Inbox/Raw/`, use the workspace root. Otherwise use a configured vault path and find its `Echoes/` folder. If no destination is accessible, ask for its path; do not guess.
2. For a Codex conversation, use only the current conversation context available to you. Do not claim to have read older Codex sessions that are not present in context. Include the user's wording and relevant assistant discussion; preserve speaker labels and conversational order.
3. For a browser-exported Markdown file, preserve its full content as source. Add metadata only when supported by its content or filename. Never silently discard messages, code, citations, or attachments references.
4. Create a collision-resistant filename: `YYYY-MM-DD - <short title> - <source>-<short id>.md`. Sanitize path separators and filesystem-reserved characters.
5. Write YAML frontmatter with `type: ai-conversation`, `status: inbox`, `platform`, `captured`, `source_url` if known, and `source_file` if imported. Use `unknown` for unavailable values.
6. Save the full source under `## 对话原文`. Add a short factual synopsis only if helpful, and label it `AI 提要（未核对）`.
7. Do not distill, classify as the user's endorsed position, move, overwrite, merge, or delete other notes in this capture step. If a same-name file exists, choose a new unique name.
8. Report the created note path and any metadata that could not be determined.

## Imported browser exports

Accept Markdown emitted by AI Chat Exporter or other exporters. Preserve original export metadata and formatting where possible. Do not fetch remote URLs or upload conversation contents.
