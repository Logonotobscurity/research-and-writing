# 03 — Research Method, Evidence Discipline, and Intelligence Workflows

## 1. Why this became a recurring workstream

Research appears across the user's product, business, technical, and writing conversations. It is not limited to finding articles or collecting links. The user repeatedly asks for a structured investigation that can explain a mechanism, expose a gap, compare competing explanations, inform a decision, and lead to a test or action.

The research practice is intended to be durable: source material, claims, contradictions, experiment notes, decisions, and changes should remain inspectable after the immediate conversation ends.

## 2. Core research principle

**Source before synthesis. Evidence before confidence. Test before declaring success.**

The user's preferred pattern is:

**Evidence → hypotheses → tests → conclusions.**

The aim is not to avoid interpretation. It is to make interpretation traceable and correctable.

## 3. Epistemic vocabulary

The archive and future research should distinguish:

| Class | Meaning | Example of appropriate use |
|---|---|---|
| FACT / VERIFIED | Directly supported by reliable, inspectable evidence. | A repository file contains a particular function. |
| CLAIM / REPORTED | A person, organization, or source asserts something. | A project owner reports a metric or feature. |
| INTERPRETATION | A reasoned explanation of observed evidence. | A workflow design suggests an implicit trust boundary. |
| ASSUMPTION | A premise temporarily accepted for planning. | A service is assumed to expose a stable API until inspected. |
| HYPOTHESIS | A testable explanation or expected mechanism. | Adding clarification may reduce unsafe action proposals. |
| ANALOGY | A comparison that may help reasoning but is not evidence. | Comparing agent policy to an operating-system permission boundary. |
| PROPOSAL | A recommended design or future action. | Introduce a durable outbox for external side effects. |
| UNKNOWN | The evidence is absent or insufficient. | No independent evaluation result is available. |
| DISPUTED | Credible sources or observations conflict. | Vendor documentation and observed behaviour differ. |

Do not collapse these classes into a single confidence score. Confidence should be specific to a claim and its evidence.

## 4. Research unit and source chain

A useful research record links:

**Claim ↔ evidence ↔ source ↔ context ↔ status ↔ change history.**

A claim without source provenance should not be treated as verified. A source without a claim or question may be noise. A conclusion without change history can obscure why a position was revised.

Recommended source metadata:

- Source ID.
- Title and publisher or owner.
- URL or repository path.
- Source type.
- Publication date and observation date.
- Retrieval date.
- Primary, secondary, user-context, model-derived, or unknown provenance.
- Relevant claim IDs.
- Relevant project or decision.
- Trust level and known limitations.
- Whether the source was fully read, partially inspected, or only discovered.
- What would invalidate or supersede it.

## 5. Source hierarchy and discovery discipline

The user's global-intelligence research work distinguishes source quality and purpose.

A practical tiering system:

- **Tier 1 — Primary:** official regulator, government, standards body, company filing, technical documentation, repository source, dataset paper, or direct policy.
- **Tier 2 — Credible secondary:** reputable journalism, peer-reviewed synthesis, established technical analysis, or expert commentary with traceable evidence.
- **Tier 3 — Discovery:** social posts, newsletters, event listings, community discussions, or unverified announcements.

Tier 3 can reveal a lead, but should not silently become the evidence for a material conclusion. Verify against a primary source where possible.

Keep discovery coverage separate from retrieval coverage, date coverage, thematic coverage, and verification coverage. Finding a source does not mean it was read; reading it does not mean its claims were independently tested.

## 6. Research workflow

A recurring research operating procedure can be represented as:

