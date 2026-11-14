# Curriculum Roadmap --- Advanced AI Prompting and Tool Fluency

**Version:** 1.0\
**Date:** 2026-11-14\
**Scope:** Roadmap only. Lesson content is intentionally not included.

## Programme architecture

The curriculum progresses through five proficiency levels. Each chapter
maps to one or more decisions in `DECISIONS.md`. Decisions are executed
one at a time to create lessons.

  -----------------------------------------------------------------------
  Level                   Capability target       Evidence of mastery
  ----------------------- ----------------------- -----------------------
  1 --- Foundation        Formulate clear tasks   Reliable prompts for
                          and evaluate basic      routine work
                          outputs                 

  2 --- Practitioner      Control context,        Repeatable workflows
                          structure, files, tools across common work
                          and iterative workflows types

  3 --- Advanced          Handle complex          Tested workflows with
                          reasoning tasks, code,  measurable quality
                          data, multimodal inputs 
                          and evaluation          

  4 --- Systems designer  Build multi-step,       Robust workflows with
                          retrieval-enabled and   controls and recovery
                          agentic workflows       

  5 --- Strategist        Govern, scale and       Portfolio-level
                          continuously improve AI standards, metrics and
                          use                     risk controls
  -----------------------------------------------------------------------

## Level 1 --- Foundations

### Chapter 1. Mental models of generative AI

-   What language models do and do not do.
-   Tokens, context windows, probabilistic generation and
    non-determinism.
-   Knowledge limits, hallucinations, uncertainty and calibration.
-   Model families and capability differences.
-   Prompting versus model selection, retrieval, tools and fine-tuning.

### Chapter 2. Anatomy of an effective prompt

-   Outcome-first task definition.
-   Context, audience, constraints and assumptions.
-   Instructions, examples and reference material.
-   Output formats and acceptance criteria.
-   Ambiguity management and clarification strategies.
-   Concision versus completeness; avoiding instruction overload.

### Chapter 3. Iteration and conversational control

-   Prompt iteration as hypothesis testing.
-   Decomposition, sequencing and progressive refinement.
-   Critique-and-revise loops.
-   Managing long conversations and context drift.
-   Asking for assumptions, evidence and concise rationales.
-   When to start a new conversation or reset context.

## Level 2 --- Practitioner

### Chapter 4. Context engineering and knowledge grounding

-   Selecting, preparing and prioritising context.
-   Grounding answers in supplied documents and trusted sources.
-   Retrieval-augmented generation (RAG) concepts.
-   Chunking, metadata, citations and source traceability.
-   Handling conflicting, missing or stale information.
-   Prompt injection and untrusted content boundaries.

### Chapter 5. Document analysis and exploitation

-   Summarisation for different audiences.
-   Extraction into structured fields and schemas.
-   Comparison, synthesis and cross-document reasoning.
-   Requirements, contracts, policies and technical-document analysis.
-   Traceability from claims to source passages.
-   Large-document workflows and staged analysis.

### Chapter 6. Document and knowledge production

-   Briefs, reports, specifications, procedures and presentations.
-   Audience, purpose, structure and acceptance criteria.
-   Drafting, critique, revision and editorial control.
-   Maintaining consistency across a document set.
-   Markdown, tables, structured data and reusable templates.
-   Fact checking, citations and document QA.

### Chapter 7. Choosing AI tools and operating modes

-   Chatbots, deep research, file analysis, code execution and agents.
-   Model capability, latency, cost, privacy and reliability trade-offs.
-   Search, connectors, plugins, APIs and local tools.
-   Tool selection by task, not brand preference.
-   Human-in-the-loop boundaries and permission models.
-   Tool capability verification and fallback planning.

## Level 3 --- Advanced

### Chapter 8. Data analysis and information management

-   Data profiling, cleaning and transformation with AI assistance.
-   Analytical question formulation and metric definitions.
-   Spreadsheet, SQL and Python workflows.
-   Structured extraction, classification and entity resolution.
-   Data validation, provenance and reproducibility.
-   Knowledge bases, taxonomies, metadata and information lifecycle.

