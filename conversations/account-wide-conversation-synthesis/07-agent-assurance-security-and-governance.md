# 07 — Agent Assurance, Security, and Governance

## 1. Why assurance is a separate workstream

The user's agent architecture is concerned with both capability and authority. This creates a distinct assurance requirement: an agent system should be evaluated not only for whether it completes tasks, but whether it stays within its permissions, resists misuse, preserves traceability, and reports outcomes honestly.

The user has explored Agent Assurance as a LOG_ON capability and as part of the broader execution-kernel platform.

## 2. Governing principle

**Can do ≠ may do.**

A model's ability to formulate or invoke an action does not create authority. Every consequential operation needs an explicit principal, scope, policy decision, and traceable outcome.

## 3. Assurance model

The recurring assurance areas include:

1. **Use-case definition:** identify the intended task, users, data, actions, and consequences.
2. **Threat modelling:** map assets, actors, trust boundaries, attack paths, abuse cases, and failure modes.
3. **Capability inventory:** identify all available tools, permissions, side effects, and external dependencies.
4. **Identity and permissions:** bind actions to principals, tenants, roles, and scopes.
5. **Prompt and context injection:** test whether untrusted instructions can alter system behaviour or authority.
6. **Credential and data access:** verify least privilege, secret handling, data minimization, and tenant isolation.
7. **Approval and oversight:** enforce human review where risk and policy require it.
8. **Traceability:** link requests, plans, policies, approvals, tool calls, results, and final outcomes.
9. **Rollback and recovery:** provide cancellation, compensation, kill switches, and reconciliation paths.
10. **Supply-chain security:** inspect agents, tools, MCP servers, dependencies, and model/service changes.
11. **Monitoring:** observe failures, suspicious activity, policy violations, drift, and new attack patterns.
12. **Go-live decision:** record residual risk, responsible owner, evidence, and conditions for release.

## 4. Audit-as-Code direction

The user has explored a model in which assurance is expressed as executable, reviewable policy and test artifacts rather than a one-time prose assessment.

Potential components:
- Agent Registry.
- Tool and capability inventory.
- Machine-readable policies.
- Adversarial test suites.
- Synthetic or LOG_ONLY monitoring targets.
- Sandboxed execution.
- Evidence collection.
- Human review and sign-off.
- Runtime monitoring.
- Controlled promotion from observation to enforcement.

The user has discussed WASM/WASI sandboxing as one possible isolation mechanism. It should not be assumed that all production workloads already run in a sandbox.

## 5. Assurance lifecycle

A practical review sequence:

1. Define use case and intended users.
2. Identify assets and data flows.
3. Map trust and authority boundaries.
4. Build threat model and misuse cases.
5. Inventory capabilities and permissions.
6. Test prompt/context/tool injection.
7. Test privacy and cross-tenant isolation.
8. Test approval integrity and state transitions.
9. Test side-effect and retry behaviour.
10. Review audit and observability.
11. Record residual risk and release decision.
12. Monitor and re-evaluate as the system changes.

## 6. Adversarial cases that matter

The prior work includes an adversarial case set and research notes. The case families described in the available context include:

- Forged approval.
- Stale approval.
- Approval for a different action or target.
- Cross-tenant access.
- Direct service or endpoint bypass.
- Prompt injection.
- Malicious tool output.
- Unauthorized external write.
- Unauthorized financial action.
- Duplicate or replayed operation.
- Race condition.
- Partial side effect.
- Retry after ambiguous timeout.
- Verification failure.
- Incorrect success reporting.
- Credential leakage.
- Excessive data access.
- Agent capability escalation.
- Tool supply-chain compromise.
- Missing audit evidence.

These are test targets, not claims that the system has already passed them.

## 7. Core invariants and proposed acceptance criteria

The user's assurance direction includes requirements such as:

- Zero unauthorized external or financial writes.
- Zero cross-workspace execution.
- Replay protection.
- Traceability for consequential operations.
- Rejection of stale or mismatched approvals.
- Verification failure must never be represented as success.
- Tool discovery must not grant permission.
- Destructive actions must be blocked or require explicit, policy-defined approval.
- Policy decisions must be explainable and recorded.

These are target criteria. They must not be written as achieved results until the corresponding tests have run against the actual implementation.

## 8. Permission and approval semantics

A meaningful approval should bind to:
- The approving principal.
- The exact proposed action.
- Target system and object.
- Relevant input values.
- Data scope.
- Risk and side-effect description.
- Policy version.
- Expiry and freshness conditions.
- Whether the proposal changed after approval.

An approval for one proposal should not be reused for a materially changed proposal. A user clicking “approve” in a UI is not sufficient if the backend cannot validate the approval's identity, scope, freshness, and integrity.

## 9. Observability and evidence

For each consequential action, a trace should connect:
- User request.
- Authenticated identity.
- Context references.
- Model or agent proposal.
- Policy result.
- Permission decision.
- Approval event, where required.
- Tool and executor identity.
- Request payload or secure reference.
- External result.
- Verification result.
- Final user-facing claim.

Sensitive values should be protected. Auditability does not require indiscriminate storage of secrets or full personal data. Retention, redaction, access control, and deletion policies remain necessary.

## 10. Assurance versus compliance

The archive should not describe the system as “certified,” “compliant,” or “secure” merely because it includes an assurance framework. Formal compliance depends on the relevant jurisdiction, scope, controls, evidence, independent assessment, and current requirements.

The term **Agent Assurance** here describes the intended engineering and governance capability. It does not imply a certification or third-party attestation.

## 11. Current evidence limitations

The prior project notes describe:
- Specifications and assurance modules.
- Adversarial case definitions.
- A registry and policy direction.
- A local synthetic/LOG_ONLY evaluation idea.
- Some implementation and testing discussions.

They also record gaps at different points, including incomplete end-to-end executors, incomplete hosted evaluation, and missing independent assurance. The exact present state must be re-inspected in the relevant repository before making a current implementation claim.

No security certification or independent penetration-test result is established by this archive.

## 12. Open questions

1. How will assurance policies be versioned and promoted?
2. What is the minimum viable agent registry?
3. How will sandbox limits be enforced across CPU, memory, network, filesystem, and credentials?
4. How will the system reconcile ambiguous external outcomes?
5. How will high-impact action approval be made accessible without weakening authority?
6. What telemetry is required while minimizing personal-data retention?
7. How will assurance results be compared across different model and tool versions?
8. What constitutes acceptable residual risk for a real customer deployment?

## 13. Current working conclusion

Agent Assurance should be treated as a continuous engineering lifecycle: define authority, test misuse, observe behaviour, preserve evidence, and revisit the decision as the system changes. The strongest assurance claim will be one supported by reproducible tests and operational evidence, not by the presence of a policy document or dashboard.
