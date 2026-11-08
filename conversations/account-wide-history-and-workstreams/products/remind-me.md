# Re:Mind Me — Product Dossier

## 1. Product intent

Re:Mind Me is a personal knowledge and memory capture system. The user's discussions describe a Supabase-backed progressive web application intended to ingest and retrieve useful material across AI conversations and voice input.

The concept is to make personal context portable and searchable rather than leaving valuable material isolated in separate chat histories and tools.

Repository reference:
- https://github.com/Logonotobscurity/Remindme

## 2. Intended user problem

Useful knowledge is distributed across:
- ChatGPT and other AI conversations.
- Claude and other assistants.
- Notes and saved references.
- Voice capture.
- Project and personal reflections.
- Follow-up reminders and tasks.

The user wants a system that can capture, organize, retrieve, and reapply this material without requiring manual reconstruction every time.

## 3. Product principles

- Capture should be explicit and understandable.
- Retrieval should be grounded in stored records.
- Source and provenance should remain visible.
- Duplicate records should be handled safely.
- Users should be able to control retention and deletion.
- Integrations should be honest about what they can actually access.
- An app should not claim to synchronize platform histories unless an authorized and working integration exists.

## 4. Architecture and integration direction

The available context identifies:
- Supabase-backed application data.
- PWA experience.
- Memory ingestion from AI platforms where accessible.
- Voice capture.
- MCP integration.
- Authenticated capture and search.
- Bearer-authenticated API paths.

The user discussed cross-platform capture for ChatGPT, Claude, and Grok, but OAuth synchronization was not established as complete in the prior notes.

## 5. Known implementation and validation notes

The available project memory records:
- An MCP branch was merged.
- Capture and search worked through Bearer authentication at the time of the note.
- OAuth sync had not been built.
- Eleven template tests were failing in an earlier snapshot.

A daily capture workflow recorded six local staged items around 22 October 2026. The notes also state:
- A schema-version field remained pending.
- No remote data was written because no authorized destination was available.
- A local Daily Reports worksheet artifact was prepared.
- No remote Google Sheet row was created.

This distinction matters: staged local records and a prepared worksheet are not proof of a successful remote sync.

## 6. Idempotency and data integrity

A durable capture system should define:
- A stable source event ID.
- Idempotent ingestion.
- Duplicate detection.
- Capture timestamp and source timestamp.
- Source identity and provenance.
- Schema version.
- Processing state.
- Error and retry behaviour.
- User-controlled deletion.
- Conflict and merge handling.

The prior discussion proposed an idempotent event identifier. The actual implementation should be checked before claiming that duplicate capture is fully controlled.

## 7. UI and interaction direction

The user discussed a visual experience involving:
- A Thinking Orb.
- A dimmed “Slumber” state.
- A more ambient personal memory interface.

These are design directions, not proof of implemented UI behaviour. The interface should make the distinction between capture, processing, retrieval, and retained memory visible.

## 8. Privacy and platform-access boundaries

The system must not assume that one AI platform exposes another platform's history. Access must come from actual user-provided exports, supported APIs, or connected integrations with appropriate permissions.

For every source, specify:
- What is captured.
- How it is authenticated.
- Which scopes are granted.
- Whether the source allows incremental sync.
- How deletions are handled.
- Whether data is stored locally or remotely.
- What happens when authorization expires.
- What is shown to the user when sync is incomplete.

## 9. Open questions

1. Which sources are supported through real integrations today?
2. Which are manual import only?
3. What is the canonical data model for memories and conversations?
4. How are memories deduplicated and linked to projects?
5. How can the user correct, export, or delete a memory?
6. How are OAuth tokens secured and revoked?
7. Which search approach best preserves context and provenance?
8. What is the relationship between personal memory and canonical project records?
9. What does a meaningful user-retention metric look like?

## 10. Current working conclusion

Re:Mind Me has a clear cross-platform personal-memory ambition, but the implementation notes show that capture, search, OAuth sync, template health, and remote persistence must be tracked separately. The product should not imply universal AI-history access until each source integration is implemented and verified.
