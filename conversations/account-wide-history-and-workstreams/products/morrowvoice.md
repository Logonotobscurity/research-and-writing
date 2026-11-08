# MorrowVoice — Product Dossier

## 1. Product intent

MorrowVoice is a voice and consent-oriented product for which the user created a dedicated repository:
- https://github.com/Logonotobscurity/MorrowVoice

The user's single source of truth describes a composition of an Iris-shaped principal and consent surface with deterministic consent kernels and audit machinery from related platforms.

The product is not merely a voice interface. Its central concern is who has authority over a person's voice, data, representation, and consent.

## 2. Governing principles

The available design notes establish:

- Adult sovereignty.
- Default deny.
- Retention off by default.
- Sharing off by default.
- Consent kernel is not the UI.
- Evidence categories: Verified, Inference, Hypothesis, Unknown.
- The adult user remains the principal for their own consent.
- Caregiver or operator convenience must not override the adult's consent authority.

The product should not assume that a caregiver, administrator, or device owner automatically has permission to record, process, share, clone, or retain another person's voice.

## 3. Product architecture

The user's single-source-of-truth concept composes:

1. A principal and consent surface.
2. Deterministic consent kernels.
3. Audit and evidence mechanisms.
4. Voice-related capture, processing, or interaction components.

The interface may communicate consent state, but the consent rules must be enforced by authoritative system logic. A consent toggle in the UI is insufficient if backend APIs or storage services can bypass it.

## 4. Consent lifecycle

A complete design should model consent through its lifecycle:

- Initial notice and purpose.
- Capture activation.
- Audio processing.
- Transcription.
- Summarization or transformation.
- Storage and retention.
- Sharing or export.
- Voice synthesis or cloning, where relevant.
- Revocation.
- Re-consent after material purpose changes.
- Deletion.
- Backup and recovery.
- Audit of consent and downstream data handling.

The consent object should be explicit about principal, purpose, data types, recipients, duration, channels, and allowed operations.

## 5. Authority and identity model

The principal model should distinguish:
- The adult whose voice or data is involved.
- The person initiating a capture or request.
- Caregiver or support roles.
- Operators and administrators.
- Service providers and processors.
- Agents and tools.
- Third parties who may be captured in audio.

Each role should have explicit authority limits. A role label should not imply unrestricted permission.

## 6. Threats and failure modes

Potential risks include:
- Consent inferred from device possession.
- Consent represented only in frontend state.
- Capture continuing after revocation.
- Sharing enabled by default.
- Retention beyond the declared purpose.
- Voice-clone use beyond the original scope.
- Caregiver or operator privilege escalation.
- Third-party audio capture without an appropriate policy.
- Deletion that leaves unmanaged backups or derived data.
- Audit logs that expose sensitive audio or transcript content.
- Re-consent omitted after a new use is introduced.

## 7. Evidence requirements

A consent action should produce a verifiable record of:
- Principal identity or validated authority.
- Consent scope.
- Purpose.
- Data categories.
- Time and policy version.
- Capture or processing event.
- Retention and sharing state.
- Revocation or expiry.
- Downstream data deletion or restriction.
- Any exception or manual review.

Logs should prove the event without storing unnecessary sensitive payloads.

## 8. Development status and evidence limits

The user requested development from the MorrowVoice source-of-truth specification and asked for verification of what remained and whether implementation followed the prompt.

The current repository state has not been independently inspected for this archive. Therefore, this dossier records the product contract and known design principles, not a claim of implementation completeness.

## 9. Open questions

1. What is the exact product user and primary use case?
2. How is the principal authenticated?
3. How is authority established for users with differing support needs?
4. What consent format is authoritative?
5. How are revocation and deletion enforced across derived data and backups?
6. Which operations can be delegated, and which remain principal-only?
7. How are third-party voices handled?
8. How is voice synthesis separated from voice capture?
9. What threat model and acceptance tests are required before a pilot?

## 10. Current working conclusion

MorrowVoice should be built around an enforceable consent kernel and an adult-controlled principal model. The interface should reveal and explain the consent state, but the system itself must enforce it across capture, processing, storage, sharing, retention, revocation, and deletion.
