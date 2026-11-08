# 06 — Memory, Context, Consent, and Personal Assistant Systems

## 1. Shared problem space

Several projects address a related problem: people and AI systems lose useful context across conversations, tools, workflows, and time. A memory product must capture information, organise it, retrieve the right material when needed, and protect the user's authority over retention, sharing, and action.

A recurring distinction is:

> **Remembering information is not the same as having permission to act on it.**

## 2. ContextPocket

**Repository:** `github.com/Logonotobscurity/context-pocket`

ContextPocket was discussed as agent context and memory infrastructure. The user was particularly concerned with real-client MCP capture/search behaviour, approval UX, and authentication.

A historical implementation snapshot in prior conversation noted:
- The repository had been made private.
- MCP capture/search worked with Bearer authentication.
- An MCP branch had been merged.
- OAuth background synchronisation was not built at that snapshot.
- Typecheck, lint, build, and MCP security tests were reported as passing.
- Eleven template tests were reported as failing around sign-in, migrations, or defaults.

These are historical reports, not current verified repository state. Recheck the code and CI before relying on them.

Important questions include: What is captured automatically? What requires user approval? Which identity/workspace owns a record? How can records be searched, corrected, exported, or deleted? How are OAuth and background sync separated from foreground capture? How is tenant isolation enforced?

## 3. Re:Mind Me

**Repository:** `github.com/Logonotobscurity/Remindme`

Re:Mind Me was described as a personal memory and reminder PWA ingesting conversations and notes from ChatGPT, Claude, and Grok, as well as voice input. The direction shifted from earlier Zapier/document/spreadsheet/ICS concepts toward a Supabase-backed application.

Historical notes included:
- Supabase as the central data layer.
- MCP capture/search using Bearer authentication.
- OAuth background sync not yet implemented at the recorded point.
- Daily_Action_Log, Daily Compilation Skill, Central Activity DB/Hub, Memory Stream, voice journaling, Google Calendar/ICS, and reminder flows.
- A “Thinking” Orb and dimmer “Slumber” visual state.

This describes design and a historical development snapshot, not proof that every integration is implemented.

A useful memory separation is:
- **Working memory:** short-lived active context and immediate state.
- **Episodic memory:** dated events and conversations.
- **Semantic memory:** stable facts, preferences, and concepts.
- **Task/reminder state:** commitments, due dates, and status.
- **Provenance:** source, capture time, and confidence.

Ingestion should normalise data, preserve attribution, suppress duplicates only where justified, and avoid converting uncertain statements into stable facts.

## 4. MorrowVoice

**Repository:** `github.com/Logonotobscurity/MorrowVoice`

MorrowVoice's single-source-of-truth direction combines an Iris-shaped principal and consent surface with deterministic consent kernels and audit machinery.

Core invariants discussed:
- Default deny.
- Retention off by default.
- Sharing off by default.
- The consent kernel is not merely a UI preference.
- The person remains the principal authority over consent.
- An operator role is not blanket permission to access or share data.
- Evidence is labelled Verified, Inference, Hypothesis, or Unknown.

The UI must accurately project system-enforced consent decisions. A visual toggle cannot be the only enforcement point.

## 5. Dedicated product records

For fuller product-level context and the distinction between historical reported state and current verification, see:
- [ContextPocket dossier](./products/context-pocket.md)
- [Re:Mind Me dossier](./products/remind-me.md)
- [MorrowVoice dossier](./products/morrowvoice.md)

## 6. Shared architecture principles

- **Ingestion:** preserve provenance, intent, time, source, and confidence.
- **Normalisation:** standardise records without erasing important wording or uncertainty.
- **Classification:** separate episodic, semantic, working, task, and sensitive data.
- **Retrieval:** apply relevance, temporal validity, permissions, and purpose; similarity alone is not authority.
- **Action:** a remembered commitment or inferred preference does not authorise an external side effect.
- **Audit:** users need understandable access to provenance, correction, export, and deletion controls.

## 7. Security and privacy risks

Cross-tenant retrieval; records exposed beyond authority; inference treated as verified profile data; prompt injection through stored notes; excessive retention; hidden sharing; reminders executed without current approval; and consent UI state diverging from backend enforcement.

## 8. Current synthesis

ContextPocket focuses on agent context infrastructure; Re:Mind Me on personal memory and continuity; MorrowVoice on principal authority, consent, and audit. Shared infrastructure may be reused, but each product requires its own user need, threat model, consent rules, and acceptance criteria.
