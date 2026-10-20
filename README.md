# Echoes

[简体中文](README.zh-CN.md)

> **Gather the scattered parts of yourself from AI conversations.**

Echoes is a local-first workflow for collecting and reviewing useful knowledge scattered across conversations with ChatGPT, DeepSeek, Codex, and other AI tools. It helps preserve and organize your ideas, plans, tasks, questions, decisions, and references in an Obsidian vault.

AI conversations can feel like `CHAOS`: valuable ideas sit beside repetition, unverified suggestions, and unresolved questions. Echoes gathers them into personal knowledge you can trace, search, and revisit.

![Echoes icon: scattered CHAOS flows into E and is organized as CHOES](echoes-icon.png)

## Getting Started

1. Clone or download this repository into your Obsidian vault and name the project folder `Echoes`.
2. Install the three Codex Skills described below.
3. Put browser chat exports in `Echoes/Inbox/Raw/`, or invoke the capture Skill in Codex.
4. Use the remaining Skills in order: organize sources, distill content, review and file.

Personal files in `Inbox/Raw/`, `Inbox/Review/`, and `Inbox/Processed/` are ignored by `.gitignore`. Review your Git changes before sharing or publishing to ensure private conversations are not included.

## Principles

- **Local first:** Plain Markdown files are the durable source of truth; Obsidian is the knowledge workspace.
- **Traceable sources:** Distilled notes link back to source conversations; transcripts stay separate from synthesized notes.
- **Clear attribution:** Distinguish the user's words, AI suggestions, shared conclusions, and uncertain items.
- **Review before filing:** AI proposes candidates and destinations; the user approves content before it enters the organized collection.
- **Gradual organization:** Capture first, then index and distill when useful.

## Workflow

1. **Web chats:** Install [AI Chat Exporter](https://github.com/Covai-Labs/ace), open a conversation in ChatGPT, DeepSeek, or another supported site, and export it as Markdown. Save or move the file into `Echoes/Inbox/Raw/` in your Obsidian vault. If the extension's Obsidian handoff creates the note elsewhere, move the original export into `Raw/`.
2. **Codex chats:** In Codex Desktop or VS Code, invoke `ai-notes-inbox-capture` to save the currently available conversation context into `Inbox/Raw/`. The Skill cannot read historical sessions that are not available in its context.
3. **Organize sources:** Invoke `ai-notes-inbox-organize`. It inventories raw chats and proposes a topic index and processing report; it asks for confirmation before creating or updating the index and never changes transcripts.
4. **Distill content:** Select one or more sources and invoke `ai-notes-inbox-distill`. It extracts ideas, plans, tasks, questions, decisions, and references, labels attribution, and creates a draft in `Inbox/Review/`.
5. **Review and file:** Review the draft in Codex and identify which items to keep or revise. The Skill writes approved items to their categories only after your explicit confirmation, with links back to the raw conversation.

## Codex Skills

This repository includes three Codex Skills. Install them in the user-level directory `~/.codex/skills/`. Codex Desktop and the VS Code Codex extension can share them when configured to use the same Codex home.

| Skill | Purpose |
| --- | --- |
| `ai-notes-inbox-capture` | Save the current Codex conversation or collect an imported AI chat Markdown file as a raw source. |
| `ai-notes-inbox-organize` | Index raw conversations by topic and report processing status without changing transcripts. |
| `ai-notes-inbox-distill` | Extract knowledge candidates from selected sources, check links and duplicates, and file approved items. |

### Installation

Copy the three Skill folders from `Skills/` into your Codex user Skills directory:

```bash
mkdir -p ~/.codex/skills
cp -R Skills/ai-notes-inbox-* ~/.codex/skills/
```

Restart or refresh Codex, then use the Skill picker or ask in natural language, for example:

- `Use ai-notes-inbox-capture to save this Codex conversation.`
- `Use ai-notes-inbox-organize to review the raw Echoes inbox conversations.`
- `Use ai-notes-inbox-distill to prepare a review draft from this chat.`

> Skills can use the current conversation context and local files you provide or make accessible. They do not claim to read Codex history that is not available in the current context.

## Importing Browser Conversations

Use [AI Chat Exporter](https://github.com/Covai-Labs/ace) to export browser conversations as Markdown, then save them in `Inbox/Raw/`. AI Chat Exporter is an independent project and is not bundled with Echoes; install and configure it separately using its official instructions.

Echoes Skills handle local collection and organization after export. They do not monitor browser pages or sync conversations in the background. Save the current Codex Desktop or VS Code conversation with `ai-notes-inbox-capture`.

## Folder Structure

```text
Echoes/
├── Inbox/
│   ├── Raw/          # Original conversation exports (private; not committed)
│   ├── Review/       # Distillation drafts awaiting review
│   └── Processed/    # Organization reports and processed-source records
├── Ideas/            # Approved ideas
├── Plans/            # Approved plans
├── Tasks/            # Approved tasks
├── Questions/        # Open questions
├── Decisions/        # Approved decisions
├── References/       # Reference leads
├── Skills/           # Installable Codex Skills
└── Templates/        # Markdown templates
```

## Attribution

Every distilled item should use one of these labels:

- `user`: explicitly expressed by the user.
- `assistant`: proposed by an AI; not evidence that the user agrees.
- `shared`: explicitly agreed in the conversation.
- `uncertain`: attribution or adoption cannot be established.

Do not turn an AI suggestion into the user's belief, decision, or task without explicit acceptance. Do not invent deadlines, commitments, or sources.

## Scope and Status

Echoes currently provides an Obsidian folder structure, Markdown templates, and Codex Skills. Browser extension installation, bulk historical imports, automatic background sync, automatic semantic deduplication, and cross-device services are outside the current version.

AI websites change their page structures, and local access to Codex conversations depends on the available context. Review exports and source links. Conversations may contain personal information; remove sensitive content before sharing publicly.

## License

Echoes is licensed under the [MIT License](LICENSE). AI Chat Exporter is an independent project, is not bundled with this repository, and is distributed under its own license.

## Acknowledgements

Thank you to [AI Chat Exporter](https://github.com/Covai-Labs/ace) for providing local export support across AI chat websites. Echoes recommends it as a browser-conversation capture option. AI Chat Exporter is independently maintained by Covai-Labs and follows its own license and release schedule.
