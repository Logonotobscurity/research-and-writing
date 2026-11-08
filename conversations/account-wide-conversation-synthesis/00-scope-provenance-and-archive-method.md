# 00 — Scope, Provenance, and Archive Method

## 1. Purpose

This document defines what the account-wide archive is intended to preserve, what source material informed it, and what claims it must not make.

The objective is not to create a flattering biography or a catalogue of project names. It is to reconstruct the intellectual and practical work visible across conversations: questions asked, positions clarified, concepts developed, systems specified, implementation attempts, evidence gaps, and changes in priority.

The archive should make it easier for a future collaborator—or the user returning to an older line of work—to answer:

- What problem were we trying to understand?
- What did the user actually define or request?
- What interpretation did the assistant introduce?
- What changed after the user corrected or refined the interpretation?
- Which architectural and product decisions emerged?
- What is implemented, planned, proposed, or unverified?
- Which projects share mechanisms or principles?
- What evidence is still needed before a claim can be treated as established?

## 2. Scope

The available synthesis covers these broad domains:

1. Intellectual orientation, investigative curiosity, systems building, and complex problem-solving.
2. Research methodology, evidence classification, source management, synthesis, and evaluation.
3. Identity-Tension Writing and broader communication principles.
4. LOG_ON's business positioning, offers, operating model, and commercial direction.
5. LOG_ON OS, agent runtime, execution kernel, orchestration, and tool boundaries.
6. Agent assurance, security, governance, permissions, approvals, and auditability.
7. PAL, cultural computing, Yoruba and Nigerian Pidgin, code-switching, and multilingual meaning-to-action.
8. Voice AI, speech recognition, voice interfaces, and edge-to-action workflows.
9. Global business intelligence, African market intelligence, and opportunity scanning.
10. Product strategy and the shared full-stack engineering methodology.
11. Specific product dossiers: ContextPocket, Re:Mind Me, MorrowVoice, Grounded Guide, CLIPIN, GigPilot, AgentBridge Africa, SafeChain, ATS/career intelligence, and related experiments.
12. Visual design, branding, creative prompts, and storytelling.
13. Integrations, APIs, MCP, no-code/low-code platforms, and connected workflows.
14. Commercial proof, adoption, customer value, measurement, and the distinction between a developed product and a validated business.

Shorter creative, interpersonal, and utility conversations are not expanded into full product dossiers unless they reveal a recurring method or materially affect a major workstream. They remain part of the account's broader interaction history, but this archive prioritizes the substantive lines of inquiry and development.

## 3. Source boundary

### Available source classes

The synthesis was prepared from:

- The active conversation context.
- Saved project and preference memory.
- Recent-conversation summaries and titles.
- Previously recorded project histories and status notes.
- The existing Research-Led Systems Builder folder in this repository.
- The repository README and six existing phase documents, inspected on 8 November 2026.
- Selected repository and project references preserved in the available context.

### What was not available as a complete source

This archive does not have a complete raw export of every conversation ever held on the account. It therefore cannot guarantee:

- Every chat has been represented.
- Every message has been preserved.
- Every date and sequence is exact.
- Every intermediate assistant or user formulation has been reproduced.
- Every metric or implementation claim has been independently tested.
- Every linked repository or external source has been re-inspected during this pass.

This is a material limitation, not a footnote. Future revisions should ingest raw exports or primary artifacts where greater fidelity is required.

## 4. Evidence and claim classification

Use these labels consistently.

| Label | Meaning | What it permits |
|---|---|---|
| **Repository-observed** | Directly visible in a repository or inspected artifact. | A narrow statement about what that artifact contains. |
| **User-reported** | The user described a goal, decision, project state, metric, or experience. | Attribution to the user's account, not independent verification. |
| **User-defined** | A term, principle, requirement, or design position explicitly set by the user. | Treating it as a design requirement or preference. |
| **Assistant synthesis** | A structured explanation assembled from multiple details. | A useful model, clearly attributed as synthesis. |
| **Joint conclusion** | A formulation clarified over multiple turns and accepted by the user. | A current working conclusion, subject to later revision. |
| **Inference** | A reasoned interpretation beyond directly available statements. | A provisional explanation, not a fact. |
| **Hypothesis** | A testable proposition. | Designing an experiment, not claiming the proposition is true. |
| **Assumption** | A temporary premise used to proceed. | Conditional planning only. |
| **Unknown** | Evidence or information is unavailable. | A request for research or a bounded statement of uncertainty. |
| **Unverified implementation** | An implementation or outcome claim without fresh validation. | Recording the claim and its verification gap only. |

### Important distinction

A statement can be accurately recorded as user-reported and still be unverified. For example, a project metric in a resume draft is evidence that the metric was used in that draft; it is not independent proof that the underlying measurement was calculated correctly.

Likewise:

- A specification is evidence of intended behaviour, not proof of implementation.
- A commit is evidence of a repository change, not proof of correctness.
- A passing local test is evidence for that test run and environment, not a security certification.
- A public repository is evidence of publication, not evidence of product-market fit.
- A prototype is evidence of exploration, not necessarily evidence of adoption.
- A model-generated answer is not primary evidence about the external world.

## 5. Reconstruction rules

### Preserve evolution

When a user corrects an earlier interpretation, preserve both the earlier reading and the correction. Record:

1. The initial interpretation.
2. What it captured.
3. What it omitted or distorted.
4. The user's correction.
5. The more accurate working model.
6. What remains uncertain.

This rule is particularly important in the Research-Led Systems Builder discussion: the initial builder-centred reading was expanded by investigative curiosity, but the user explicitly clarified that building remains central.

### Avoid false quotation

Do not put synthesized wording inside quotation marks. Exact quotations are retained only when original wording is available in the conversation context. Otherwise use attributed paraphrase.

### Preserve status

For projects, use a status vocabulary such as:

- **Idea / exploration**
- **Research / specification**
- **Prototype**
- **Partial implementation**
- **Local validation reported**
- **Hosted validation reported**
- **Pilot**
- **Production**
- **Commercially validated**
- **Unknown / requires inspection**

A project may occupy more than one status across different subsystems.

### Distinguish the layers of a product

For each product, separately describe:

- User problem and intended audience.
- Product promise and non-goals.
- Workflow and behavioural assumptions.
- Architecture and technology choices.
- Authority, privacy, security, and failure handling.
- Actual implementation evidence.
- Validation and adoption evidence.
- Current gaps and next tests.

## 6. Organizing principle

The archive uses a hub-and-spoke arrangement:

- **Chronology** captures the evolution across phases.
- **Cross-cutting documents** preserve recurring intellectual, research, communication, business, and architectural principles.
- **Product dossiers** give each product a bounded description and status record.
- **Cross-workstream synthesis** reveals shared mechanisms, dependencies, tensions, and portfolio-level questions.
- **Latest phase** records the newest clarification and the next evidence agenda.

This organization is preferable to one document per chat title alone because many discussions revisit the same system from different angles. It is also preferable to a single master essay because individual workstreams need to remain inspectable and updateable.

## 7. Known limitations and repair path

The archive should be considered a high-coverage synthesis of the available context, not a complete archival database.

To improve fidelity:

1. Ingest available raw conversation exports.
2. Attach source IDs or dates to each claim.
3. Add exact message excerpts where the source is available.
4. Compare the synthesis against repositories and implementation evidence.
5. Record disagreements and corrections as new events.
6. Keep an explicit missing-source register.
7. Review the archive after each major project or research milestone.

## 8. Governing principle

A useful archive does not merely remember what was said. It preserves why a decision was made, what evidence supported it, what changed, and what still needs to be tested.