1. **REGISTER** — define the question, scope, time range, and decision the research should inform.
2. **INGEST** — collect source records with provenance.
3. **EXTRACT CLAIMS** — identify factual, interpretive, and normative statements.
4. **CLASSIFY** — label evidence, claim type, source type, and confidence.
5. **LINK EVIDENCE** — connect claims to supporting and contradicting sources.
6. **COMPARE** — examine agreement, disagreement, mechanisms, context, and scope.
7. **RECORD CONTRADICTIONS** — preserve conflicts rather than selecting the most convenient source.
8. **PROPOSE DELTA** — describe what new understanding would change in the model, product, or decision.
9. **HUMAN REVIEW** — inspect consequential claims and actions.
10. **APPROVE** — authorize changes to canonical state.
11. **LINT** — check missing provenance, unsupported statements, stale claims, broken links, and unresolved contradictions.
12. **NEXT TEST** — turn unresolved uncertainty into a research question or experiment.

This workflow reflects the user's research-notebook approach. Its implementation status varies across the repositories and experiments mentioned in prior conversations.

## 7. Research protocol and iteration

The user has developed a multi-stage research protocol:

**Baseline → Discover → Diverge → React → Recombine → Critique → Converge → Reflect.**

Its role is to prevent premature convergence.

- **Baseline:** record current understanding, assumptions, known evidence, and unknowns.
- **Discover:** identify sources, perspectives, and mechanisms.
- **Diverge:** generate plausible explanations and alternatives.
- **React:** test interpretations against evidence and objections.
- **Recombine:** connect ideas across domains.
- **Critique:** expose weak assumptions, contradictions, and scope errors.
- **Converge:** state the most defensible conclusion and its limits.
- **Reflect:** record what changed and what should be tested next.

The stages are a research aid, not a claim that all discovery can be made fully deterministic.

## 8. The research notebook as persistent infrastructure

The user has repeatedly wanted a Project-style notebook with:

- Source registry.
- Claim ledger.
- Evidence map.
- Contradiction register.
- Experiment runbook.
- Individual experiment notes.
- Decision log.
- Action backlog.
- Change history.
- Coverage and lint reports.

A master research state should be a navigable index, not an unstructured essay. Each claim should have provenance and a current status. Each experiment should preserve its inputs, method, outcome, limitations, and next decision.

## 9. Experimental discipline

The user prefers reversible, high-information experiments. A useful experiment record includes:

- Research question.
- Hypothesis.
- Competing hypotheses.
- Target population or system.
- Dataset or source selection.
- Inclusion and exclusion criteria.
- Baseline.
- Intervention.
- Measurements.
- Safety and failure criteria.
- Sample limitations.
- Results.
- Interpretation.
- Alternative explanations.
- Decision.
- Next experiment.

Where the experiment is a software test, distinguish unit, integration, end-to-end, adversarial, hosted CI, security review, and user-pilot evidence.

A passing unit test does not prove production reliability. A synthetic benchmark does not prove real-world adoption. A single demonstration does not validate a general capability.

## 10. Research and implementation feedback

Research should not be isolated from implementation:

- A source may change a system requirement.
- An implementation failure may falsify an assumption.
- A pilot may expose a missing user context.
- A safety test may reveal an authority gap.
- A market signal may change a product priority.
- An external reviewer may show that a benchmark does not measure the intended capability.

The resulting evidence should update the claim ledger and decision record, not simply appear in a final narrative.

## 11. Frequent failure modes to guard against

- Treating search-result snippets as fully read sources.
- Treating a user-reported metric as independently verified.
- Confusing a dataset's language coverage with model performance.
- Confusing an architecture diagram with an implemented system.
- Treating mock executors as real actions.
- Treating a benchmark specification as a benchmark result.
- Selecting only sources that support the preferred hypothesis.
- Using one confidence score for several different uncertainties.
- Overstating generality from a small pilot.
- Hiding contradictions to create a cleaner narrative.
- Using old vendor documentation to make current capability claims.
- Presenting an inferred mechanism as a fact.

## 12. Current research priority

The main opportunity is to connect the user's high-level research method to a small number of independently inspectable, repeatable evidence pipelines. The strongest proof will come from research that changes a real decision, a product requirement, a safety boundary, or a measured outcome—and records exactly how it did so.
