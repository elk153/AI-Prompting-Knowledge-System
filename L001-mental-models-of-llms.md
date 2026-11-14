# L001 --- A Practical Mental Model of Large Language Models

**Decision:** D001  
**Roadmap:** Level 1, Chapter 1  
**Version:** 1.0  
**Date:** 2026-11-14  
**Status:** Reviewed

## 1. Learning objective

By the end of this lesson, I will be able to explain how a modern large language model (LLM) turns context into generated output, estimate the operational implications of tokens and context limits, distinguish model uncertainty from missing knowledge or missing tools, and select a proportionate response (prompting, retrieval, tool use, model change or human verification) for a professional task.

### Success criteria

- Explain next-token generation, tokenisation, context windows and sampling accurately, without describing an LLM as a database or deterministic reasoning engine.
- Diagnose at least four common failure modes and identify which intervention is most likely to address each.
- Given three professional tasks, justify whether prompting alone is sufficient or whether model selection, retrieval, tools, fine-tuning or human review is also needed.
- Score at least 20/28 on the evaluation grid, with no score of 1 for output verification or risk/limitations.

## 2. Why this matters

Prompting is an interface to a model, not a universal fix for every AI problem. A useful mental model helps distinguish problems that can be improved by clearer instructions from problems caused by missing or stale information, model capability, context limits, tool availability or weak verification.

For an engineering leader, this distinction matters operationally. If an answer is wrong because the model has no access to the current source of truth, adding more adjectives to the prompt is unlikely to solve it. If the task requires exact arithmetic, database state or a current market price, a calculator, query or trusted live source may be more appropriate. If the task is ambiguous, improving the task specification may be enough.

The durable principles in this lesson apply broadly, but implementation details—tokenisation, context limits, supported modalities, sampling controls, tool interfaces and model strengths—vary by provider, model and product version. Check current documentation for the actual system in use.

## 3. Prerequisites

- **Knowledge:** General familiarity with software systems, data and probabilistic processes. No machine-learning mathematics is required.
- **Tools/access:** A conversational AI interface. Optional: provider documentation and a token-counting utility for the model being studied. The exercises can be completed without API access or paid developer tools.
- **Previous lessons:** None. D001 has no dependencies.

## 4. Core concepts

### 4.1 The short version: a conditional generator

A language model processes an input sequence represented as tokens and generates an output sequence. In a conventional autoregressive language model, generation can be described as repeatedly estimating a probability distribution for the next token given the preceding context:

\[
P(x_t \mid x_1, x_2, \ldots, x_{t-1})
\]

It selects or samples a token, appends it to the sequence, and repeats until a stopping condition is reached. The model is not looking up a pre-written answer. It is generating a continuation conditioned on the context and its learned parameters.

This explains both the power and the limitation:

- It can generalise patterns learned during training and produce useful language, code, transformations and structured outputs.
- A plausible continuation is not necessarily a true statement, a valid calculation or a verified observation.
- The model's output is sensitive to the input context, model version, system instructions, decoding configuration and surrounding product orchestration.

This description is a useful baseline for many modern text-generating LLMs, not a claim that every AI model or multimodal system has exactly the same architecture.

### 4.2 From text to tokens

Models generally do not process text as human-readable words. A tokenizer maps text into token IDs. A token may represent a whole short word, part of a longer word, punctuation, whitespace or another frequently occurring text fragment. Different model families can use different tokenizers, so the same text need not have the same token count everywhere.

Why this matters:

- **Capacity:** Input and generated output consume token capacity.
- **Cost and latency:** API products commonly meter at least some usage by input and output tokens.
- **Truncation and prioritisation:** A long prompt, conversation or document may exceed the available context budget.
- **Language and format effects:** Code, tables, unusual strings and languages can tokenise differently from ordinary English prose.

Rules such as “one token is about four English characters” are rough estimates, not sizing guarantees. Use the actual provider's tokenizer or token-counting facility when capacity or cost matters. Images, audio, video and other modalities may also consume context or modality-specific budgets.

### 4.3 Context window: working set, not permanent memory

