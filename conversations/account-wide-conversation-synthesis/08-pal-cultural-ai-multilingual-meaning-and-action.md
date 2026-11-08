# 08 — PAL, Cultural AI, Multilingual Meaning, and Action

## 1. Research problem

The PAL workstream explores a limitation in systems that treat speech and text as literal strings: the words alone may not be enough to recover the intended meaning, social function, or action.

The user has focused on Yorùbá, Nigerian Pidgin, English, and code-switched speech, including situations where meaning is indirect, relational, context-dependent, or culturally situated.

The central research question is not simply whether a model can translate a sentence. It is whether a system can preserve the meaning that matters to the task without inventing cultural context or making unsafe assumptions.

## 2. Project and repository context

Known references:
- PAL repository: https://github.com/Logonotobscurity/pal
- Voice/STT research repository: https://github.com/Logonotobscurity/wwhisper

The user has also referred to PAL, CIE, DAPF, and earlier terminology that was revised. **DAPF replaces the earlier Proverb-Logic framing.**

The exact current implementation state must be verified in the repositories before a present-tense feature claim is made.

## 3. Core research distinction

The work separates several layers that are often conflated:

1. **Transcription:** what speech sounds were recognized as words.
2. **Literal meaning:** what the recognized words conventionally mean.
3. **Pragmatic meaning:** what the speaker is doing through the utterance.
4. **Discourse position:** how the utterance functions in the conversation.
5. **Relationship and register:** what social relationship and mode of address shape interpretation.
6. **Cultural grounding:** which contextual frames may be relevant and how strongly they are supported.
7. **Task intent:** what the speaker wants to achieve.
8. **Action proposal:** what structured operation could satisfy the intent.
9. **Authority and policy:** whether the proposed action is permitted.
10. **Execution and verification:** whether the operation occurred and whether the intended outcome was achieved.

A correct transcript does not guarantee correct intent. A plausible intent does not authorize execution.

## 4. Cultural grounding rules

The user has emphasized that culture should be treated as contextual evidence, not as a demographic shortcut.

A system must not infer a speaker's desired proverb, register, interpretation, or action from ethnicity, name, location, religion, or social category.

Cultural knowledge should help generate or retrieve interpretations only where the utterance and context support them. When context is missing, the system should ask rather than fill the gap with a stereotype.

A culturally informed answer can still be wrong. Native-speaker validation and realistic discourse examples are required.

## 5. PAL conceptual dimensions

The available PAL design notes describe 13 contextual dimensions:

1. Simulation world.
2. Conceptual domain.
3. Discourse position.
4. Speech act.
5. Relationship register.
6. Community specificity.
7. Failure contexts.
8. Provenance.
9. Philosophical layer.
10. Worldview assumptions.
11. Temporal logic.
12. Power symmetry.
13. Deployment risk.

These dimensions are intended to preserve context that a generic semantic embedding or literal translation may not capture. They should not be treated as a mandatory set of fields for every utterance; the architecture must distinguish required, optional, unknown, and inapplicable dimensions.

## 6. Retrieval and reasoning direction

The prior design describes a contextual retrieval process:

**Context parse → semantic retrieval → filters → relation expansion → safety policy → ranking.**

The process should consider:
- Task and domain.
- Discourse context.
- Linguistic mode and code-switching.
- Relationship and register.
- Source provenance and community specificity.
- Contradicting interpretations.
- Freshness and source quality.
- Whether the retrieved material supports the proposed interpretation.

Retrieval should not produce one apparently certain interpretation when several remain plausible.

## 7. Decision states

The user has identified four useful decision states:

- **DEPLOY:** sufficient evidence and context support the interpretation and intended use.
- **DEPLOY_WITH_CAVEAT:** the system may proceed with an explicit limitation or qualification.
- **ASK_FOR_CONTEXT:** important context is missing or multiple interpretations remain materially different.
- **DO_NOT_DEPLOY:** evidence, safety, or task constraints do not support use.

These states help preserve uncertainty rather than forcing a binary answer.

## 8. DAPF: Discourse and Pragmatic Framing

The newer framework replaces the earlier Proverb-Logic emphasis with a broader way to represent communicative strategy.

The available dimensions are:
- Task grounding.
- Audience context.
- Linguistic mode.
- Discourse strategy.
- Cultural grounding.
- Action close.

Possible strategies include:
- DIRECT.
- CLARIFY.
- QUESTION_FIRST.
- ANALOGY.
- STORY_FIRST.
- COMMUNITY_REFERENCE.
- PROVERB.
- MULTIPLE_INTERPRETATIONS.
- REPAIR.
- ESCALATE.
- NONE.

