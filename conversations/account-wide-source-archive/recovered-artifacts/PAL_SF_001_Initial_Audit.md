# PAL-SF-001 --- Initial Corpus Integrity & Silent Failure Audit

**Audit run:** 2026-10-22\
**Scope:** Available PAL research materials retrieved from the user's
ChatGPT Library.\
**Audit mode:** Baseline evidence audit; no claim of Yoruba linguistic
or cultural validation.\
**Decision:** **NOT READY for publication or claims of validated
cultural interpretation.**\
**Narrow permitted use:** Internal research hypotheses and test-design
development, with clear unverified labels.

## 1. Executive assessment

**Initial readiness: 3/10 for publication-grade evaluation; 6/10 for
structured internal research development.** These are qualitative
readiness judgments, not statistically calibrated scores.

The materials already contain several strong integrity principles:
preserve canonical Yoruba text, keep raw source data immutable, record
hashes and pipeline versions, separate hypotheses from validated claims,
preserve community variance, and allow retrieval to abstain. The main
gap is evidence and execution: the inspected PAL v0.2 draft contains ten
entries, not a verified 52-record corpus, and its entries explicitly
mark provenance as unverified and interpretation fields as hypotheses.
The v0.3 architecture defines 13 dimensions, while the requested
research package refers to seven dimensions. These must be reconciled
before downstream evaluation.

## 2. Evidence inventory

The following three Library files were materialized and inspected
programmatically:

  ------------------------------------------------------------------------------------------------------------------------------------------
  File                                       Bytes                Lines SHA-256
  --------------------------- -------------------- -------------------- --------------------------------------------------------------------
  `PAL_v0.2_fixed.md`                       23,592                  618 `9bab0f9ef33424fb07e83a2e227b54ead2b34f6dd20c46e36e4e1d81616a1bd7`

  `PAL_V03_ARCHITECTURE.md`                 21,771                1,063 `8cc555d151e283c15bc6169a88960a32a675326e190792f9a0beb0588bf0a1b6`

  `PAL_V03_DEVELOPMENT.md`                  24,517                1,533 `cd19cc8f0c9c82ff46f227211ddb10fac406b244794f64efd7f2b0ca9966de3e`
  ------------------------------------------------------------------------------------------------------------------------------------------

**Not established in this audit:** the existence or identity of the
cited framework paper PDF; a complete 52-record export; primary-source
page/entry locators for the draft proverbs; independent annotations by
Yoruba-fluent experts; community review records; or empirical
inter-annotator agreement.

The GitHub repository `Logonotobscurity/pal` was previously found to
describe a voice-to-action / meaning-to-action project. Do not assume it
is the canonical repository for this Proverb Activation Library research
corpus without an explicit repository-level verification.

## 3. Findings register

### F-001 --- Corpus size does not meet the proposed 52-record target

-   **Severity:** High
-   **Confidence:** High for the inspected file; not a claim about every
    file that may exist elsewhere.
-   **Evidence:** `PAL_v0.2_fixed.md` has ten `ENTRY 01` through
    `ENTRY 10` sections.
-   **Risk:** Claims about a 52-proverb corpus could overstate the
    material actually present in this inspected artifact.
-   **Action:** Treat this file as a ten-entry draft. Locate or
    construct a separate, provenance-backed 52-record export; do not pad
    the corpus with generated examples.

### F-002 --- Provenance is explicitly unverified

-   **Severity:** Critical for publication claims
-   **Confidence:** High
-   **Evidence:** The v0.2 header says source provenance must be
    verified per entry. Each of the ten entry sections includes
    `SOURCE_NOT_YET_VERIFIED`.
-   **Risk:** The cited collection or attribution could be wrong,
    incomplete, or untraceable.
-   **Action:** For each entry, record the exact work/edition, page or
    entry locator, source text, and verification evidence. Until then,
    retain `UNVERIFIED` and exclude from claims that require
    source-authenticated proverbs.

### F-003 --- Interpretive fields are hypotheses, not ground truth

-   **Severity:** Critical for evaluation validity
-   **Confidence:** High
-   **Evidence:** The v0.2 rules classify semantic frame, causal
    structure, bidirectionality, social domain, discourse position,
    relationship register, community specificity, failure contexts, and
    expected activation as interpretive fields requiring validation. The
    ten entry sections repeatedly mark interpretations as hypotheses and
    include `TBD` experiment outputs.