The context window is the bounded amount of information the model can condition on for a particular request or interaction. Depending on the product and model, it can include system/developer instructions, conversation history, the current request, supplied documents, tool definitions and results, and generated output. Exact accounting differs by interface and model.

Think of it as a working set rather than the model's entire training corpus or a guaranteed long-term memory store.

Consequences:

1. A fact in an earlier turn may no longer be available if the product truncates, summarises or otherwise manages history.
2. A large context window does not guarantee that every detail will be used correctly. Retrieval and attention over long inputs can be imperfect; irrelevant material can compete with important evidence.
3. More context is not automatically better. Curate for relevance, authority, freshness and clarity.
4. For long-running work, maintain explicit state, concise summaries, source references or external retrieval rather than relying on an assumption that the model remembers everything.

A context limit is a hard capacity boundary; poor use of a large context is a separate quality problem. Do not confuse the two.

### 4.4 Transformer intuition

Many modern LLMs are based on the Transformer architecture. At a high level, token IDs are mapped into vector representations. Self-attention lets a position compute context-dependent relationships to other positions in the sequence; feed-forward layers transform those representations. Stacked layers produce representations used to predict subsequent tokens.

Self-attention is not human attention, consciousness or a guarantee of logical reasoning. It is a learned computational mechanism for mixing information across positions. The original Transformer paper introduced an architecture based on attention mechanisms rather than recurrence and convolutions; later LLMs build on and modify this foundation.

You do not need to implement attention to prompt effectively. The useful operational point is that the model's response is conditioned on the tokens made available to it, transformed through learned parameters—not on an independent, authoritative view of the world.

### 4.5 Training knowledge, current information and hallucination

A model's parameters encode statistical structure learned from training and subsequent training stages. They are not a live, queryable copy of the internet or your organisation's systems.

Distinguish three information sources:

- **Parametric knowledge:** Information reflected in learned model parameters. It can be broad and useful, but may be incomplete, outdated or expressed with unjustified confidence.
- **Context-provided information:** Material supplied in the current request or conversation, such as a document, specification or data extract. Its usefulness depends on relevance, completeness and trustworthiness.
- **Externally retrieved or tool-produced information:** Results from search, databases, APIs, code execution or other tools. These can provide current or exact data, but introduce their own access, provenance, execution and interpretation risks.

A hallucination is an output that presents unsupported or false content as if it were valid. It can occur when the model fills a gap with a plausible continuation, misreads ambiguous context, blends related facts or produces fabricated citations, details or calculations. The model may not reliably signal that it is guessing.

Practical controls:

- Ask it to distinguish supplied facts, external evidence, assumptions and unknowns.
- Require citations or source locations when claims must be traceable; then verify that the sources support the claims.
- Provide authoritative source material when the answer depends on private, current or specialised facts.
- Use deterministic tools for exact calculations and system state.
- Use human review for high-impact decisions.

A request to “be accurate” or “do not hallucinate” is not a verification mechanism.

### 4.6 Probabilistic generation and non-determinism

The model generally produces a distribution over possible next tokens. A decoding strategy turns that distribution into an output. Sampling controls such as temperature or nucleus sampling (top-p), where exposed, influence how candidate tokens are selected. Their precise behaviour and availability are implementation-specific.

Lower sampling randomness may make outputs more repeatable in some settings, but it does not make the underlying answer factually correct. A confident, fluent error remains an error. Conversely, variation is not automatically a defect: different valid phrasings or approaches may be useful for creative or exploratory tasks.

Even when a product exposes deterministic-looking settings, exact reproducibility may be affected by model updates, serving infrastructure, hidden orchestration, tools, and other implementation details. Treat repeatability as something to test in the actual environment.

### 4.7 Model families and capability differences

“LLM” is a broad category, not a single capability profile. Models and product modes can differ in:

- Reasoning and multi-step problem-solving performance.
- Coding, mathematics, language and domain strengths.
- Context capacity and long-context behaviour.
- Multimodal input/output support.
- Tool-use and structured-output reliability.
- Latency, cost, throughput and availability.
- Knowledge freshness, safety behaviour and deployment constraints.

