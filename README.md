# AI Prompting Knowledge System

**Version:** 1.0\
**Created:** 2026-11-14\
**Status:** Programme blueprint; lessons not yet generated.

## Purpose

A structured, evidence-informed programme to develop advanced capability
in prompting, AI tool selection, workflow design, evaluation and agentic
work.

## File map

  -----------------------------------------------------------------------
  File                                Purpose
  ----------------------------------- -----------------------------------
  `PROJECT_INSTRUCTIONS.md`           Operating instructions to paste
                                      into this ChatGPT Project's
                                      Instructions field

  `ROADMAP.md`                        Curriculum organised by chapters
                                      and proficiency levels

  `DECISIONS.md`                      Ordered backlog; executing a
                                      decision generates one lesson

  `PROMPT_SCORECARD_AND_LOG.md`       Prompt review rubric and
                                      longitudinal effectiveness record

  `LESSON_TEMPLATE.md`                Standard contract for every
                                      generated lesson

  `REFERENCES.md`                     Recognised primary references and
                                      evidence principles
  -----------------------------------------------------------------------

## Recommended setup

1.  Open the Project menu and choose **Edit project** / **Project
    settings**.
2.  Paste the contents of `PROJECT_INSTRUCTIONS.md` into the Project
    Instructions field.
3.  Upload the remaining Markdown files to the Project as knowledge
    files. Keep this README as the index.
4.  For durable history and collaboration, keep a local Git repository
    (or an approved document repository) as the source of truth. ChatGPT
    Project files are useful working context, but should not be treated
    as a full version-control system.
5.  Start with decision `D001`. Ask the assistant to execute it using
    the decision workflow below.

## Operating workflow

### Generate a lesson

Use this command in the project:

> Execute decision D###. Read the roadmap, decisions, lesson template
> and references. Generate the lesson as a standalone Markdown artifact.
> Do not execute later decisions. Include objectives, prerequisites,
> references, practical exercises, expected deliverables, evaluation
> grid and completion criteria. Then update the decision status and
> explain what changed.

### Review a prompt

Paste the prompt and, if available, the resulting AI output. Ask:

> Review this prompt using the project's scorecard. Separate prompt
> quality from model/tool limitations and execution quality. Give
> evidence-based scores, identify the three highest-impact improvements,
> and propose a revised prompt. Record the assessment in the prompt
> effectiveness log using a new entry. Do not claim an improvement
> unless a comparable test supports it.

### Update the programme

Use:

> Update the roadmap, decision backlog and progress log based on the
> completed work. Preserve IDs and history. Do not silently delete or
> renumber records. Add a dated change note.

## Decision lifecycle

`PROPOSED → READY → IN_PROGRESS → GENERATED → REVIEWED → COMPLETED`

A decision is not complete merely because a lesson draft exists. Review
it against the lesson template, check links and exercises, and record
the result.

## Lesson quality gate

A lesson must contain: - A measurable learning objective and observable
success criteria. - A concise explanation of why the skill matters and
when to use it. - Reading references, with source type,
author/organisation, title, URL and access date where applicable. -
Exercises using realistic work tasks, including at least one
deliberately imperfect prompt. - A worked example or answer key where
appropriate. - A scoring grid with behavioural anchors, not vague
labels. - A transfer task that applies the skill to a different model or
tool. - Limitations, failure modes, safety/privacy considerations and
tool-selection guidance. - A short reflection and a recordable
assessment result.

## Measurement principles

-   Compare like with like: same task, inputs, model/tool settings where
    possible.
-   Separate prompt quality, model capability, context quality, tool
    availability and execution quality.
-   Score output against task-specific criteria, not whether the answer
    merely sounds convincing.
-   Preserve original prompts and outputs for meaningful comparisons.
-   Treat scores as diagnostic evidence, not objective universal
    measures.