-   **Risk:** A model could be evaluated against the author's
    unvalidated interpretation, making the evaluation circular or
    measuring conformity to a hypothesis rather than proverb
    understanding.
-   **Action:** Keep hypotheses distinct from
    expert/community-adjudicated references. Do not score model outputs
    against unvalidated labels as if they were gold-standard answers.

### F-004 --- Seven-dimensional and 13-dimensional schemas are not yet reconciled

-   **Severity:** High
-   **Confidence:** High
-   **Evidence:** `PAL_V03_ARCHITECTURE.md` explicitly defines D1--D13:
    Simulation World, Conceptual Domain, Discourse Position, Speech Act,
    Relationship Register, Community Specificity, Failure Contexts,
    Historical Provenance, Philosophical Layer, Worldview Assumptions,
    Temporal Logic, Power Symmetry, Deployment Risk. The research brief
    names seven dimensions, using some different names (for example,
    Simulation Domain and Conceptual Domain).
-   **Risk:** Field names, definitions, label scales, and evaluation
    results may not map consistently across artifacts.
-   **Action:** Publish a versioned 7D research schema and a separate
    7D↔13D mapping table. Mark each mapping as exact, partial, derived,
    or unmapped; never silently drop dimensions.

### F-005 --- The architecture has useful integrity controls, but implementation status is unknown

-   **Severity:** Medium
-   **Confidence:** High that the controls are documented; unknown
    whether they are implemented.
-   **Evidence:** Architecture/development materials call for immutable
    raw records, source hashes, pipeline versions, original Yoruba and
    search-normalized text separation, provenance tracking, staged
    annotation, community variance, and non-destructive correction
    history.
-   **Risk:** Documentation may be mistaken for working controls.
-   **Action:** Convert each invariant into an executable test and
    report which tests actually ran. Do not claim controls are
    implemented until code, data, or logs demonstrate it.

### F-006 --- Text integrity can be checked mechanically, but correctness cannot be inferred from Unicode alone

-   **Severity:** High
-   **Confidence:** High
-   **Evidence:** The development material explicitly prohibits
    stripping tonal marks, replacing Yoruba letters with English
    approximations, LLM rewriting, or back-translation as a way to
    recover canonical text.
-   **Risk:** Export, normalization, or copy-editing can silently change
    text; conversely, valid Unicode does not prove a proverb's spelling
    is authoritative.
-   **Action:** Hash and freeze source text; compare all derived exports
    to the canonical field; keep search normalization in a separate
    field; route suspected spelling variants to qualified review.

### F-007 --- Existing evaluation design needs independent references and controlled conditions

-   **Severity:** High
-   **Confidence:** High as a requirement; actual benchmark execution
    not established.
-   **Evidence:** The v0.2 file includes planned behavioral/mechanistic
    evaluation and control conditions, but `ACTUAL ACTIVATION` remains
    `TBD` in the ten entry sections.
-   **Risk:** Prompt changes, answer ordering, leakage, or
    model-generated references could produce inflated or unstable
    results.
-   **Action:** Freeze prompt/model/dataset versions; separate
    development and held-out evaluation data; use independent reference
    annotations; test prompt sensitivity and report all exclusions.

## 4. Initial status summary

  ----------------------------------------------------------------------------
  Control area            Initial status          Reason
  ----------------------- ----------------------- ----------------------------
  Source provenance       **Fail / unresolved**   Ten inspected entries
                                                  explicitly mark source
                                                  unverified.

  52-record target        **Fail in inspected     Only ten entry sections
                          draft**                 found in v0.2.

  Canonical text          **Documented**          Strong requirements exist;
  preservation policy                             runtime enforcement not
                                                  demonstrated.

  Seven-/13D schema       **Fail / unresolved**   Both exist but no verified
  compatibility                                   mapping artifact was found
                                                  in inspected files.

  Annotation ground truth **Not established**     Hypotheses and `TBD`
                                                  experiment results remain.

  Independent             **Not established**     No completed adjudication
  human/community                                 evidence inspected.
  validation                                      

  Reproducible evaluation **Not established**     Evaluation design exists,
                                                  but completed runs and logs
                                                  were not verified.

  Research claim          **Partially specified** Provenance/evidence-status
  traceability                                    concepts exist; end-to-end
                                                  claim ledger not verified.
  ----------------------------------------------------------------------------

## 5. Release decision

**NOT READY** for publication claims that imply a source-verified,
culturally validated 52-proverb corpus or established model competence.

