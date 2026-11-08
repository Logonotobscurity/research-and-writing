# 05 — PAL, African-Language Intelligence, and Voice-to-Action Research

## 1. Research direction

The user has discussed a family of research and product concepts centred on language understanding, code-switching, cultural context, voice, and the safe conversion of interpreted meaning into action.

The central problem is not simply converting speech into text. It is preserving meaning when speakers move between languages, dialects, registers, idioms, cultural references, and implied intentions—then determining whether the interpreted request authorises a particular action.

The work is connected to African language and interaction contexts, especially Yorùbá and Nigerian Pidgin. The user has explicitly emphasised that corpora, performance claims, and language coverage must not be fabricated.

## 2. PAL and related concepts

Retained names include:
- **PAL:** Personal AI / language-context and voice-to-workflow research.
- **CIE:** Contextual Intelligence exploration.
- **DAPF:** Discourse-Adaptive Prompting Framework.
- **Sahara CodeSwitch:** African multilingual and code-switching research.
- **Proverb-Logic:** older term replaced in the retained context by DAPF.
- **Proverb Activation Library:** older or alternate PAL expansion referenced in earlier notes.
- **Meaning-to-Action Kernel 2.1:** proposed layer converting interpreted meaning into a governed action representation.
- **Composer's Voice Twin:** voice-representation and interaction concept.

These are related research or product components, not automatically separate, complete products.

## 3. Repository and research references

Prior references:
- PAL: `github.com/Logonotobscurity/pal`
- `wwhisper`: `github.com/Logonotobscurity/wwhisper`
- Prompt Protocol Atlas DOI: `10.1145/3773292`
- Sahara CodeSwitch Africa Challenge.
- AssemblyAI context associated with `wwhisper`.
- NCAIR / Langa-hosted N-ATLaS API access was reported by the user.

This archive does not independently verify current repository contents, current API access, dataset availability, model performance, or publication metadata.

## 4. OMI Edge Ear concept

The user's conceptual pipeline was:

**BLE/Wi-Fi input → PAL Mobile Gateway → Sahara STT / code-switch handling (EN / PCM / YOR) → Meaning-to-Action Kernel 2.1 → Composer's Voice Twin or downstream action.**

This is a system concept. Exact implementation, supported devices, model versions, and field performance remain to be verified.

## 5. Why transcription is not enough

A speech recogniser can produce plausible text while losing:
- Language boundaries and code-switch structure.
- Speaker intent.
- Idiomatic or figurative meaning.
- Context-dependent references.
- Social or cultural nuance.
- Negation, uncertainty, or implied constraints.
- The difference between a request, suggestion, joke, and instruction.

The architecture should distinguish:
1. Audio and speech processing.
2. Language identification and code-switch segmentation.
3. Literal transcription.
4. Contextual and discourse interpretation.
5. Uncertainty estimation.
6. Intent and action-candidate formation.
7. Permission and consent checks.
8. Human confirmation where required.
9. Execution and audit.

## 6. Action gates

An interpreted utterance must not automatically trigger a consequential action. The system must establish:
- Whether the request was understood with sufficient confidence.
- Whether the speaker has authority over the action.
- Whether the action is in scope.
- Whether it is reversible or high impact.
- Whether confirmation is required.
- Whether necessary data and permission exist.

The action gate is separate from speech recognition and language interpretation.

## 7. Research and benchmark requirements

Future experiments should record:
- Dataset source and licence.
- Language, dialect, and code-switch coverage.
- Speaker and domain diversity.
- Annotation methodology.
- Train/validation/test separation.
- Data contamination and leakage checks.
- Word error rate and task-specific metrics.
- Semantic interpretation accuracy with defined labels.
- False-action and missed-action rates.
- Human review and disagreement rates.
- Performance in noisy and low-resource conditions.

Do not report corpus size, language coverage, accuracy, or benchmark results without an actual dataset and reproducible experiment.

## 8. Key risks and current direction

Risks include treating a language label as a full representation of cultural context, translating literal words while losing pragmatic meaning, overstating idiom understanding, fabricating corpus records, bypassing action authorisation, and confusing transcription accuracy with action correctness.

The research direction is to connect language understanding to governed action while preserving uncertainty and cultural context. Speech recognition, meaning reconstruction, permission, approval, and audit are separate stages requiring separate evaluation.
