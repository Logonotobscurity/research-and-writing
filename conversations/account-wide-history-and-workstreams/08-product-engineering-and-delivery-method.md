# 08 — Product Engineering, Specifications, Audits, and Delivery Method

## 1. Product-development expectation

Across product conversations, the user has asked for a disciplined approach combining product strategy, research, user experience, service design, business analysis, behavioural analysis, architecture, product operations, and engineering. The goal is a product that solves a real problem and can be implemented—not merely polished positioning or a feature list.

The recurring chain is:

**Human Need → Business Need → Context → Behaviour → Workflow → Product → Implementation → Adoption → Outcome → Scale.**

## 2. Perspectives expected in a serious product audit

Reason across the responsibilities of Principal Product Strategist, Product Manager, UX Researcher, Service Designer, Enterprise/Solution Architect, Business Analyst, Behavioural Designer, Product Operations, and Senior Full-Stack Engineer. These are review perspectives, not a claim that one document replaces specialist review.

## 3. Product definition sequence

### Human and business need
Identify who experiences the problem, what they are trying to do, why current alternatives fail, who pays, and what outcome matters.

### Context
Map environment, devices, connectivity, accessibility, culture, regulation, trust, time pressure, and existing tools.

### Behaviour
Describe triggers, decisions, barriers, incentives, mistakes, recovery behaviour, and edge cases. Do not design only for an ideal user following the happy path.

### Workflow
Map the actual sequence from initiation to completion, including waiting, handoffs, exceptions, retries, escalations, and approvals.

### Product
Define the core job, value proposition, boundaries, feature priority, non-goals, monetisation assumptions, and adoption path.

### Implementation
Translate the product into data models, APIs, state transitions, permissions, UI surfaces, background jobs, observability, tests, and deployment needs.

### Adoption and outcomes
Define onboarding, activation, retention, support, success measures, and evidence that the product improves the original situation.

## 4. Development artefacts expected

A robust specification set may include:
- Product brief and problem definition.
- User and stakeholder research.
- Jobs-to-be-done and behavioural analysis.
- User roles and permission model.
- Service blueprint and workflow diagrams.
- Functional and non-functional requirements.
- Information architecture and navigation.
- Interaction, state, and error specifications.
- Domain model, database schema, and API contracts.
- Authentication, authorisation, and privacy model.
- Agent and automation runtime design where relevant.
- Retry, recovery, audit, and observability requirements.
- Threat model and abuse cases.
- Accessibility, responsiveness, and performance criteria.
- Test strategy and acceptance criteria.
- Deployment, backup, operations, and rollback.
- MVP boundary and post-MVP roadmap.

## 5. Audit protocol

A serious audit should:
1. Inspect the actual repository and current branch.
2. Read source-of-truth documents.
3. Trace requirements to implemented code.
4. Run or inspect tests and CI results.
5. Identify missing workflows and unhandled states.
6. Review permissions, secrets, data access, and external effects.
7. Test realistic user journeys.
8. Separate code defects from product-design gaps.
9. Prioritise by user impact, business impact, probability, and repair cost.
10. Define a fix and how it will be verified.

Do not claim a fix was applied unless a write or code change was actually made and confirmed. Do not infer current repository state from a README alone.

## 6. MVP discipline

An MVP is the smallest complete experience capable of validating the core value. It must include enough workflow, reliability, feedback, and operational control to be usable in its intended setting. A feature demonstration is not an MVP when critical states, data ownership, error handling, onboarding, or approval behaviour are missing.

## 7. Human approval and side-effect boundaries

For agentic systems, GigPilot, memory products, and voice-to-action, distinguish:
- Read-only analysis.
- Draft generation.
- Proposed external action.
- Human-approved action.
- Automated execution within a narrow, authorised scope.

For high-impact or externally visible actions, draft-and-review is a safer default than ungoverned auto-execution. Exact approval rules must follow risk and user authority.

## 8. Developer handoff

A strong engineering prompt should define repository and branch assumptions, scope and non-goals, architecture constraints, source-of-truth documents, required files, data/API contracts, security boundaries, test commands, acceptance criteria, evidence to report, and rollback.

Avoid instructions such as “build everything” without staged implementation and verification.

## 9. Design preferences

A recurring LOG_ON visual direction:
- Ivory `#F5EDD4`; dark `#141412`; purple `#9B78E8`; teal `#1A5C48`.
- Cormorant Garamond and DM Sans.
- VisionOS-inspired cards and fintech-editorial layouts.
- Basquiat-inspired visual energy for GigPilot.

These are creative preferences, not fixed requirements for every product. Each product needs context-specific research, accessibility, and usability review.

## 10. Current conclusion

Start with problem and context investigation; define user behaviour and workflow; establish product boundaries and authority; then design, implement, and validate. Every important requirement should connect to a test or observable outcome.