A model's advertised context size or benchmark score is not a substitute for testing it on your own task. Select against task requirements and operational constraints, not brand reputation alone. For a consequential workflow, use a representative test set and verify the actual output.

### 4.8 Prompting is one lever among several

Use the intervention that addresses the root cause:

| Problem | Likely useful intervention | What prompting alone cannot guarantee |
|---|---|---|
| The task or desired output is ambiguous | Clarify objective, audience, constraints and acceptance criteria | That missing business decisions can be inferred correctly |
| Relevant facts are in supplied documents | Provide focused context and ask for traceable answers | That every passage will be noticed or interpreted correctly |
| Facts are current or private to an organisation | Retrieval, connectors, database/API access, then source verification | Access to information the model was never given |
| Exact calculation or state transition is required | Calculator, code, database query or validated business tool | Arithmetic or execution correctness merely by instruction |
| Model lacks a needed capability | Select a more suitable model or specialist tool | New capability through wording alone |
| Repeated specialised behaviour is required | Evaluate prompt patterns, workflow design, and—where justified—fine-tuning | That fine-tuning supplies live facts or replaces retrieval |
| Outcome is high-impact | Independent checks, human approval and audit trail | Safety or correctness from fluent output alone |

Fine-tuning changes model behaviour through additional training; it is not the same as giving a model a document at inference time. Retrieval supplies relevant external information at run time. Tools let a model request actions or computations from other systems. These interventions solve different problems and can be combined.

### 4.9 Common failure modes and diagnostic questions

| Symptom | Possible root cause | Diagnostic question |
|---|---|---|
| Plausible but false factual answer | Missing evidence; stale or weak parametric knowledge | What authoritative source supports this claim? |
| Missed detail in a long document | Context overload, poor retrieval, weak attention to the relevant passage | Can the task be narrowed or the evidence located explicitly? |
| Inconsistent answer across runs | Sampling, model updates, context variation or tool variability | Were model, settings, context and tools held constant? |
| Incorrect exact number | Reasoning or arithmetic limitation; ambiguous units | Can a calculator or executable check validate it? |
| Confident answer about internal company state | No access to the system of record | Which connector, query or approved data source supplies that state? |
| Strong result on one model, weak on another | Capability or instruction-following differences | Has the workflow been tested on the target model? |
| Output follows malicious text inside a document | Untrusted input treated as instruction | Are source content and governing instructions clearly separated? |

The last example is introduced here as a mental-model warning; detailed prompt-injection controls belong to a later decision.

## 5. Reading and reference material

Access date for all web references below: **2026-11-14**.

| Type | Author / organisation | Title | URL | Why it matters |
|---|---|---|---|---|
| Primary documentation | OpenAI | Understanding and counting tokens | https://help.openai.com/en/articles/4936856-what-are-tokens | Explains tokenisation and practical token-count estimates; product-specific details may change. |
| Primary documentation | OpenAI | Key concepts: Tokens | https://developers.openai.com/api/docs/concepts | Explains tokens and context-length implications in the API context. |
| Primary documentation | Anthropic | Context windows | https://platform.claude.com/docs/en/build-with-claude/context-windows | Describes context-window accounting, tool use and context management for Claude. |
| Primary documentation | Google AI for Developers | Understand and count tokens | https://ai.google.dev/gemini-api/docs/tokens | Describes tokenisation and token counting for Gemini, including non-text inputs. |
| Research paper | Vaswani et al. (2017) | Attention Is All You Need | https://arxiv.org/abs/1706.03762 | Original Transformer architecture paper; useful technical foundation, not a complete description of every current LLM. |
| Optional primary documentation | Anthropic | Models overview | https://platform.claude.com/docs/en/models/overview | Example of provider-specific model capability and context comparisons; values are version-sensitive. |

Start with the token and context documentation for the provider/model actually in use. Read the Transformer paper selectively if you want architectural depth; understanding its full mathematical detail is not required to complete this lesson.

## 6. Worked example

### Task and baseline

