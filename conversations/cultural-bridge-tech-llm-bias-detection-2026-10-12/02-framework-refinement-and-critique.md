# 02 — Framework Refinement and Critique

## What we are building
Cultural Bridge Tech (CBT): an open, mechanistic toolkit that detects, analyzes, and mitigates cultural/social biases in LLMs via SAE feature analysis (anchored on Gemma Scope JumpReLU SAEs) plus cross-lingual adversarial robustness testing.

## Contextual design framing
- Empathize: biases hide in cross-lingual transfer, code-switching, low-resource languages.
- Define: black-box benchmarks are incomplete; mechanistic methods are heavy but precise.
- Ideate/Prototype: Gemma Scope + SAELens as microscope, wrapped with multilingual adversarial generation and hybrid validation.
- Test: success = feature precision + robustness under language shift + human cultural validation.

## Critique and alternatives
**Strengths:** Aligns with sparse feature circuits (Marks et al.), healthcare race-bias SAE work, and open Gemma Scope infrastructure.

**Limitations:**
- Incomplete feature recovery, residual polysemanticity, shrinkage (mitigated by JumpReLU).
- English-centric training misses culture-specific concepts.
- SAE features themselves can be adversarially attacked.
- High compute and evaluation subjectivity.

**Complementary frameworks:**
- Hybrid mechanistic + behavioral (CrowS-Pairs, MultiLingualCrowsPairs, LangBiTe).
- Sparse feature circuits for causal localization.
- Multilingual / language-specific SAEs.
- Governance-oriented explainability-debt tracking.
- English debiasing transfer studies with measured fluency cost.

## Expanded framework elements
Refined architecture with MIMO-style channels, hybrid validation, and practical SAE fixes (prefer JumpReLU, track feature persistence/divergence, validate behaviorally). Minimal conceptual code skeleton provided.
