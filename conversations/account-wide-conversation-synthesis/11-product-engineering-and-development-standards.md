# 11 — Product Engineering and Development Standards

## 1. The user's product-development expectation

Across product audits and development prompts, the user consistently asks for more than a concept description, feature list, or polished interface. The intended output should define a usable product from the human problem through the engineering and adoption requirements.

The user frequently asks the assistant to operate across the responsibilities of:
- Principal Product Strategist.
- Product Manager.
- UX Researcher.
- Service Designer.
- Solutions Architect.
- Business Analyst.
- Behavioural Designer.
- Product Operations.
- Senior full-stack engineer.

This is a way to force a complete view of the system, not a request to claim credentials or to skip specialist review.

## 2. End-to-end product chain

The user's recurring product framework is:

**Human Need → Business Need → Context → Behaviour → Workflow → Product → Implementation → Adoption → Outcome → Scale.**

Each stage should have a clear answer.

### Human need
What job, problem, constraint, or desired outcome exists for the person using the product?

### Business need
Why does the organization need to solve it? What value, cost, risk, or strategic outcome is involved?

### Context
Where does the problem occur? What systems, devices, language, data, environment, incentives, and constraints shape it?

### Behaviour
What do users actually do, what do they avoid, and what causes them to trust, abandon, approve, or reject the workflow?

### Workflow
What happens before, during, and after the main task? What are the branches, handoffs, exceptions, and recovery states?

### Product
What is the smallest coherent product that addresses the real need? What is in scope and out of scope?

### Implementation
What contracts, data models, APIs, permissions, services, interfaces, jobs, and tests are necessary?

### Adoption
How will users discover, understand, trust, learn, and continue using the product?

### Outcome
What observable change should occur? How is the baseline established and the result measured?

### Scale
What must change when usage, data, customers, risk, or operational complexity grows?

## 3. Expected specification contents

A full-stack product specification should usually contain:

1. Product thesis and problem statement.
2. Target users, buyers, operators, and affected parties.
3. Context and user research assumptions.
4. Primary and secondary jobs-to-be-done.
5. User journeys and service blueprint.
6. Information architecture.
7. Functional requirements.
8. Non-functional requirements.
9. Data model and ownership.
10. API contracts and event flows.
11. Authentication, authorization, and tenancy.
12. Privacy and data lifecycle.
13. Agent and tool boundaries, where applicable.
14. Workflow state machine.
15. Approval and rejection behaviour.
16. Empty, loading, error, timeout, retry, and recovery states.
17. Observability and audit.
18. Accessibility and responsive behaviour.
19. Acceptance criteria.
20. Test strategy.
21. Deployment and operations.
22. Adoption plan.
23. Outcome metrics and instrumentation.
24. Open decisions and explicit assumptions.

Not every MVP needs a large implementation. It does need a coherent contract for the behaviours it claims to support.

## 4. Behavioural analysis

The user has emphasized that product development must account for real-world use rather than feature completion alone.

For consequential workflows, specify:
- What the user intends.
- What information they understand.
- What they may misunderstand.
- What they must confirm.
- What they expect the system to remember.
- What they expect the system to forget.
- Which actions feel reversible.
- Which actions require consent or approval.
- What happens when they change their mind.
- How they recover from an error.
- What feedback helps them understand the state.

The product should not assume that users behave like the developer expects. Behavioural assumptions should be tested through observation or a pilot.

## 5. MVP discipline

An MVP is not a visually complete prototype with critical actions simulated.

A credible MVP should have:
- One clearly defined user problem.
- A complete happy path for the chosen scope.
- Real persistence for canonical state.
- Real authentication and authorization.
- Explicit failure states.
- Appropriate privacy and security boundaries.
- Real integrations for any function advertised as operational.
- Verification for consequential side effects.
- Tests covering the essential contract.
- Instrumentation to learn from actual use.

Features that remain mocked, simulated, or manual should be labelled honestly.

## 6. Engineering principles

### Contracts before interface assumptions
Define data schemas and service contracts before allowing the UI to become the source of business truth.

### Clear ownership
Every piece of state should have an authoritative owner. Do not let browser state, caches, and databases become competing sources of truth.

### Deterministic policy
Keep permissions, business rules, money calculations, consent, and safety gates outside free-form model reasoning.

### Fail visibly
The product should not show success when an operation failed, timed out ambiguously, or was not verified.

### Real integrations
Use adapter boundaries, but do not replace unfinished integrations with mock success while describing the feature as complete.

### Observability
Record enough structured evidence to diagnose and evaluate the workflow while protecting sensitive data.

### Reversibility
Prefer reversible actions and explicit confirmation where possible. Provide cancellation, compensation, or recovery when side effects cannot be reversed.

### Replaceable intelligence
Models and providers should be replaceable behind stable product and workflow contracts.

## 7. UI and product behaviour

The user's design and architecture discussions include a strong separation between interface and runtime.

The UI should display:
- User context.
- Workflow state.
- Available actions.
- Required input.
- Approval requests.
- Progress.
- Errors.
- Evidence and outcomes.

It should not be the only enforcement point for:
- Authentication.
- Authorization.
- Consent.
- Tenant isolation.
- Data access.
- Policy.
- External side effects.

A disabled button is not a security control if the API endpoint remains unprotected.

## 8. AI product requirements

Where a product includes an LLM or agent, additionally specify:
- Model purpose and limits.
- Input sources and provenance.
- Context construction.
- Untrusted input boundaries.
- Prompt and tool injection risks.
- Retrieval quality and freshness.
- Structured output validation.
- Confidence and uncertainty representation.
- Clarification conditions.
- Human escalation.
- Policy enforcement.
- Evaluation datasets and baselines.
- Provider fallback behaviour.
- Cost and latency constraints.
- Data retention and provider sharing.
- Model/version change management.

Do not use an LLM where a deterministic rule, database query, or conventional workflow is more reliable and less costly.

## 9. Development prompts and agent handoff

The user wants development prompts that can guide an engineer or coding agent without relying on vague role-play.

A strong handoff should specify:
- Repository and branch assumptions.
- Source-of-truth documents.
- Exact scope.
- Files or subsystems involved.
- Constraints and invariants.
- Required implementation behaviour.
- Forbidden shortcuts.
- Test and validation commands.
- Acceptance criteria.
- Expected evidence.
- Rollback and failure behaviour.
- Definition of done.

Avoid instructing a coding agent merely to “make it production-ready” without defining what production readiness means for the specific system.

## 10. Audit method

A repository audit should answer:

1. What does the product currently claim to do?
2. Which behaviours exist in the code?
3. Which services are real, stubbed, mocked, or missing?
4. What tests cover them?
5. Which tests were actually run and in what environment?
6. What security and privacy boundaries are enforced?
7. Which user journeys work end to end?
8. What remains unimplemented?
9. What is the highest-risk gap?
10. What is the smallest testable next change?

Every finding should link to an inspectable file, test, endpoint, run, or observed behaviour where possible.

## 11. Evidence of development quality

Use separate evidence levels:
- Source inspection.
- Static checks.
- Unit tests.
- Integration tests.
- End-to-end tests.
- Hosted CI.
- Security tests.
- Independent review.
- User pilot.
- Production monitoring.
- Commercial outcomes.

Do not let success at one level imply success at the next.

## 12. Current working conclusion

The user's product standard is grounded engineering: understand the human and business problem, model real behaviour, define the workflow, build a coherent and secure system, verify that it works, and measure whether people receive the intended value.