This is not a rejection of PAL's concept. It is a restriction on what
the current inspected evidence supports. PAL can continue as an internal
framework and hypothesis-development project if all unverified content
remains explicitly labeled.

## 6. P0 remediation sequence

1.  **Freeze the inspected baselines.** Keep the three source files
    unchanged and preserve their SHA-256 values above.
2.  **Create a corpus manifest.** One row per candidate record, with
    stable ID, exact source locator, source-text hash, provenance
    status, canonical text, and review state.
3.  **Verify the target corpus count.** Establish whether the research
    target is ten, 50, 52, or another size. Do not conflate PAL-50 and
    the proposed 52-record package.
4.  **Reconcile the schema.** Produce `PAL_ANNOTATION_SCHEMA_7D_v1.0.md`
    plus a loss-aware mapping to the 13D architecture.
5.  **Separate annotation proposal from reference annotation.** Give
    every field an epistemic status and evidence basis; prohibit model
    confidence from upgrading that status.
6.  **Run canonical-text integrity checks.** Compare source, canonical,
    processed, and exported text without overwriting the source.
7.  **Set up independent annotation and adjudication.** Record raw
    annotator decisions, disagreements, adjudication, community-specific
    variation, and unresolved cases.
8.  **Only then finalize the benchmark.** Freeze model, prompt, split,
    scoring, and acceptance criteria before running held-out evaluation.

## 7. Falsifiable minimum experiments

### MVE-1 --- Record/provenance coverage

-   **Question:** What fraction of the declared corpus has traceable
    primary-source provenance?
-   **Procedure:** Enumerate all records and independently verify each
    locator.
-   **Acceptance:** 100% of records included in the publication-grade
    evaluation have a resolvable provenance record, or are explicitly
    excluded from that evaluation.
-   **Failure:** Any record silently treated as verified without source
    evidence.

### MVE-2 --- Canonical text round-trip

-   **Question:** Do ingestion, export, and reload preserve canonical
    Yoruba text exactly?
-   **Procedure:** Hash canonical UTF-8 text before and after each
    supported transformation; compare exact strings and code points.
-   **Acceptance:** 100% exact match for canonical fields; any intended
    alternative spelling is a separate reviewed variant.
-   **Failure:** Any unexplained difference in canonical text.

### MVE-3 --- Schema mapping coverage

-   **Question:** Can each 7D field be mapped to the 13D schema without
    silent information loss?
-   **Procedure:** Map every field and label, then test records
    containing multi-label, missing, disputed, and community-variant
    values.
-   **Acceptance:** Every mapping is classified
    exact/partial/derived/unmapped, with explicit loss behavior and
    tests.
-   **Failure:** Unexplained dropped fields or silently collapsed
    disagreement.

### MVE-4 --- Independent annotation pilot

-   **Question:** Can two qualified annotators apply each categorical
    dimension consistently?
-   **Procedure:** Independently annotate a small pilot sample selected
    to include ambiguous/context-sensitive cases; adjudicate only after
    initial decisions are locked.
-   **Acceptance:** Pre-register a dimension-appropriate agreement
    method and threshold before looking at results; report per-dimension
    values and confidence/limitations. Do not invent a universal
    threshold for free-text fields.
-   **Failure:** Agreement computed from post-adjudication labels or
    from model-generated pseudo-labels treated as independent.

### MVE-5 --- Prompt-sensitivity test

-   **Question:** Are model results robust to irrelevant prompt and
    answer-order changes?
-   **Procedure:** Freeze a held-out set and compare a pre-registered
    set of semantically equivalent prompt variants and answer-order
    permutations.
-   **Acceptance:** Report performance deltas and error changes; set the
    acceptable delta before the run.
-   **Failure:** Reporting only the best-performing prompt/order.

## 8. Evidence required to upgrade the release decision

-   Complete record manifest and corpus-size statement.
-   Resolvable provenance for every record used in claims.
-   Canonical text integrity report.
-   Versioned schema and mapping tests.
-   Independent annotation data, disagreement log, and adjudication
    protocol.
-   Held-out evaluation data and reproducible run configuration.
-   Claim-to-evidence register that distinguishes observed results,
    interpretations, hypotheses, and unknowns.

------------------------------------------------------------------------

**Audit integrity note:** This report evaluates the inspected artifacts
and their documented state. It does not verify the cultural correctness
of any proverb, and it does not imply that tests not run have passed.