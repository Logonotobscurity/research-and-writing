# Code Engineering Experiment — Preflight Report

**Date:** 21 October 2026  
**Task:** `safe-divide-canary-v1`  
**Status:** harness preflight passed; real model experiment **not run**.

## Results

| Measure | Single-pass baseline | Draft/verify |
|---|---:|---:|
| Candidate attempts | 1 | 2 |
| Visible tests | Pass | Pass on accepted attempt |
| Holdout acceptance tests | **Fail** | **Pass** |
| Accepted task | No | Yes, in the scripted fixture |
| Provider cost | Not available | Not available |

The scripted baseline returns a basic implementation that passes visible tests but fails holdout cases involving Boolean inputs and non-finite values. The scripted draft/verify path first rejects missing finite-value checks, then returns a corrected implementation that passes both suites.

## What this establishes

The harness mechanics were exercised end to end: candidate edits are allowlisted, visible tests run before verifier review, the retry limit is enforced, the verifier's reject/accept decision is recorded, and holdout tests run after verifier acceptance. The five harness unit tests pass. Python bytecode compilation of the harness and adapter also passes.

## What this does not establish

This is **not evidence** that draft/verify is better than single-pass generation in a real LLM workload. The mock adapter was intentionally written to exercise the desired control flow. No external model was called, no live provider usage was measured, and no cost-saving percentage is available. The local run time is not model latency. A single synthetic task cannot support the proposed 20% cost-reduction hypothesis.

## Decision

**Preflight: pass. Engineering hypothesis: untested.**

The next valid experiment requires actual baseline, drafter, and verifier adapters with provider-reported token/cost telemetry, a representative frozen task set, fixed acceptance suites, and a sandbox that limits generated code. Do not publish the fixture outcome as model-quality evidence.