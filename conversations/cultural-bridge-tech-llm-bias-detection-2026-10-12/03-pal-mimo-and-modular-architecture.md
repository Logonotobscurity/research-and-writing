# 03 — PAL, MIMO, and Modular Architecture

## Interpretation of user request
"Within the same build up and design for Pal and MIMO why"

Interpreted as applying the same design system to:
- **PAL** = Program-Aided Language Models (Gao et al. 2023) — LLM generates executable intermediate programs run by a runtime.
- **MIMO** = Multiple-Input Multiple-Output metaphor for parallel channels (languages, cultural framings, attack types).

## Why the combination is stronger
- Mechanistic (SAE features) shows *where*.
- MIMO forces multi-perspective measurement of persistence/divergence.
- PAL makes scoring and evaluation executable and reproducible, reducing LLM-as-judge meta-bias.

## Refined modular architecture (six modules)
1. **MIMO Input & Channel Layer** — expands base prompt into tagged parallel channels.
2. **PAL Analysis Generation Layer** — emits sandboxed Python scripts for deltas, probes, steering checks.
3. **Mechanistic Core (SAE Engine)** — Gemma Scope / JumpReLU + SAELens hooks.
4. **Hybrid Validation & Robustness Layer** — mechanistic + behavioral + executable scores.
5. **Steering & Mitigation Module** — optional, measured clamps with capability preservation.
6. **Output, Audit & Dashboard Layer** — JSON, human report, visualizations, full audit log.

Key contracts and extension points documented. Patterns of understanding (feature persistence, divergence, steering fragility) treated as cognitive signals with human-in-the-loop for cultural interpretation.
