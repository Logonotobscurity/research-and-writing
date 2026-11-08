# 13 — Integrations, Tools, and Platform Workflow Decisions

## 1. Why this is a separate topic

The user repeatedly explores how existing services, APIs, agents, and workflow tools can be connected into a coherent product. Integration is both a technical interest and an architectural concern.

A connected workflow is not simply a chain of API calls. It needs identity, permissions, data contracts, error handling, retries, observability, and a clear source of truth.

## 2. Integration principle

**Connection does not equal authorization. Registration does not equal trust. A successful request does not always equal a verified outcome.**

Every integration should specify:
- Provider and version.
- Authentication method.
- Permissions and scopes.
- Data exchanged.
- Side effects.
- Rate and resource limits.
- Error and timeout behaviour.
- Retry and idempotency strategy.
- Security and privacy requirements.
- Evidence and observability.
- Revocation and recovery.

## 3. MCP

MCP appears across the user's work as a common tool and context interface.

The user's design direction is to treat external MCP servers as untrusted boundaries until inspected. A server's advertised capabilities are not sufficient proof of its actual behaviour or security.

Review areas include:
- Server identity and provenance.
- Tool schemas.
- Read and write capabilities.
- Credentials and scopes.
- Network and filesystem access.
- Prompt injection through tool descriptions and outputs.
- Data exfiltration.
- Side effects.
- Audit and logging.
- Version and supply-chain changes.

MCP should not become a way to bypass the execution kernel or grant authority simply because a tool is discoverable.

## 4. Zapier and workflow automation

A recent discussion referenced the Zapier MCP connection endpoint:

https://mcp.zapier.com/api/v1/connect

The user has explored Zapier as an integration layer. The architectural distinction remains:
- Workflow automation platforms can connect external services and coordinate operational tasks.
- LOG_ON's authoritative policy, permissions, state, and high-impact execution controls should remain governed by the core product architecture.

A connection URL is not proof of a configured integration. Each connected action must be tested with the actual account, permission scopes, and target service.

## 5. n8n

The user's architecture notes explicitly state that n8n is not the core business logic or execution kernel.

It may be used for:
- Workflow automation.
- Service integration.
- Scheduled operations.
- Low-code orchestration in bounded use cases.

It should not silently become the authoritative layer for:
- Identity.
- Policy.
- Permission.
- Consent.
- Critical state transitions.
- High-impact action verification.

## 6. Supabase

Supabase appears in product discussions, particularly Re:Mind Me and related application architecture.

The user's wider architecture preference places PostgreSQL as authoritative state. Where Supabase is used, the application must still define:
- Tenant boundaries.
- Row-level security.
- Auth flows.
- Service-role key handling.
- Database migration discipline.
- Edge function permissions.
- Storage access.
- Backup and deletion policies.
- Audit and observability.

Using a managed database does not remove the need for application-level authority design.

## 7. Model and AI providers

The available technical discussions include:
- OpenRouter for model access and routing.
- AssemblyAI for speech and voice-agent capabilities.
- Sahara / Intron for African-language speech recognition research.
- N-ATLaS as a model/API reference the user says they can access.
- Other AI and model providers in research and product work.

Capabilities, pricing, language support, data handling, and APIs change over time. Any current product claim must be checked against the provider's current primary documentation and actual account configuration.

A model API key is a credential, not proof that a product integration is secure or production-ready. Never place keys in public repository files or conversation archives.

## 8. OpenServ and agent platform exploration

The user discussed a Global Business Intelligence Agent planned for an OpenServ environment. Prior context recorded that an OpenServ connector was not available in the relevant assistant environment at that time.

That historical limitation should not be treated as a permanent statement about the platform. Recheck current integrations before selecting the implementation path.

## 9. GitHub and engineering workflow

GitHub is used across the user's repositories for code, specifications, issues, pull requests, and CI.

A recurring lesson in the recent development work is that repository state and hosted CI state must be inspected separately.

### Example: hosted workflow failure

A recent status report described:
- GitHub Actions enabled.
- The eval workflow in .github/workflows/ci.yml active.
- PR #8 reported as merged by the user.
- A recent run, ID 41973874167, failing in approximately one second.
- The reported failure indicated that no runner was assigned.

This is recorded as a user-provided status report from the relevant conversation, not an independently reproduced run in this archive pass.

The diagnostic distinction matters: an execution environment that never assigns a runner cannot provide evidence about whether the test suite itself passes or fails. The next step is to inspect workflow configuration, runner availability, repository permissions, and actual run annotations.

## 10. Third-party workflow and media tools

The account context includes occasional use and discussion of:
- Descript for video editing and publishing workflows.
- Spotify for music discovery and playlist-related tasks.
- GitHub integrations.
- File and document workflows.
- Other connected apps and APIs.

These should be treated as separate connector use cases, not automatically part of LOG_ON's product architecture.

## 11. Integration evaluation checklist

For each integration, document:

1. What user problem requires the provider?
2. What is the source of truth?
3. Who authorizes the connection?
4. What scopes are granted?
5. What data leaves the system?
6. What external effects can occur?
7. How are results validated?
8. How are failures and retries handled?
9. How can access be revoked?
10. What evidence proves the workflow works end to end?

## 12. Open questions

- Which integrations are genuinely reusable across products?
- Which integrations should be direct and which should pass through MCP?
- How should credentials be scoped and rotated?
- Which actions can be safely retried?
- What is the standard event and audit envelope?
- How should external provider changes be detected?
- How are integration costs and rate limits incorporated into product economics?

## 13. Current working conclusion

The user values integration as a core systems capability. The strongest approach is to connect tools through stable, inspectable contracts while keeping authority, policy, consent, and canonical state under explicit control.