**NONE must remain a valid strategy.** The architecture should not force cultural expression into an interaction when direct language is clearer or culturally neutral language is more appropriate.

Strategy selection must not be inferred from a demographic label.

## 9. Uncertainty representation

The PAL work should avoid collapsing all uncertainty into one scalar confidence value.

Uncertainty may concern:
- ASR transcription.
- Language identification.
- Code-switch boundary.
- Word sense.
- Pragmatic intent.
- Cultural interpretation.
- Relationship context.
- Slot extraction.
- Task suitability.
- Action policy.
- External execution.

A system can be confident about transcription and uncertain about intent. It can understand the user's intent but lack authority to execute the requested operation.

Those states should remain distinct in schemas, traces, UI, and evaluations.

## 10. Evaluation design

The conversation history includes a proposed comparison across conditions:

- **A:** generic zero-shot model.
- **B:** literal translation.
- **C:** semantic retrieval.
- **D:** naive culturalization.
- **E:** PAL.
- Additional ablations to isolate individual components.

The test set should include:
- Explicit business request.
- Ambiguous idiom.
- Code-switched utterance.
- Indirect disagreement.
- Emotional expression.
- Cultural reference.
- False cultural cue.
- User correction.
- Missing context.
- Unnecessary culturalization.

Evaluation should measure more than answer preference:
- Meaning preservation.
- Intent accuracy.
- Contextual interpretation.
- Clarification behaviour.
- False cultural inference.
- Over-culturalization.
- Uncertainty calibration.
- Task success.
- Unsafe action proposals.
- Performance by language and context.

## 11. Dataset and annotation discipline

The available notes mention:
- AfriSwitch as an approximately 54.41-hour corpus with roughly 16,602 utterances, including Yoruba and Pidgin material.
- AfriSwitchCare as an approximately 12.11-hour corpus with roughly 108 simulated clinical conversations across nine languages, with a published evaluation test split.
- A preliminary cultural annotation pilot of ten examples that requires Yoruba expert validation.
- A separate voice pilot specification of 50 utterances.

These figures are preserved from the research context and are not independently rechecked here. Dataset use must follow the actual published licence, split, schema, and collection conditions.

No corpus should be fabricated to fill a benchmark gap. A benchmark loader must use the actual published schema and fail closed when expected fields or split boundaries do not exist.

## 12. Repository and implementation caveats

The available project notes describe PAL as containing or planning:
- TypeScript schemas and Zod validation.
- Authenticated workspace and tenancy boundaries.
- Sahara voice ingestion.
- Semantic and workflow agents.
- Workflow intermediate representation validation.
- Capability registry.
- Policy and proposal creation.
- Approval UI/API.
- Execution and verification service boundaries.

The same notes identify incomplete or historically absent areas at the time of inspection:
- Research intelligence plane.
- Full React Flow workspace.
- Real production executors.
- Realtime transcript experience.
- Full activity/audit UI.
- Benchmark artifacts and measured results.
- Observability maturity.
- Complete voice frontend.

Some previous notes reported a local test count of 139 passing at a particular snapshot. That is a historical reported state, not a current verified test result.

A benchmark report was recorded as NOT RUN in the prior context. The evaluator also had mock or placeholder paths, and the loader initially made assumptions about dataset fields and splits. A subsequent branch change was recorded as fail-closed for the published test split. The complete current code state needs inspection.

## 13. Research integrity risks

- Cultural stereotypes presented as meaning recovery.
- Literal translation presented as pragmatic understanding.
- One cultural interpretation treated as universal.
- Synthetic examples presented as natural discourse.
- Dataset split leakage.
- Invented or mislabelled corpus fields.
- Placeholder evaluation reported as a measured benchmark.
- Strong aggregate scores concealing low performance in a language or context.
- Model confidence presented as evidence.
- Native-speaker disagreement erased rather than recorded.

## 14. Open questions

1. Which parts of PAL should be deterministic metadata, retrieval, learned representation, or human review?
2. How should community and dialect specificity be represented without essentializing speakers?
3. What is the correct annotation protocol for implied intent and discourse function?
4. How should disagreement between competent native annotators be recorded?
5. Which metrics reveal preservation of meaning rather than fluency?
6. How should PAL distinguish helpful cultural grounding from unnecessary culturalization?
7. What minimum evidence justifies each decision state?
8. Can action-level safety be measured independently of transcription and semantic quality?

## 15. Current working conclusion

PAL is best framed as a context-sensitive meaning and action-support system. Its value is not cultural decoration; it is preserving task-relevant meaning, representing uncertainty, asking when context is missing, and preventing an interpretation from bypassing policy and authority.
