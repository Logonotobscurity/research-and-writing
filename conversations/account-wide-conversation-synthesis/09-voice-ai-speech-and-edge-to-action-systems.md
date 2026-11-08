# 09 — Voice AI, Speech, and Edge-to-Action Systems

## 1. Scope

The user's voice work connects speech capture, code-switch recognition, contextual interpretation, workflow generation, consent, execution authority, and verification.

The design goes beyond a speech-to-text interface. Voice is treated as one input channel into a larger action system.

## 2. Reference architecture

A recurring architecture in the available notes is:

**OMI Edge Ear → BLE / Wi-Fi → PAL Mobile Gateway → Sahara STT → Meaning-to-Action Kernel 2.1 → Voice-to-Workflow → Composer's Voice Twin.**

The labels describe a proposed or explored system arrangement. They do not prove that every stage is fully implemented or integrated.

### OMI Edge Ear
An edge audio-capture interface, discussed in connection with OMI hardware and wearable or ambient audio input.

### Connectivity
BLE and Wi-Fi provide the path from the capture device to a gateway. The trust and privacy implications of always-available audio require separate treatment.

### PAL Mobile Gateway
A local or mobile bridge that receives audio and coordinates transcription and downstream processing.

### Speech recognition
Sahara/Intron has been explored for African speech and code-switch scenarios. The user has also referred to an NCAIR N-ATLaS API key. The precise API capability and permitted use must be checked against current documentation and credentials; possession of a key does not establish implementation.

### Meaning-to-Action Kernel
The downstream system should identify what the utterance means for the active task, preserve uncertainty, and generate an action proposal rather than execute arbitrary transcript content.

### Voice-to-Workflow
A spoken instruction can be converted into a structured, reviewable workflow with explicit fields and required context.

### Composer's Voice Twin
The concept appears as a personalized voice-related interface or output layer. Its exact product contract, consent semantics, and production status should be established in a dedicated specification before making implementation claims.

## 3. Speech recognition versus meaning recovery

The architecture should keep separate:
- Audio quality.
- Speech segmentation.
- Language identification.
- Transcription.
- Code-switch boundary detection.
- Word and phrase interpretation.
- Pragmatic intent.
- Required slot extraction.
- Task feasibility.
- Permission and policy.
- Execution and verification.

A high-quality transcript is not sufficient proof that an action proposal is correct. The system must validate critical details such as recipient, destination, amount, currency, date/time, negation, payment status, customer, or invoice where these affect the task.

## 4. Voice action gates

The broader PAL and execution-kernel discussions imply four separate gates:

1. **Meaning gate:** is the utterance understood well enough for the requested task?
2. **Completeness gate:** are required details present, and are critical slots reliable?
3. **Authority gate:** is the principal authorized to perform the proposed operation under policy?
4. **Execution and verification gate:** can the action be performed safely and can its outcome be confirmed?

If a critical detail is missing or ambiguous, the system should clarify. If authority is absent, it should refuse or seek the appropriate approval. If an external result is unknown, it should say so.

## 5. Code-switch and African language support

The user's research focus includes Yoruba-English and Nigerian Pidgin-English code-switching, along with English and mixed utterances.

The system should not treat code-switching as noise or assume every language transition is a transcription error. It should preserve language spans and uncertainty where possible.

Vendor capabilities must be checked against current official documentation. Prior notes reported differing support across vendors and included the warning not to claim turnkey Yoruba/Pidgin support from a voice-agent product without confirmation.

## 6. Pilot design

A prior 50-utterance pilot specification allocated:
- 20 Yoruba-English utterances.
- 15 Pidgin-English utterances.
- 10 English utterances.
- 5 mixed or ambiguous utterances.

The proposed comparison uses providers as A/B conditions with the same downstream meaning, policy, and workflow logic. The key is to isolate the contribution of the speech-recognition provider from the behaviour of the downstream action system.

Suggested measurements:
- Word and phrase accuracy.
- Language-span identification.
- Code-switch boundary accuracy.
- Critical-slot extraction.
- Intent classification.
- Clarification appropriateness.
- Workflow validity.
- Policy compliance.
- Approval correctness.
- Unsafe action rate.
- Provenance completeness.
- End-to-end task outcome.

The pilot size is suitable for exploratory error analysis, not broad claims about general performance.

## 7. Safety endpoint

The user has identified **UNSAFE ACTION RATE** as a particularly important endpoint.

The measure should be defined precisely. For example, an unsafe action proposal might include:
- Wrong recipient or target.
- Missing critical field treated as known.
- Negation reversal.
- Incorrect payment or completion status.
- Unauthorized financial or external write.
- Action based on untrusted audio content.
- Failure to request clarification when required.
- Approval bypass.
- Execution despite a policy rejection.

The denominator, adjudication protocol, severity weighting, and handling of ambiguous cases must be specified before reporting a rate.

## 8. External media and music-related interactions

The account history also includes occasional questions involving music, lyrics, audio, and media discovery. Those interactions are related to voice/media understanding but should not be conflated with the PAL action platform.

Where media interpretation is requested:
- Identify the actual source material.
- Distinguish text or audio evidence from interpretation.
- Preserve uncertainty about cultural meaning.
- Do not invent lyrics or attribution.
- Respect copyright limits when quoting lyrics or reproducing source text.

## 9. Privacy and consent implications

Voice systems may capture sensitive or third-party information. The architecture should define:
- Capture activation and user notice.
- Whether ambient capture is continuous or event-based.
- Local versus cloud processing.
- Audio and transcript retention.
- Redaction and deletion.
- Sharing and export.
- Access control.
- Third-party recording implications.
- Consent to voice cloning or synthesis.
- Revocation and re-consent.
- Security of device pairing and transmission.

These are design requirements and questions; their present implementation state is not established here.

## 10. Open questions

1. What is the exact role of the edge device versus the mobile gateway?
2. Which processing can remain local?
3. What is the source of truth for transcripts and workflow proposals?
4. How are multiple speakers and third-party consent handled?
5. Which critical slots require human confirmation regardless of model confidence?
6. How is a voice-generated action tied to an authenticated principal?
7. Which vendor currently provides the required language and code-switch performance?
8. How are action outcomes reconciled when the external system times out?

## 11. Current working conclusion

Voice is an input modality, not an authority mechanism. Speech recognition, meaning recovery, task completion, authorization, and execution verification must remain separate, testable stages.