**Professional task:** Prepare a short briefing on the current status of a software delivery programme, including completed milestones, open risks and the latest release date.

A weak baseline prompt might be:

> Write a briefing on our software delivery programme. Include the latest status, risks and release date. Be accurate and concise.

The prompt is understandable but assumes the model has access to the programme's current state. Without supplied records or connected tools, it cannot know the latest release date or internal risks. It may fill those gaps with plausible-sounding content.

### Improved approach

First choose the right information path. If the user can supply a status report and risk register, use those as the evidence base:

> Using only the two supplied documents (the delivery status report and risk register), prepare a one-page executive briefing for the steering committee.
>
> Include: overall status, milestones completed since the previous report, the next milestone and date, the three most material open risks, decisions required, and any schedule variance explicitly stated in the sources.
>
> For each material status or date, identify the source document and section/page. Do not infer a current release date if it is absent or inconsistent. Separate documented facts from your interpretation. List missing or conflicting evidence under “Open questions”. Do not invent owners, dates, percentages or mitigations.
>
> Keep the briefing concise and use a table for risks. If the supplied documents do not support a requested point, say so.

If the documents are not available, the correct next step is to request them or use an authorised connector to retrieve them—not to ask the model to guess harder.

### Explanation

The improved approach does more than add detail. It changes the epistemic contract: the model is asked to work from a defined evidence set, preserve traceability, and expose gaps rather than silently complete them. The intervention addresses missing context and verification, not just wording.

### Validation

- Check every milestone and date against the named source passage.
- Confirm that each risk appears in the register and that severity/owner fields have not been altered.
- Compare conflicting dates explicitly; do not silently choose one.
- Confirm that missing facts are reported as unknown.
- Have the programme owner validate interpretation and decisions before circulation.

## 7. Exercises

### Exercise 1 --- Guided practice: explain the mechanism

- **Scenario:** A colleague says, “The model searches its database of answers and returns the closest match.”
- **Task:** In 150–250 words, correct or qualify that mental model. Explain tokenisation, conditional next-token generation and why a plausible answer can still be false.
- **Inputs:** This lesson and the OpenAI token reference in Section 5.
- **Expected deliverable:** A short explanation suitable for a technically literate manager, plus one analogy and one limitation of that analogy.
- **Constraints:** Do not describe the model as conscious, as a deterministic database, or as having live access to the internet by default.
- **Hints:** Explain what is conditioned on (the available context) and what is stored in learned parameters.

### Exercise 2 --- Independent practice: diagnose and select an intervention

For each scenario below, identify the likely root cause, the best first intervention, one residual risk and a verification method.

1. A model is asked for the current number of unresolved production incidents but has no access to the incident system.
2. A model summarises a 200-page policy but omits a critical exception in an appendix.
3. A model produces a fluent financial calculation that is off by 8%.
4. A model is asked to compare two architecture options, and the decision criteria have not been specified.

- **Expected deliverable:** A four-row diagnosis table and revised task approach for each case.
- **Evaluation evidence:** Each intervention must address the stated root cause rather than simply adding “be more accurate” to the prompt.

### Exercise 3 --- Failure analysis: expose the false premise

- **Intentionally flawed prompt/output:**

  Prompt:
  > You know our current cloud spend. Tell me this month's exact spend and explain why it increased. Do not ask questions; make your best estimate.

  Example output:
  > This month's spend is €184,250, up 12% due to increased Kubernetes compute and storage.

  The figures and explanation above are deliberately fabricated for this exercise; they are not real organisational data.

- **Diagnose:** Identify the unsupported assumptions, distinguish unavailable data from model capability, and explain why a confident answer is not evidence.
- **Improve:** Rewrite the request so it obtains a defensible answer, including the required source, period, currency, comparison baseline and cost breakdown.
- **Explain the root cause:** State why prompt wording cannot create access to a billing system or establish the truth of a guessed number.
- **Expected deliverable:** A diagnosis, revised prompt and a short validation checklist.

### Transfer exercise --- apply the model to another system

Choose a different provider/model or a non-chat AI tool that you use. Consult its current documentation and compare:

- How it represents or counts input tokens (or the equivalent input units).
- Its context capacity and what counts toward it.
- Its supported modalities and tool interfaces.
- One important capability difference that could affect a real task.

**Expected deliverable:** A one-page comparison with links, access date, and a short statement of which principles transfer and which implementation details are provider-specific. If a feature or limit cannot be verified, mark it unknown rather than guessing.

## 8. Evaluation grid

Score only what the submitted exercises demonstrate. Use 1 = insufficient, 2 = developing, 3 = competent, 4 = strong.

| Criterion | 1 --- Insufficient | 2 --- Developing | 3 --- Competent | 4 --- Strong | Score |
|---|---|---|---|---|---:|
| Objective and success criteria | Cannot state what a correct explanation or diagnosis must achieve | States a broad goal but omits measurable checks | Explains the mechanism and defines observable checks | Prioritises checks and adapts them to task criticality | |
| Context and constraints | Treats model knowledge as current/private system access | Recognises some missing context but leaves assumptions implicit | Identifies relevant evidence, limits and assumptions | Explicitly handles provenance, freshness, conflicts and unknowns | |
| Prompt/workflow design | Uses a vague request regardless of root cause | Adds instructions but does not change the information path | Chooses a suitable prompt or workflow for the problem | Uses the minimum sufficient combination of context, retrieval and tools | |
| Tool/model selection | Assumes any model can answer any task | Suggests a plausible tool without explaining fit | Selects an appropriate model/tool or identifies that more evidence is needed | Validates trade-offs and provides a practical fallback | |
| Output verification | Accepts fluent output without checks | Performs superficial plausibility checks | Checks claims against sources or deterministic tools | Provides traceable checks and handles failed/conflicting evidence | |
| Risk and limitations | Ignores hallucination, privacy or impact | Names risks without controls | Applies proportionate verification and human review | Defines operational controls, escalation and stop conditions | |
| Transferability | Cannot distinguish general principles from provider details | Transfers ideas with substantial prompting | Applies principles to another model/tool and flags differences | Independently tests and adapts the approach with sound judgement | |
| **Total** |  |  |  | **/28** | |

**Suggested threshold:** 20/28, with no score of 1 in output verification or risk/limitations.

### Assessment interpretation

- **7–13:** Revisit the core concepts and repeat guided practice.
- **14–19:** Developing; complete additional independent practice.
- **20–24:** Competent; apply the mental model to a real, low-risk task and revisit the result.
- **25–28:** Strong; demonstrate transfer to a second model or tool and explain the limits of the comparison.

## 9. Reflection and next actions

After completing the exercises, record:

- Which explanation or analogy helped you understand token generation, and where did it break down?
- Which failure mode had previously looked like a prompt problem but was actually a context, model or tool problem?
- What evidence did you use to verify outputs?
- Which principles transferred to the second model/tool, and which details differed?
- What would you change in a real workflow as a result?

Do not treat a high score as proof that every model behaves identically. The objective is a practical diagnostic model that improves tool and workflow choices.

## 10. Completion record

| Field | Record |
|---|---|
| Exercises completed | Pending learner completion |
| Evaluation score | Pending |
| Evidence / artifact links | Pending |
| Reviewer notes | Lesson reviewed against the repository quality gate; learner performance not yet assessed |
| Completion date | Pending |
| Follow-up decision | D002 remains unexecuted; execute only on explicit instruction |
 
### Completion criteria

This lesson is complete when all of the following are true:

1. Exercises 1–3 and the transfer exercise have been submitted.
2. The learner can accurately explain tokens, conditional generation, context windows and probabilistic output without relying on the “database of answers” misconception.
3. The learner correctly diagnoses the four independent-practice scenarios and chooses interventions that address their root causes.
4. The learner's evaluation score is at least **20/28**, with no score of 1 for output verification or risk/limitations.
5. The transfer exercise cites current documentation for a second model/tool and clearly distinguishes general principles from provider-specific behaviour.
6. Reflection and the completion record are filled in with evidence. A generated or reviewed lesson alone does not constitute learner completion.
