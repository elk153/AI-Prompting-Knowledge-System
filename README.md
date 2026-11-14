# AI Prompting Knowledge System

**Version:** 1.2  
**Updated:** 2026-11-14  
**Status:** D001 lesson generated and reviewed; learner completion pending.

## Purpose

A structured, evidence-informed programme to develop advanced capability in prompting, AI tool selection, workflow design, evaluation and agentic work.

## Canonical source of truth

The GitHub repository is the authoritative location for programme documents, lesson artifacts, decisions, references and prompt-assessment history:

**Repository:** https://github.com/elk153/AI-Prompting-Knowledge-System

Use Git commits as the durable change history. ChatGPT Project uploads and local copies are convenience copies only; they are not authoritative and do not synchronise automatically with GitHub.

## File map

| File | Purpose |
|---|---|
| `PROJECT_INSTRUCTIONS.md` | Operating instructions to copy into the ChatGPT Project Instructions field |
| `ROADMAP.md` | Curriculum organised by chapters and proficiency levels |
| `DECISIONS.md` | Ordered backlog; executing a decision generates one lesson |
| `PROMPT_SCORECARD_AND_LOG.md` | Prompt review rubric and longitudinal effectiveness record |
| `LESSON_TEMPLATE.md` | Standard contract for every generated lesson |
| `REFERENCES.md` | Recognised primary references and evidence principles |
| `L###-short-title.md` | Individual lesson artifacts created as decisions are executed |
| `L001-mental-models-of-llms.md` | D001 lesson: practical mental model of LLMs, capabilities and limitations |

## Recommended setup

1. Open the repository and confirm that you have the intended access level: https://github.com/elk153/AI-Prompting-Knowledge-System
2. Copy the complete contents of `PROJECT_INSTRUCTIONS.md` into the ChatGPT Project's **Instructions** field (Project menu → Edit project / Project settings).
3. Connect or enable the GitHub integration in ChatGPT, with access to this repository. The assistant must read the current repository files before relying on programme state and use GitHub writes for updates.
4. You may upload selected Markdown files to the ChatGPT Project as convenience context, but they are snapshots. They can become stale; GitHub remains authoritative.
5. Keep any local clone in sync with the intended branch using normal Git operations. Review diffs before pushing changes.
6. Start with decision `D001`. Ask the assistant to execute it using the decision workflow below.

## GitHub operating rules

- Read the current version of relevant files from GitHub before editing or making decisions based on them.
- Use the current default branch unless another ref is explicitly requested.
- Fetch the latest file and its blob SHA before updating it; avoid stale overwrites.
- Create new lesson files without replacing existing files. Preserve IDs and append to logs.
- Use descriptive commit messages. For multi-file changes, prefer a branch and pull request when supported.
- Verify writes and report changed paths, commit and file links.
- Never commit secrets, credentials or confidential prompt content without explicit approval. Prefer redacted assessment records.
- If GitHub access or write permissions are unavailable, provide a proposed patch or downloadable draft and clearly state that it has not been committed.

## Operating workflow

### Generate a lesson

Use this command in the project:

> Execute decision D###. Read the current roadmap, decisions, lesson template and references from the GitHub repository. Check prerequisites. Generate exactly one standalone Markdown lesson in the repository, update the relevant decision/progress records, preserve history, commit and verify all changes. Do not execute later decisions. Include objectives, prerequisites, references, practical exercises, expected deliverables, evaluation grid and completion criteria. Return the GitHub file and commit links.

### Review a prompt

Paste the prompt and, if available, the resulting AI output. Ask:

> Review this prompt using the current repository scorecard. Separate prompt quality from model/tool limitations and execution quality. Give evidence-based scores, identify the three highest-impact improvements, and propose a revised prompt. If appropriate, append a new assessment entry to the repository log, update the dashboard based on evidence, commit and verify the changes. Do not record confidential content verbatim without my approval and do not claim improvement unless a comparable test supports it.

### Update the programme

Use:

> Update the roadmap, decision backlog and progress log in the GitHub repository based on the completed work. Read current files first, preserve IDs and history, avoid stale overwrites, commit the changes and provide the commit and file links. Do not silently delete or renumber records. Add a dated change note.

## Decision lifecycle

`PROPOSED → READY → IN_PROGRESS → GENERATED → REVIEWED → COMPLETED`

A decision is not complete merely because a lesson draft exists. Review it against the lesson template, check links and exercises, and record the result in the repository.

## Lesson quality gate

A lesson must contain:
- A measurable learning objective and observable success criteria.
- A concise explanation of why the skill matters and when to use it.
- Reading references, with source type, author/organisation, title, URL and access date where applicable.
- Exercises using realistic work tasks, including at least one deliberately imperfect prompt.
- A worked example or answer key where appropriate.
- A scoring grid with behavioural anchors, not vague labels.
- A transfer task that applies the skill to a different model or tool.
- Limitations, failure modes, safety/privacy considerations and tool-selection guidance.
- A short reflection and a recordable assessment result.

## Current progress

- **D001 — GENERATED:** [L001: A Practical Mental Model of Large Language Models](L001-mental-models-of-llms.md) has been created and reviewed against the lesson quality gate. Exercises and learner assessment remain pending; D002 has not been executed.

## Measurement principles

- Compare like with like: same task, inputs, model/tool settings where possible.
- Separate prompt quality, model capability, context quality, tool availability and execution quality.
- Score output against task-specific criteria, not whether the answer merely sounds convincing.
- Preserve original prompts and outputs for meaningful comparisons, subject to privacy approval and data minimisation.
- Treat scores as diagnostic evidence, not objective universal measures.
