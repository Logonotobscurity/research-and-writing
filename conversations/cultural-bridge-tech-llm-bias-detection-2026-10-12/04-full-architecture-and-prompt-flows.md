# 04 — Full Architecture and Prompt Flows

## Complete module map
Mermaid-style flow from MIMO Input → PAL + SAE parallel → Hybrid Validation → optional Steering → Output, with feedback loop.

## End-to-end prompt journey
1. Base prompt + channel spec enters MIMO layer.
2. Expanded into N parallel channels (language, cultural context, transformation type).
3. Each channel branches to SAE Engine (feature extraction) and PAL Generator (executable script).
4. Hybrid Validation aggregates mechanistic, behavioral, and executable scores.
5. Optional steering with re-validation and capability check.
6. Output assembles JSON report, human summary, visualizations, and audit log.
7. Results can generate new channels for iteration.

Every prompt keeps a unique trace ID. Cross-channel consistency is computed only after all channels complete. No prompt leaves without an audit record.

## Development skeleton
Conceptual Python dataclass for Channel and core class showing the contracts. Immediate sequence: data models → Gemma Scope loader → minimal PAL templates → one behavioral validator → logging.