### Chapter 9. Code generation and software engineering

-   Requirements-to-code prompting.
-   Repository context and codebase exploration.
-   Architecture, implementation and refactoring prompts.
-   Tests, fixtures, linting, static analysis and code review.
-   Debugging and root-cause analysis.
-   Secure coding, dependency risks and verification of generated code.
-   IDE copilots, terminal agents and coding agents.

### Chapter 10. Multimodal prompting and specialist tasks

-   Images, diagrams, screenshots and visual inspection.
-   Audio, transcription and speech workflows.
-   Video understanding and temporal analysis.
-   Tables, charts and mixed-format documents.
-   Image generation and editing prompts.
-   Modality-specific constraints, uncertainty and evaluation.

### Chapter 11. Evaluation, testing and prompt optimisation

-   Defining success criteria before prompt tuning.
-   Rubrics, test cases, golden datasets and representative samples.
-   Pairwise comparison and blind evaluation.
-   Regression testing and model-version drift.
-   Error taxonomies and failure analysis.
-   Cost, latency, quality and risk trade-offs.
-   Prompt versioning and experiment records.

## Level 4 --- Systems designer

### Chapter 12. Workflow orchestration and prompt chains

-   Task decomposition and workflow graphs.
-   Sequential, parallel and conditional execution.
-   Intermediate artifacts and typed hand-offs.
-   State, memory and context management.
-   Retries, idempotency, timeouts and recovery.
-   Observability and workflow-level evaluation.

### Chapter 13. Agentic AI and tool use

-   Agent patterns and autonomy levels.
-   Tool/function calling and structured interfaces.
-   Planning, execution, observation and adaptation.
-   Permissions, approvals and side-effect boundaries.
-   Sandboxing, secrets and least privilege.
-   Stop conditions, escalation and safe failure.
-   Human oversight and audit trails.

### Chapter 14. Reliability, security and responsible AI

-   Prompt injection and indirect instruction attacks.
-   Data leakage, privacy and confidential information.
-   Output validation and schema enforcement.
-   Bias, fairness and responsible use.
-   Risk classification and assurance controls.
-   Source verification and provenance.
-   Operational incident handling.

## Level 5 --- Strategist

### Chapter 15. Enterprise adoption and AI operating models

-   Use-case discovery and prioritisation.
-   Build, buy or configure tool decisions.
-   Process redesign and human/AI task allocation.
-   Governance, policies and standards.
-   Vendor/model evaluation and portability.
-   Change management, training and adoption.

### Chapter 16. Prompt and workflow portfolio management

-   Prompt libraries and reusable patterns.
-   Version control, ownership and lifecycle.
-   Quality dashboards and performance indicators.
-   Cost and value measurement.
-   Continuous improvement and retirement criteria.
-   Reuse, standardisation and controlled variation.

### Chapter 17. Capstone --- Design an AI-enabled professional workflow

-   Select an end-to-end work process.
-   Define baseline, target outcomes and risks.
-   Choose models, tools, data and autonomy level.
-   Design prompts, workflow, evaluation and human checkpoints.
-   Run a controlled pilot and compare against baseline.
-   Document operational playbook and governance.
-   Present evidence of effectiveness and lessons learned.

## Suggested progression

Complete the chapters in order through Level 2. From Level 3 onward,
some chapters can be pursued in parallel depending on current work
needs. Chapters 11, 13 and 14 are cross-cutting: revisit them as
complexity and autonomy increase.

## Completion definition

The programme is complete when the learner can independently: 1. Select
an appropriate model, tool and interaction mode for a task. 2. Define
measurable outcomes and construct fit-for-purpose prompts. 3. Ground
work in documents and data with traceability. 4. Build and verify
document, data and code workflows. 5. Evaluate quality empirically and
diagnose failures. 6. Design agentic workflows with bounded permissions
and recovery. 7. Govern and improve a portfolio of AI-enabled workflows.
