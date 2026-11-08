# 04 — Agent Systems, Runtime Architecture, and AI Assurance

## 1. Architectural direction

The user has repeatedly developed an agent-platform architecture in which the interface is not the runtime itself. A central principle is:

> **The UI is a projection of the system, not the runtime.**

The runtime should own orchestration, state, policy, permissions, execution, validation, audit, and recovery. The interface should expose understandable status, evidence, approvals, and controls without becoming the source of authority.

A second principle is:

> **Can do ≠ may do.**

A model or tool may technically be able to perform an action. That does not mean the system is authorised to perform it in the current context.

## 2. Specification hierarchy

The user's source-of-truth chain is:

`EXECUTION_KERNEL_SPEC`  
→ `AGENT_RUNTIME_SPEC` + `TOOL_AND_MCP_SPEC`  
→ `VOICE_VISION_SPEC`  
→ `FRONTEND_ARCHITECTURE`

The intention is to establish execution and safety invariants before designing the experience layer. This reduces the risk of implementing a convincing interface over an underspecified runtime.

## 3. Runtime lifecycle

A recurring lifecycle is:

**Intake → Memory → Policy → Orchestrator → Plan → Permission → Action → Validation → Approval → Execution → Audit → Evaluation → Learning.**

- **Intake:** request, actor, context, and objective.
- **Memory:** relevant context subject to access, provenance, and retention rules.
- **Policy:** evaluate what is allowed.
- **Orchestrator:** select an appropriate plan or agent.
- **Plan:** describe intended actions and dependencies.
- **Permission:** check identity, scope, authority, and capability.
- **Action / validation:** validate tool arguments and preconditions.
- **Approval:** obtain a human decision where required.
- **Execution:** perform and record permitted operations.
- **Audit:** preserve a trace of inputs, decisions, and effects.
- **Evaluation:** measure correctness, safety, and outcomes.
- **Learning:** update through controlled processes.

The exact order can be adapted to a product, but the boundaries must remain explicit.

## 4. Technology choices discussed

The retained stack references include Next.js, TypeScript, Zod, PostgreSQL, BullMQ, Redis, LangGraph, MCP, OpenTelemetry, Langfuse, React, Tailwind, React Flow, ELK.js, and WASM/WASI sandboxing.

n8n was discussed as useful for integrations and automation, but not as the core execution logic for the agent runtime. The distinction is between workflow integration and a controlled runtime with durable state and explicit policy.

These are architecture choices and proposals from prior discussions, not a claim that every component is currently deployed in a single production system.

## 5. Tool and MCP governance

A robust tool system should document:
- Tool identity and provenance.
- Input and output schemas.
- Authentication and credential boundaries.
- Permitted read/write operations.
- Data that may be accessed.
- Side effects and reversibility.
- Rate limits and failure behaviour.
- Human approval requirements.
- Logging, audit fields, and versioning.
- Supply-chain and dependency risk.

Validate arguments, reject out-of-scope actions, isolate untrusted content, and prevent retrieved documents or tool responses from redefining system authority.

## 6. AI Agent Assurance

The assurance direction includes **Audit-as-Code**, an agent and tool registry, controlled sandboxing, and synthetic LOG_ONLY targets.

Recurring review modules:
1. Use-case definition and intended outcome.
2. Threat model and misuse scenarios.
3. Capability and boundary testing.
4. Prompt and context injection testing.
5. Identity and permission review.
6. Credential and sensitive-data access review.
7. Traceability and audit completeness.
8. Approval and human-oversight design.
9. Rollback and kill-switch readiness.
10. Dependency and supply-chain review.
11. Go-live decision and post-deployment monitoring.

A successful demonstration is not enough to establish safe operational behaviour. The review must assess both capability and authority.

## 7. Assurance principles

- Least privilege by default.
- Separate planning from execution.
- Treat retrieved content as data, not instructions.
- Apply stronger controls to irreversible or high-impact actions.
- Make approvals specific and meaningful.
- Preserve provenance and traceability.
- Design rollback and kill-switch controls before deployment.
- Do not equate confident model output with verified fact.
- Evaluate misuse resistance and recovery, not just nominal task success.

## 8. Global AI Business Intelligence Agent

A Global AI Business Intelligence Agent was discussed as a strategic system, with OpenServ mentioned as a planned direction. The desired boundary is controlled repository interaction: safe edits, explicit diff review, bounded permissions, and rollback rather than unrestricted autonomous modification.

Its intended role is to connect opportunity intelligence, research, strategic interpretation, and operational action. The precise integration and current implementation status are unknown here.

## 9. Open design questions

- Which actions require approval, and at what risk tier?
- How are delegated permissions scoped and revoked?
- How are cross-agent identities and tool provenance represented?
- How are memory reads and writes governed?
- How are traces tied to business outcomes?
- What is the recovery plan for partial execution and retries?
- How are agent upgrades and policy changes tested before release?

These questions belong in product-specific source-of-truth specifications and tests, not only in general architecture prose.
