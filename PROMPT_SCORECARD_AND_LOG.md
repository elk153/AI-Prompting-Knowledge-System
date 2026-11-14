# Prompt Effectiveness Scorecard and Progress Log

**Version:** 1.0\
**Date:** 2026-11-14

## 1. Assessment principles

A prompt is effective when it helps achieve the intended task outcome
reliably and efficiently in its actual model/tool/context environment.

Do not equate a polished prompt with a successful result. Evaluate
separately: - Prompt design. - Model capability and configuration. -
Context and input-data quality. - Tool availability and tool
execution. - Output quality and verification. - Human review and
downstream impact.

If no output or execution evidence is supplied, mark outcome-dependent
criteria **N/O (not observed)** rather than guessing.

## 2. Prompt review rubric

Score each criterion from 1 to 5.

  ---------------------------------------------------------------------------
  Criterion         1 --- Weak           3 --- Adequate    5 --- Excellent
  ----------------- -------------------- ----------------- ------------------
  Goal clarity      Task unclear         Task              Outcome and
                                         understandable    purpose explicit

  Context           Key context absent   Most relevant     Sufficient,
  sufficiency                            context present   prioritised and
                                                           well delimited

  Constraints and   Important limits     Main constraints  Risks, exclusions
  boundaries        absent/conflicting   stated            and ambiguity
                                                           handled

  Output contract   Output unspecified   Format partly     Format, audience,
                                         specified         depth and
                                                           acceptance
                                                           criteria clear

  Evidence and      No evidence          Sources/context   Traceability,
  grounding         requirements         requested         uncertainty and
                                                           missing-evidence
                                                           handling defined

  Model/tool fit    Poor or unstated fit Plausible fit     Tool choice
                                                           justified against
                                                           task needs

  Workflow design   Monolithic or        Reasonable task   Decomposition,
                    brittle              structure         checkpoints and
                                                           recovery fit
                                                           complexity

  Testability       No way to judge      Some checks       Measurable
                    success              possible          criteria and
                                                           representative
                                                           tests

  Efficiency        Excessive or         Reasonable        Minimum sufficient
                    insufficient detail                    instruction
                                                           without losing
                                                           control

  Risk and privacy  Relevant risks       Basic safeguards  Proportionate
                    ignored                                safeguards and
                                                           human approvals
  ---------------------------------------------------------------------------

**Prompt design score:** sum / 50.\
**Percentage:** (sum ÷ 50) × 100.

Suggested interpretation: 10--20 weak; 21--30 developing; 31--40
competent; 41--46 strong; 47--50 exceptional. These are diagnostic
bands, not universal scientific thresholds.

## 3. Outcome score (only when output is available)

Score each from 1 to 5, using task-specific evidence.

  -----------------------------------------------------------------------
  Criterion                           Assessment question
  ----------------------------------- -----------------------------------
  Correctness                         Are factual, analytical or
                                      technical claims correct?

  Completeness                        Are all required elements
                                      addressed?

  Relevance                           Does the output solve the intended
                                      problem?

  Usability                           Can the result be used with
                                      acceptable rework?

  Consistency                         Does it meet the criteria across
                                      repeated or varied cases?

  Traceability                        Can material claims be checked
                                      against sources/data?

  Efficiency                          Was the result achieved with
                                      reasonable time, cost and
                                      interaction?
  -----------------------------------------------------------------------

Do not combine prompt design and outcome scores into one number unless
the weighting and purpose are explicit. Keep the two dimensions visible.

## 4. Review output format

For each submitted prompt, provide:

1.  **Intent understood:** one-sentence interpretation.
2.  **Overall diagnosis:** strongest aspect and principal weakness.
3.  **Scorecard:** criterion, score, evidence and improvement.
4.  **Top three improvements:** prioritised by expected impact.
5.  **Revised prompt:** preserve the user's intent; avoid unnecessary
    complexity.
6.  **Why it should improve:** explain the causal rationale and
    assumptions.
7.  **Test plan:** how to compare the original and revised prompts.
8.  **Attribution:** prompt issue, context issue, model limitation, tool
    issue, execution issue or unknown.

## 5. Controlled comparison protocol

For meaningful prompt evolution tracking: - Keep the task, input data
and success criteria constant. - Record model/provider, model version if
known, settings, tools and date. - Run original and revised prompts on
the same representative cases. - Use the same scoring rubric;
blind-review outputs where practical. - Repeat tests when model output
variance matters. - Record sample size and limitations. - Do not
attribute improvements to prompt changes if the model, tools or input
data also changed without noting the confounder.

## 6. Prompt effectiveness log

Append one entry per assessed prompt. Do not replace previous entries.

### Entry template

#### P-YYYYMMDD-XX --- \[Short task name\]

-   **Date:**
-   **Use case category:** chatbot / document analysis / document
    generation / coding / data / research / multimodal / agentic / other
-   **Task and intended outcome:**
-   **Model/provider/version:**
-   **Tools and settings:**
-   **Prompt identifier/version:**
-   **Input/context description:**
-   **Original prompt:** \[verbatim or redacted summary; do not store
    confidential content without approval\]
-   **Output available:** yes / no
-   **Prompt design score:** \_\_ / 50 (or N/O)
-   **Outcome score:** \_\_ / 35 (or N/O)
-   **Evidence/sample size:**
-   **Main failure mode(s):**
-   **Attribution:** prompt / context / model / tool / execution /
    unknown
-   **Top improvements:**
-   **Revised prompt reference:**
-   **Retest date/result:**
-   **Learning / reusable pattern:**

## 7. Progress dashboard

Update after each assessment. Never invent missing data.

  ----------------------------------------------------------------------------------------
  Date     Entry ID Category       Prompt    Outcome Model/tool   Comparable   Key
                                score /50        /35              to prior?    learning
  -------- -------- ---------- ---------- ---------- ------------ ------------ -----------
  ---      ---      Baseline          N/O        N/O ---          ---          Initial
                    not yet                                                    scorecard
                    recorded                                                   created

  ----------------------------------------------------------------------------------------

### Trend interpretation

Track: - Mean prompt design score, with number of assessments. - Mean
outcome score, with number of observed outcomes. - Scores by task
category. - Percentage of tests meeting task-specific acceptance
criteria. - Rework/time/cost where measurable. - Common failure modes
and their frequency.

Do not claim improvement based on a single unrelated task. Prefer
category-specific trends and paired comparisons.

## 8. Privacy and retention

Do not record credentials, secrets, personal data or confidential
business content unnecessarily. Redact prompts and inputs where needed.
Store only the minimum information required to learn from the
assessment.
