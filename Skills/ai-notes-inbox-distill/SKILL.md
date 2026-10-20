---
name: ai-notes-inbox-distill
description: Distill one or more AI conversation source notes into reviewable Obsidian candidates for personal ideas, plans, tasks, questions, decisions, and references. Use when the user asks to organize, extract, review, or synthesize conversations in Echoes.
---

# AI Notes Inbox Distill

Turn source conversations into concise, traceable candidates for human review.

## Workflow

1. Locate the Echoes project root: a directory named `Echoes` containing `README.md` and `Inbox/`, or the current workspace root if it contains both. If it cannot be accessed, ask for its path; never assume a location.
2. Determine the source scope from the user's request. If unspecified, list Inbox sources and ask which to process when there are several; do not process the entire vault implicitly.
3. Read source notes and inspect likely related notes using filenames, frontmatter, tags, and Obsidian links. Read only relevant notes.
4. Extract zero or more candidates in these types: `idea`, `plan`, `task`, `question`, `decision`, `reference`.
5. For every candidate, label attribution:
   - `user`: explicitly stated by the user.
   - `assistant`: proposed by an AI; not evidence of user belief or commitment.
   - `shared`: explicitly agreed in the conversation.
   - `uncertain`: attribution or intent cannot be established.
6. Keep each candidate faithful and concise. Include a short supporting quote or message reference. Preserve uncertainty and disagreement. Do not convert an AI suggestion into a user plan or task unless the user explicitly accepts it.
7. Identify possible duplicates and related notes. Recommend `new`, `append`, `task`, `reference`, or `skip`, with a brief reason. Never edit/merge existing notes during analysis.
8. Create a review draft in `<Echoes root>/Inbox/Review/` using `Templates/review-candidates.md` (or its structure). Link each source with an Obsidian link and include source URLs when present. Keep status `needs-review`.
9. Show the draft contents or a clear summary and ask the user to confirm which items to file. Do not write candidates into final folders until the user explicitly confirms.

## On confirmation

- Create only the approved items in `<Echoes root>/Ideas/`, `Plans/`, `Tasks/`, `Questions/`, `Decisions/`, or `References/`.
- Re-check the proposed target for duplicates immediately before writing.
- If appending to an existing note, show the exact proposed addition and get confirmation first.
- Link each saved item to its source conversation. Preserve the original source note unchanged.
- Mark the review draft and source status as processed only after successful writes; do not delete either.
- Report files created or updated, skipped candidates, and any unresolved ambiguity.

## Output format

For each candidate include:

```text
### [type] Title
- Attribution: user | assistant | shared | uncertain
- Candidate: faithful short formulation
- Evidence: short quote or message locator
- Suggested destination: path or Obsidian link
- Similar existing notes: links or none found
- Recommendation: new | append | task | reference | skip
- Confidence: high | medium | low
```

Use the user's language. Keep raw source separate from synthesis. Never invent dates, deadlines, commitments, or citations.
