# 15 — Forward Research Agenda and Priorities

## 1. Purpose

This document turns the archive's open questions into a practical forward agenda. It does not assume that every project should proceed at once or that the user has approved every item as the next priority.

The agenda is organized around evidence that would materially improve decisions: source fidelity, customer proof, execution safety, multilingual evaluation, portfolio health, and intelligence-to-action quality.

## 2. Priority 1 — Make the conversation archive a dependable research record

### Why this matters

The repository now contains a useful account-wide synthesis, focused conversation folders, thematic documents, product dossiers, and maintenance rules. However, the source available for this initial archive was conversation context, saved memory, recent-conversation summaries, and inspected repository material—not a complete raw export of every message.

### Recommended work
1. Ingest available raw conversation exports where they can be obtained.
2. Establish stable source IDs for conversations, messages, project notes, and repository artefacts.
3. Attach exact dates and direct quotations only where source text exists.
4. Link each substantive claim to its source and current status.
5. Record corrections, reversals, disagreements, and superseded decisions as dated changes.
6. Maintain a missing-source register.
7. Compare project dossiers with current source-of-truth repositories and specifications.

### Success evidence
A future reader can trace a material claim to its original conversation or project source and can distinguish what was said, inferred, proposed, implemented, and measured.

## 3. Priority 2 — Establish one repeatable commercial proof for LOG_ON

### Why this matters

The LOG_ON strategy spans a broad technical and operational vision. A narrower commercial proof can show that the operating approach solves a real problem, earns customer trust, and produces measurable value.

### Recommended work
1. Select one target segment and one recurring business workflow.
2. Interview or observe real operators before fixing the product scope.
3. Record the current baseline: time, cost, response, conversion, quality, or customer experience.
4. Design the smallest workflow that can be deployed safely.
5. Identify human approvals, data access, retention, and external side effects.
6. Run a bounded pilot with a real customer.
7. Record implementation effort, operating cost, failures, support burden, and measured outcomes.
8. Obtain permission before publishing any customer identity, testimonial, or case-study material.

### Success evidence
A documented before-and-after case with a credible baseline, real deployment, observed use, customer feedback, cost to deliver, and clear limitations. A landing page, demo, prospect list, or pricing proposal alone is not sufficient proof.

## 4. Priority 3 — Validate the execution kernel at the service boundary

### Why this matters

The agent architecture's key invariant—**Can do ≠ may do**—must hold even when a UI is bypassed, a tool response is malicious, an approval is stale, or an external operation has an ambiguous result.

### Recommended work
1. Inspect the current repository implementation and identify the actual enforcement points.
2. Test identity and workspace isolation.
3. Attempt direct-service bypass of UI approval controls.
4. Test forged, stale, mismatched, and replayed approvals.
5. Test concurrent and duplicate requests.
6. Simulate partial external side effects and timeouts.
7. Verify idempotency, reconciliation, and recovery.
8. Confirm that verification failure or an unknown outcome is never reported as success.
9. Ensure every consequential operation has a trace linking request, principal, plan, policy, permission, approval, executor, external result, and verification.
10. Record the exact test environment and evidence.

### Success evidence
Reproducible adversarial test results against real service boundaries, with no unauthorized writes or cross-tenant execution in the defined test scope. Passing a specification review or isolated unit test is not enough.

## 5. Priority 4 — Turn PAL and voice research into reproducible evaluation

### Why this matters

The PAL direction seeks to preserve meaning in multilingual and culturally situated interaction. Claims about language coverage, contextual interpretation, or safe action must be demonstrated with valid data and independent review.

### Recommended work
1. Inventory actual datasets, licensing, published splits, schema, collection conditions, and limitations.
2. Ensure benchmark loaders use the published schema and fail closed when assumptions are not met.
3. Remove mock or placeholder evaluation paths from any reported benchmark result.
4. Have Yoruba/Pidgin examples and interpretations reviewed by qualified native speakers.
5. Record disagreement between annotators instead of hiding it.
6. Separate ASR, code-switch identification, pragmatic meaning, slot extraction, policy, and execution performance.
7. Compare generic, literal-translation, retrieval, naive-culturalization, and PAL conditions.
8. Measure unnecessary culturalization and false demographic inference as failure modes.
9. Define and adjudicate the unsafe-action endpoint before reporting a rate.
10. Publish datasets, prompts, code, and results only where rights and privacy permit.

### Success evidence
A reproducible evaluation with explicit data provenance, baselines, annotation method, limitations, and independent review. A benchmark specification or small unvalidated pilot is not evidence of broad capability.

