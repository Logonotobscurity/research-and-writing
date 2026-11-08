# 06 — LOG_ON OS, Execution Kernel, and Agent Runtime

## 1. Architectural intent

The user's LOG_ON OS concept is a multi-agent business growth and operations system. Its purpose is to coordinate intelligence, strategy, demand, delivery, retention, measurement, and learning while keeping governance, security, and orchestration across the system.

The architecture is intended to be an execution platform, not a loose collection of chatbots. The user has described it as an **execution-kernel-based agent platform**.

The central invariant is:

> **Can do ≠ may do.**

A model may be technically capable of proposing an action. That does not establish that it is authorized to carry out the action.

## 2. Specification hierarchy

The known source-of-truth hierarchy is:

1. EXECUTION_KERNEL_SPEC
2. AGENT_RUNTIME_SPEC
3. TOOL_AND_MCP_SPEC
4. VOICE_VISION_SPEC
5. FRONTEND_ARCHITECTURE

The hierarchy expresses a deliberate design rule: user interface and tool presentation are projections of the underlying runtime and authority system, not substitutes for it.

## 3. Core runtime lifecycle

The recurring lifecycle is:

**INTAKE → CONTEXT / MEMORY → POLICY → ORCHESTRATOR → PLAN → PERMISSION → ACTION → VALIDATION → APPROVAL → EXECUTION → EVIDENCE / AUDIT → EVALUATION → LEARNING**

### Intake
Receive the user's request, identity, workspace, channel, and any structured input.

### Context and memory
Retrieve only relevant context with provenance, scope, freshness, and access controls. Memory should not become unrestricted authority.

### Policy
Apply deterministic business, security, privacy, and risk rules before an action is approved.

### Orchestration
Select an appropriate agent or capability, coordinate work, and preserve workflow state.

### Plan
Generate a proposed sequence of steps, required inputs, target systems, and expected side effects.

### Permission
Check whether the requesting principal, agent, and workflow are authorized for the exact action, target, scope, and data.

### Action
Prepare or invoke the eligible operation through an explicit capability boundary.

### Validation
Check schema, critical fields, business invariants, preconditions, and expected results.

### Approval
Obtain human approval for actions that require it. An approval should be bound to the specific proposal and its relevant context.

### Execution
Carry out the permitted action with idempotency, bounded retries, and traceability.

### Evidence and audit
Record what was proposed, authorized, executed, rejected, or left uncertain.

### Evaluation and learning
Measure outcome quality, policy correctness, user satisfaction, and failure patterns. Update future decisions only through controlled mechanisms.

## 4. Deterministic and probabilistic responsibilities

The design separates model reasoning from authoritative system controls.

### Model responsibilities
- Interpret user intent.
- Generate candidate plans.
- Summarize relevant context.
- Propose structured actions.
- Explain uncertainty.
- Ask for missing information.
- Assist with research and synthesis.

### Deterministic system responsibilities
- Identity and workspace authorization.
- Schema and contract validation.
- Policy enforcement.
- Capability permission checks.
- Approval requirements.
- Idempotency and replay handling.
- State transitions.
- Execution boundaries.
- Audit and evidence persistence.
- Verification of external side effects.

The model may propose. The policy and execution layers decide whether the proposal may proceed.

## 5. Core system boundaries

The architecture discussion identifies several boundaries that must remain explicit:

- Model versus deterministic policy.
- Agent versus tool.
- Tool registration versus tool authorization.
- Plan versus action.
- Approval versus execution.
- Internal state versus external side effect.
- User interface versus authoritative runtime.
- Read access versus write access.
- Reversible versus irreversible operation.
- Verified outcome versus uncertain outcome.

A permission should not be inferred from the existence of an integration or the agent's ability to call it.

## 6. Technology choices discussed

The stack described in prior architecture notes includes:

- Next.js and TypeScript for application and interface layers.
- Zod for schemas and boundary validation.
- PostgreSQL for authoritative state.
- Redis and BullMQ for operational queues and background work.
- LangGraph for orchestration where graph-based agent control is useful.
- MCP for tool connectivity, with explicit trust boundaries.
- OpenTelemetry and Langfuse for traces and model/agent observability.
- React, Tailwind, React Flow, and ELK.js for workflow and system visualization.

The user has specifically distinguished n8n from the core execution kernel: n8n may be useful for external workflow automation or integration, but it should not silently own core policy and execution logic.

These are architecture choices and design intentions in the available record. They should be verified against the current repository before being described as the active production stack.

## 7. Data and state principles

- PostgreSQL should be authoritative for canonical application state.
- Redis and BullMQ are operational infrastructure, not the source of truth.
- Agents should be replaceable without changing stable business contracts.
- Every workflow should have explicit lifecycle state.
- Tool calls should be represented with input, authority, result, and evidence.
- Retries should be safe and idempotent where possible.
- The system should not silently turn an error or unknown external outcome into success.
- State changes should be traceable to a principal, policy decision, approval, and event.

## 8. Tool and MCP handling

MCP servers and external tools must be treated as trust boundaries.

Before a tool is made available to an agent, the platform should inspect:
- Identity and provenance of the tool provider.
- Declared capabilities and actual behaviour.
- Read/write scope.
- Data transmitted and received.
- Credential access.
- Network and filesystem access.
- Side effects and reversibility.
- Failure and retry behaviour.
- Tool-output trust.
- Logging and auditability.

Tool discovery is not authorization. A tool description is not proof that the tool is safe. Tool output should be treated as untrusted data until validated.

## 9. User interface principle

The user has stated the design rule:

**UI is projection of system, not runtime.**

The interface may visualize:
- Current workflow state.
- Agent plan and rationale.
- Required information.
- Permission and approval state.
- Execution progress.
- Evidence and result.
- Errors and recovery actions.

But the UI should not be the sole location where consent, permission, or execution logic is enforced. An endpoint must not be able to bypass the underlying kernel simply because a button is hidden or disabled.

## 10. Failure model

The runtime should distinguish at least:

- Model failure.
- Tool failure.
- Policy rejection.
- Permission denial.
- Validation failure.
- Timeout.
- External-system failure.
- Human rejection.
- Partial side effect.
- Unknown outcome.
- Duplicate or replay attempt.
- Cancellation.
- Compensation or rollback failure.

A critical rule is that an unknown outcome must not be represented as success. If an external request times out after the remote service may have accepted it, the system must reconcile before blindly retrying.

## 11. Product and workflow implications

The same execution kernel can support multiple business workflows, but each capability still needs a defined contract.

A workflow specification should include:
- Business purpose.
- Actor and principal.
- Input schema.
- Required context.
- Permission policy.
- Risk classification.
- Preconditions.
- Side effects.
- Human approval conditions.
- Execution adapter.
- Verification method.
- Idempotency strategy.
- Failure and recovery behaviour.
- Audit record.
- Success criteria.

## 12. Open design questions

1. Which policy decisions are global, tenant-specific, or workflow-specific?
2. How are policy versions bound to plans and executions?
3. How are delegated agents prevented from escalating authority?
4. How are stale approvals and changed proposals invalidated?
5. How are partial side effects reconciled?
6. How do retries behave across services that lack idempotency support?
7. What data may enter memory, for how long, and under whose authority?
8. How are tool changes and supply-chain risks continuously monitored?
9. How is learning evaluated without allowing unreviewed state changes to redefine policy?

## 13. Current working conclusion

LOG_ON OS is best understood as an execution and coordination platform in which models contribute intelligence but deterministic boundaries govern authority, state, side effects, and evidence. The strongest architecture will make those boundaries enforceable at service level, not merely visible in a dashboard.