## 6. Priority 5 — Reassess product portfolio maturity and focus

### Why this matters

The portfolio contains products, platform components, research programmes, prototypes, and historical ideas. They should not all be treated as equally mature or equally active.

### Recommended work
For each product:
1. Inspect the current repository and branch.
2. Identify the source-of-truth specification.
3. Trace the principal user journey end to end.
4. Mark each feature as implemented, partial, mocked, manual, or missing.
5. Run the appropriate tests and inspect hosted CI.
6. Review security, privacy, data lifecycle, and permissions.
7. Identify current users and actual repeat use.
8. Confirm metrics at the source.
9. Decide whether to proceed, test, pause, merge, or archive.
10. Record the next decision and its evidence threshold.

### Suggested order of audit
Prioritize products with an identifiable real user, reachable pilot participants, reusable infrastructure, and a measurable task. Do not prioritize solely by technical novelty or the amount of documentation already written.

### Success evidence
A concise, source-backed portfolio register with current maturity, actual evidence, largest risk, and an explicit next decision for each active workstream.

## 7. Priority 6 — Improve intelligence-to-decision quality

### Why this matters

Global BI and opportunity scanning should reduce uncertainty and help people make decisions. A large feed of links does not necessarily produce value.

### Recommended work
1. Choose a manageable set of opportunity categories and target markets.
2. Define authoritative sources for each category and country.
3. Capture publication date separately from event date and deadline.
4. Verify eligibility and application status against official sources.
5. Record the exact claim each source supports.
6. Explain the market or strategic implication.
7. Link a verified opportunity to one actionable next step.
8. Track whether the user accepts, rejects, applies, or defers the recommendation.
9. Measure precision, duplicate rate, eligibility correctness, time-to-decision, and actions completed.
10. Update the ranking model from observed outcomes rather than preference alone.

### Success evidence
A smaller set of verified signals that reliably supports decisions, with an audit trail from source to outcome.

## 8. Priority 7 — Mature the memory and consent product family

### Why this matters

ContextPocket, Re:Mind Me, and MorrowVoice explore related context and memory problems but have different principals, users, and authority models.

### Recommended work
- Define which records are local, personal, shared, or canonical project state.
- Establish provenance, freshness, correction, export, deletion, and retention.
- Verify real OAuth and platform sync rather than relying on proposed access.
- Test access control and tenant boundaries.
- Ensure consent is enforced in backend services and storage, not only represented in UI.
- Distinguish the person whose data is processed from the operator or device owner.
- Validate deletion across derived data and backups.

### Success evidence
A tested data lifecycle with user-visible controls and service-level enforcement of authority, retention, and revocation.

## 9. Decision discipline across all priorities

For every new initiative, ask:

1. What is the decision this work should improve?
2. What do we know, and how do we know it?
3. What is the main uncertainty?
4. What evidence would change the current decision?
5. What is the smallest reversible test?
6. What will count as a failure?
7. Who has authority to approve the next action?
8. How will the result be verified?
9. What should be learned or updated?
10. What work should be deferred to protect focus?

## 10. Suggested sequencing

A practical sequence is:

| Sequence | Focus | Reason |
|---|---|---|
| 1 | Preserve source and project context | Prevents future work from repeating or misrepresenting earlier decisions. |
| 2 | Select one commercial proof workflow | Creates external evidence and sharper product priorities. |
| 3 | Validate critical execution-kernel invariants | Establishes trust before broader autonomy. |
| 4 | Run one reproducible PAL/voice evaluation | Tests a distinctive research capability with real evidence. |
| 5 | Audit product portfolio and select pilots | Directs limited engineering time toward the strongest proof opportunities. |
| 6 | Improve intelligence-to-action tracking | Ensures research produces decisions and outcomes. |

This ordering is a recommendation, not a commitment. The user may reorder it based on new evidence, deadlines, customer access, or available resources.

## 11. Review cadence

At each meaningful project milestone, update:
- What changed.
- Why it changed.
- Evidence observed.
- Claims strengthened or weakened.
- Remaining unknowns.
- Risks and side effects.
- Next decision.
- What should be stopped, paused, or expanded.

Do not create repetitive status reports that add no new evidence or decision value.

## 12. Closing principle

The most useful next step is not necessarily to build another system. It is to produce evidence that makes an important decision clearer: a customer outcome, a verified safety property, a reproducible language result, a dependable memory lifecycle, or a signal that leads to a real action.

The recurring loop remains:

**Investigate → understand → define → architect → build → integrate → verify → learn.**
