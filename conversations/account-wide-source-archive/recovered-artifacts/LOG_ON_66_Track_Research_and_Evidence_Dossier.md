# LOG_ON — 66-Track Research & Evidence Dossier
## Track-specific research questions, required proof and advancement gates

**Purpose:** establish the research and evidence needed for every track in the LOG_ON portfolio. This is a research plan, not a claim that the research has already been performed or that any product implementation has been verified.

**Evidence boundary:** this dossier uses the owner-provided audit and the recovered 66-track register. The portfolio repository is a registry/explorer, systems map, diagram gallery and local enquiry form. It is not the product codebase for these 66 tracks. The reported status means the owner described the initiative; proposed means its intended shape is recorded; unknown must remain unknown. None of the 66 tracks is verified or deployed.

## 1. Current baseline and status rules

| Evidence classification | Tracks | What it means |
|---|---:|---|
| Verified | 0 | No track has product-level implementation evidence sufficient for this label |
| Reported | 21 | Owner-described; still requires repository/source and behavior verification |
| Proposed | 44 | Intended project shape; research and validation remain necessary |
| Unknown | 1 | Do not infer identity, domain, users or claims |
| **Total** | **66** | Portfolio inventory count, not a shipped-product count |

Owner-provided activity: **62 ongoing, 4 historical, 0 paused**. Thirteen names are proposed working names. A working name remains visible and does not imply inactivity.

Owner-provided maturity roll-up: 32 in design, 12 in development, 12 research, 6 prototype, 0 verified MVP and 0 deployed. The audit also says historical tracks must not be treated as a maturity stage: their **activity** is historical and their **maturity** is unknown. Therefore, the registry migration must move historical out of the maturity enum and recalculate the exact maturity counts from individual records. Do not guess which records occupy each maturity bucket.

Reported tracks by ID: **1, 7, 9, 10, 11, 18, 20, 23, 25, 35, 37, 39, 41, 43, 50, 57, 59, 60, 61, 62, 63**. Track **45 Peculiar** is unknown. The remaining 44 are proposed.

## 2. What counts as evidence

### A. Research evidence

Every track needs a research packet proportionate to its risk and type:

1. **Problem evidence:** named user, buyer, job, observed workflow, pain frequency, current workaround and consequence of failure.
2. **Market and alternatives:** competitors, substitutes, manual workarounds, procurement constraints, switching cost, target geography and evidence of willingness to pay where commercial.
3. **Product definition:** charter, target user, non-goals, use cases, refusal/abstention path, state model and success criteria.
4. **Technical feasibility:** source/API/hardware/model inventory, version compatibility, data availability, license, latency/cost assumptions and a proof for the riskiest dependency.
5. **Data and rights:** provenance, permission/license, consent, intended purpose, access, retention, correction, deletion, backup deletion and transfer/residency questions where relevant.
6. **Risk and misuse:** assets, actors, threat model, abuse cases, prompt injection, excessive agency, authorization, privacy, supply chain and high-impact failure scenarios.
7. **Evaluation design:** hypothesis, baseline, dataset, metrics, thresholds, uncertainty, test slices, reviewer method and known limitations.
8. **Operations:** operator, support owner, monitoring, incident path, retry/reconciliation, backup, rollback, service dependencies and cost to operate.
9. **Outcome evidence:** user task completion, quality, time/cost change, adoption, retention or business result where appropriate, with attribution limitations.
10. **Decision record:** proceed, narrow, pivot, defer, archive or retain unknown, with rationale, reviewer and source references.

### B. Implementation evidence for any track actually being built

The owner-defined 00–12 specification set is mandatory for a build track:

- `00-PRODUCT-CHARTER.md`
- `01-USER-JOURNEY.md`
- `02-BEHAVIORAL-FLOWS.md`
- `03-OPERATIONAL-FLOWS.md`
- `04-SYSTEM-ARCHITECTURE.md`
- `05-DATA-FLOW.md`
- `06-AUTHORIZATION-FLOWS.md`
- `07-ERROR-RECOVERY.md`
- `08-SECURITY-THREAT-MODEL.md`
- `09-OBSERVABILITY-AUDIT.md`
- `10-TEST-ACCEPTANCE.md`
- `11-DEPLOYMENT-OPERATIONS.md`
- `12-API-CONTRACTS.md`

In addition, require a real repository/branch/commit, reproducible setup, tests for yes and no paths at each decision gate, fail-closed authorization with a recorded denial, data lifecycle controls, redacted auditable telemetry, monitored runtime, incident ownership and demonstrated rollback/recovery. A build passing or a diagram rendering is not enough.

### C. Evidence dimensions

| Dimension | Required proof | Not sufficient on its own |
|---|---|---|
| Existence | Source repo, commit SHA, build/run instructions, artifact | Name, flowchart, case-study page |
| Behavior | Tests and observed behavior on positive and negative branches | Diagram, design mockup, passing typecheck |
| Security | Threat model, least privilege, denied-path tests, privacy controls | “Secure by design” statement |
| Operations | Telemetry, alerts, incident runbook, recovery and rollback evidence | Local demo or screenshot |
| Value | Validated user task and attributable outcome | Registrations, likes, impressions or an untested market estimate |

## 3. Research method to apply to each track

**Step 1 — Provenance recovery.** Find the original brief, repository, commits, designs, datasets, publications and decisions. Record URL/path, version, author, date, claim supported and limitations. Do not treat a generated summary as primary evidence.

**Step 2 — Problem discovery.** Interview users and buyers separately when they differ. Observe the existing task when possible. Record workarounds and actual behavior, not only expressions of interest.

**Step 3 — Alternatives.** Compare direct competitors, adjacent products, manual operations, internal systems and doing nothing. Establish a differentiated job and explicit non-goals.

**Step 4 — Feasibility and constraints.** Check current official API/SDK docs, data availability, license, platform terms, jurisdiction, model/hardware limits, cost and integration risk. Prototype the riskiest assumption first.

**Step 5 — Baseline and evaluation.** Define task-specific metrics before building. Examples: completion rate, false acceptance, false rejection, precision/recall, WER/CER, citation correctness, reconciliation accuracy, latency, cost per task, user correction effort. Derive thresholds from risk and baseline; do not invent universal targets.

**Step 6 — Negative and adversarial paths.** Test invalid input, insufficient evidence, unauthorized user, expired/revoked access, untrusted content, duplicate event, partial completion, timeout, dependency failure, rollback and deletion. Test the “no” path as deliberately as the happy path.

**Step 7 — Independent review and decision.** Have someone other than the author review the evidence. Record proceed/narrow/pivot/defer/archive/unknown. Preserve uncertainty; effort does not automatically earn a higher status.

## 4. Track-specific research and evidence requirements


### A. LOG_ON commercial systems

#### 1. LOG_ON Agency & LOG_ON OS
- **Current evidence / maturity:** Reported / in development.
- **Research:** Validate one target vertical and one paid business problem. Map the current workflow, buyer, user, budget owner, existing tools, operational constraints and measurable baseline. Do not treat the broad multi-agent OS concept as one MVP.
- **Research questions:** Which repeated workflow causes missed revenue, delay or avoidable cost? Who owns the budget? What can be automated safely? What requires human approval? What would make a business switch?
- **Evidence required:** Customer interviews and observed workflow; signed pilot scope and permission; baseline/target metric; bounded charter and non-goals; real product repository and commit; integration/data map; authorization tests; failed-action and rollback tests; operator/support ownership; measured pilot outcome with attribution limits.
- **First test:** Run one bounded workflow pilot with one real business; record baseline, consent, failure behavior and outcome.

#### 2. LOGON Insights Hub
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Validate the decision-making job before designing dashboards or AI summaries. Inventory actual source systems, data owners, metric definitions and freshness requirements.
- **Research questions:** Which decisions are currently delayed or poorly supported? Are metrics consistent across systems? What is the cost of a wrong insight? Which source is authoritative?
- **Evidence required:** Buyer/user interviews; decision map; metric dictionary; data contracts and source approvals; lineage/freshness checks; hand-calculated comparison set; tenant/role authorization tests; correction history; user task-completion test.
- **First test:** Select one important business decision and compare Hub output with a manually reconciled result.

#### 3. LOG_ON Reputation Intelligence
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Study review generation, private feedback and service recovery for local businesses. Verify channel access, platform rules and sentiment validity for Nigerian English, Yorùbá and Pidgin where in scope.
- **Research questions:** Which feedback should be public versus private? How is consent captured? How are fake reviews, selective review invitations and review gating prevented? Can sentiment labels be trusted?
- **Evidence required:** Channel/API permission; consent and opt-out; source-linked review records; duplicate handling; sentiment benchmark with human labels; approval logs; non-manipulation controls; response and escalation tests; measurable service-recovery outcomes.
- **First test:** Run an opt-in feedback journey with a small business. Verify that no review is fabricated, suppressed or selectively manipulated.

#### 4. LOG_ON Growth Systems
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Select one acquisition or conversion bottleneck. Validate local SEO, lead capture, WhatsApp follow-up, review journey and retention separately before bundling.
- **Research questions:** Where do leads drop out? Which follow-ups are permitted? What is the conversion baseline? Which outcomes can be attributed to the intervention?
- **Evidence required:** Funnel baseline; lead source and consent records; CRM/messaging permissions; campaign approval; delivery/failure logs; opt-out tests; attribution method; cohort comparison; owner-confirmed outcome and limitations.
- **First test:** Run a measured, opt-in experiment on one funnel stage. Do not claim ROI from impressions or message volume.

#### 5. Hotel / Clinic / Professional / SME OS
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Treat this as four vertical hypotheses, not one universal OS. Validate workflows, buyers, incumbent software, integrations and data sensitivity independently.
- **Research questions:** Which workflows are common and which are vertical-specific? What personal or health data is processed? Who authorizes access? Which existing systems cannot be replaced?
- **Evidence required:** Separate interviews and workflow maps per vertical; vertical charters and non-goals; data classification; integration proof; jurisdiction-specific legal review; role/permission matrix; prototype task tests; willingness-to-pay and cost-to-serve evidence.
- **First test:** Choose one vertical only after evidence of a repeat problem, budget owner and bounded workflow. Clinic-related functionality needs a separate privacy and clinical-governance review where applicable.

#### 6. Opportunity Exploration Engine / Pan-African Opportunity Scanner
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Test whether it discovers timely, actionable opportunities rather than noisy lists. Define geographies, sectors, source hierarchy, freshness and scoring logic.
- **Research questions:** Which opportunities count? What makes a source authoritative? How are stale or duplicate calls handled? Can scores be calibrated against human decisions and outcomes?
- **Evidence required:** Dated source register; taxonomy; deduplication and expiry rules; scoring rubric; retrospective precision/recall sample; independent reviewer ratings; owner/eligibility checks; action outcome tracking; conflict-of-interest disclosure.
- **First test:** Assemble a historical opportunity set and have independent reviewers score relevance before automating discovery.

#### 7. Global AI Business Intelligence Agent / OpenServ track
- **Current evidence / maturity:** Reported / research.
- **Research:** Evaluate source-grounded market intelligence and opportunity recommendations. Verify the current OpenServ integration status and distinguish discovery, recommendation and execution.
- **Research questions:** Which decisions does the agent support? Which sources are primary? How are claims timestamped and cross-checked? What API capabilities and permissions are actually available?
- **Evidence required:** Research question and user; source/API inventory; claim-level citations; source freshness checks; contradiction handling; benchmark against human reviewers; opportunity scoring evaluation; tool permission matrix; approval/denial tests; actual repository and integration traces.
- **First test:** Run a research-only benchmark that produces cited intelligence without contacting people, applying or initiating external actions.

#### 8. LOG_ON Agent Assurance
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Identify the buyer, assurance scope and evidence that can be reliably collected from agent systems. Distinguish configuration review, adversarial testing and runtime monitoring.
- **Research questions:** Who accepts agent risk? Which controls can be measured? What can telemetry prove without collecting secrets? Which assurance claims are outside scope?
- **Evidence required:** Buyer interviews; service charter and exclusions; control catalogue; threat model; repeatable test harness; sample report; false-positive/negative review; remediation workflow; reviewer qualifications; pricing and delivery-cost model.
- **First test:** Perform one explicitly non-certifying assessment of a bounded agent workflow and report findings with source evidence and limitations.

### B. Agent infrastructure and assurance

#### 9. AgentBridge-Africa
- **Current evidence / maturity:** Reported / in development.
- **Research:** Verify the real execution and authorization boundary: identity, capability scope, policy decision, tool use, side effects and evidence capture.
- **Research questions:** What is the runtime contract? How are agents registered? How are tools scoped? How are revocation, replay, retries, partial side effects and prompt injection handled?
- **Evidence required:** Actual repository/branch/commit; runtime architecture and threat model; identity/capability registry; allow/deny tests; scoped credential tests; tool-injection scenarios; sandbox evidence; secret redaction; idempotency and external reconciliation; kill-switch and recovery test.
- **First test:** Demonstrate one low-risk tool action and its denied counterpart with a complete authorization and outcome trace.

#### 10. ArchAudit-CCM
- **Current evidence / maturity:** Reported / in development.
- **Research:** Prove deterministic, repeatable control evaluation with known evidence provenance. Do not equate a dashboard or control mapping with compliance certification.
- **Research questions:** Which framework/version is mapped? What evidence proves a control? How are stale, missing or contradictory artifacts handled? How are rules versioned and tested?
- **Evidence required:** Control catalogue and mapping rationale; versioned deterministic rules; evidence schema/provenance; known-answer fixtures; replay tests; missing/stale evidence cases; false-positive/negative review; finding/remediation/retest audit trail; report limitations.
- **First test:** Implement one control family with synthetic fixtures and prove the same inputs produce the same result; missing evidence must never produce a pass.

#### 11. SafeChain
- **Current evidence / maturity:** Reported / prototype.
- **Research:** Determine whether a tamper-evident ledger is actually needed versus a signed append-only database.
- **Research questions:** Who needs independent verification? Why is decentralization needed? Who operates validators? What are finality, privacy, key-loss, throughput and cost requirements?
- **Evidence required:** Original use case; alternatives analysis; threat model; network/consensus rationale; contract audit; key-management/recovery tests; reorg/finality tests; privacy assessment; gas/latency benchmark; reproducible testnet evidence; explicit prototype boundary.
- **First test:** Compare the blockchain design with a conventional append-only design under the same threat model.

#### 12. GRC Agent Studio
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Identify GRC tasks suitable for assisted evidence gathering and mapping; preserve human accountability for risk acceptance and legal conclusions.
- **Research questions:** Which frameworks are in scope? Who owns risk acceptance? Can generated mappings be challenged? How are segregation of duties and evidence citations handled?
- **Evidence required:** Practitioner/buyer interviews; versioned framework mapping; source provenance; roles/segregation matrix; recommendation tests; citations; approval/rejection audit; qualified reviewer sign-off; model limitations.
- **First test:** Prototype one evidence-collection or control-mapping task with a qualified human reviewer.

#### 13. Relaywise
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry. Working name.
- **Research:** Define what a node is and distinguish this track from AgentBridge execution and FlowRail orchestration.
- **Research questions:** Are nodes agents, services, devices or workflow endpoints? How are they discovered/authenticated? What delivery guarantees and loop prevention are needed?
- **Evidence required:** Product boundary and terminology; actor/use-case interviews; node identity/capability contract; routing protocol; authorization model; retry/expiry tests; duplicate/loop tests; node failure and revocation scenarios.
- **First test:** Validate one node-to-node use case and compare it with direct API orchestration.

#### 14. FlowRail
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry. Working name.
- **Research:** Validate durable workflow orchestration requirements and compare with established workflow engines and managed services.
- **Research questions:** What state survives worker failure? How are idempotency, cancellation, compensation and workflow version changes represented? Who operates queues and workers?
- **Evidence required:** Alternatives comparison; workflow/state model; persistence contract; retry/backoff tests; crash/replay tests; cancellation/compensation tests; version migration tests; throughput/latency/cost benchmarks.
- **First test:** Build a failure-injection prototype around one multi-step workflow and compare recovery behavior with an established option.

#### 15. SignalLedger
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry. Working name.
- **Research:** Define the reconciliation domain and determine whether this is an event ledger, reconciliation service or audit interface.
- **Research questions:** Which systems emit expected/actual events? How are events correlated and ordered? How are late or duplicate events treated? Who resolves exceptions?
- **Evidence required:** Domain event dictionary; source identifiers; storage integrity rationale; idempotency/ordering tests; reconciliation fixtures; mismatch workflow; audit integrity; exception ownership and resolution-time measures.
- **First test:** Use test events containing duplicates, out-of-order records and mismatches; prove every exception is explainable.

#### 16. FoundryKit
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry. Working name.
- **Research:** Define evaluation contracts and reproducibility before building a general benchmark platform.
- **Research questions:** Who owns datasets? How are licensing, leakage and contamination controlled? Which metrics represent target behavior? How is evaluator uncertainty measured?
- **Evidence required:** Benchmark contract; dataset provenance/license; immutable split/version IDs; leakage checks; baseline runs; reproducibility; metric definitions; human-labelled test set; adversarial cases; evaluator agreement and uncertainty.
- **First test:** Run the same pinned benchmark twice and verify identical inputs, configuration trace and explainable variance.

#### 17. PatchPilot
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry. Working name.
- **Research:** Define the user job, autonomy boundary and repository permissions required for safe AI-assisted maintenance.
- **Research questions:** Who authorizes changes? Can the agent access secrets? How are commands sandboxed? What files are in scope? What must pass before merge?
- **Evidence required:** Threat model; repository permission matrix; isolated environment; malicious instruction/dependency tests; branch/diff evidence; test-quality evaluation; secret scanning; human review; rollback; build provenance.
- **First test:** Start read-only, then perform a branch-only patch that requires human approval before merge.

#### 18. Cognitive Protocol
- **Current evidence / maturity:** Reported / research.
- **Research:** Recover the original seven-step loop, prediction gates and telemetry definitions. Establish the problem and falsifiable hypothesis before claiming cognitive or capability improvement.
- **Research questions:** Which behavior is improved or constrained? What exactly is a prediction gate? How is friction measured? What are measurable outcomes and counterexamples?
- **Evidence required:** Original protocol/version; construct definitions; hypotheses; task benchmark; baseline comparison; telemetry schema; privacy boundary; user-study method; independent review/replication plan.
- **First test:** Convert every protocol step into observable behavior and test on one bounded task.

#### 19. FDE-Platform-2026
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Study repeatable customer-specific deployment, configuration, observability and support for forward-deployed engineering.
- **Research questions:** Who are the FDE users? What is deployed per customer? Which steps are reusable versus manual? How are upgrades and incidents handled?
- **Evidence required:** FDE/customer interviews; engagement journey; tenancy/deployment model; environment provisioning; secrets/configuration model; observability; release/rollback; incident process; support model; repeatability and unit economics.
- **First test:** Map one real deployment lifecycle and classify every step as reusable, manual, customer-specific or unsafe to automate.

### C. Multilingual and cultural intelligence

#### 20. PAL — culturally grounded meaning and action platform
- **Current evidence / maturity:** Reported / research.
- **Research:** Test whether PAL preserves pragmatic, cultural and discourse meaning across Yorùbá, Nigerian Pidgin and code-switched contexts—not merely literal translation or transcription.
- **Research questions:** Which languages, varieties, domains and modalities are in scope? What counts as pragmatic meaning? How are speaker disagreements and contested interpretations represented? Which actions may safely be proposed?
- **Evidence required:** Corpus/source register with consent and license; orthography/normalization policy; original/canonical/search forms; annotation handbook; native-speaker and linguist review; disagreement measures; held-out dialect/domain tests; baseline comparisons; provenance hashes; abstention and human-approval tests.
- **First test:** Define one discourse task and create a small consented, reviewed benchmark. Existing Yorùbá resources are candidate inputs, not proof that PAL's code-switch or pragmatic-action goal is covered.

#### 21. CIE — Contextual Intelligence Exploration
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Define context as observable, annotatable dimensions rather than an unbounded claim of cultural understanding.
- **Research questions:** Which context features change interpretation? Which are speaker-supplied versus inferred? How is missing context represented? What must the system not infer?
- **Evidence required:** Operational definition and taxonomy; annotation guide; context-labelled sample; inter-annotator agreement; ablation tests; ambiguity/abstention set; dialect/subgroup analysis; counterexamples and limitations.
- **First test:** Test whether explicit context improves a defined task over a text-only baseline without increasing unsupported cultural assumptions.

#### 22. DAPF — Discourse-Adaptive Prompting Framework
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Determine whether discourse-adaptive prompting improves performance beyond a fixed prompt or standard context template.
- **Research questions:** Which signals trigger adaptation? How is the adaptation policy selected? Does it generalize across languages/tasks? What are token, latency, cost and regression effects?
- **Evidence required:** Formal method; versioned prompts; fixed baseline; held-out tasks; ablations; blinded human evaluation; failure taxonomy; prompt-injection tests; cost/latency; reproducible experiment scripts.
- **First test:** Compare pinned prompts/models/datasets under controlled conditions and report gains and regressions.

#### 23. Proverb Activation Library
- **Current evidence / maturity:** Reported / historical activity; maturity should be unknown.
- **Research:** Archive the historical asset and map its source material, concepts and methods to current PAL work without presenting it as an active product.
- **Research questions:** What corpus, schema, ontology and provenance exist? What is reusable, superseded or restricted? Which ideas were transferred into PAL?
- **Evidence required:** Original files/commit history; provenance/license; dated scope; ontology/version; examples; limitations; PAL crosswalk; archival or supersession decision.
- **First test:** Produce an archival record and crosswalk. No new performance or product claim without a fresh research plan.

#### 24. Sahara CodeSwitch
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Evaluate code-switch-aware speech recognition and language identification at switch boundaries in realistic conversation.
- **Research questions:** Which language pairs and switching patterns are in scope? How are switch boundaries annotated? How do accent, noise, channel and speaker variation affect error?
- **Evidence required:** Consented/licensed audio; language-pair and speaker metadata; annotation guidelines; speaker-separated train/dev/test; WER/CER and switch-region error; language-ID accuracy; noise/channel slices; latency and confidence calibration.
- **First test:** Create a held-out speaker set and compare a general ASR baseline with any adapted approach; report switch-region error separately from aggregate WER.

#### 25. wwhisper
- **Current evidence / maturity:** Reported / in development.
- **Research:** Verify the repository's actual transcription pipeline and evaluate the languages, code-switch patterns and recording conditions it supports.
- **Research questions:** Which components actually run? Which providers/models are called? Are timestamps, diarization and confidence supported? What happens on provider outage or unsupported language?
- **Evidence required:** Current repo/commit/dependencies; model/provider configuration; licensed test audio; WER/CER by language/accent; timestamp/diarization metrics if claimed; latency/cost; failure/fallback tests; API key handling; data-retention behavior.
- **First test:** Run a reproducible evaluation against the current branch. Recheck any earlier integration description against code before publishing it as current.

#### 26. OMI Edge Ear
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Validate edge audio capture and gateway feasibility, usability and privacy in actual environments.
- **Research questions:** What hardware is targeted? What audio formats and sample rates? What BLE/Wi-Fi range, battery, offline and reconnect behavior is needed? What is stored locally?
- **Evidence required:** Hardware bill of materials; device capability matrix; audio/noise tests; battery/thermal measures; packet-loss/reconnect tests; secure pairing; visible consent indicators; offline buffer/deletion tests; usability study.
- **First test:** Build a limited hardware proof before promising device compatibility or always-on behavior.

#### 27. Meaning-to-Action Kernel 2.1
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Specify the boundary between understanding an utterance, proposing an action and authorizing that action.
- **Research questions:** How is intent represented? How are uncertain or conflicting interpretations exposed? Which side effects require confirmation? How are principal, scope and revocation enforced?
- **Evidence required:** Versioned intent/action schema; ambiguity benchmark; confidence calibration; action policy table; allow/deny tests; replay/duplicate tests; approval UX tests; external outcome verification; trace evidence.
- **First test:** Test ambiguous, misheard and injected commands. A plausible action plan must never be enough to execute an action.

#### 28. Composer’s Voice Twin
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Clarify whether “voice twin” means voice persona, interaction style, TTS adaptation, speaker likeness or another capability. Do not assume cloning.
- **Research questions:** What user problem is solved? Does it synthesize or imitate a real speaker? What consent/identity evidence is needed? Can a person revoke and delete voice data?
- **Evidence required:** Capability boundary; consent and rights model; impersonation threat assessment; speaker-data provenance; quality tests if synthesis is in scope; revocation/deletion tests; abuse scenarios; jurisdiction review.
- **First test:** Resolve the capability definition before choosing models or claiming voice-replication features.

#### 29. Voice / STT Adapters
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Define a provider-neutral contract for speech input, language metadata, timestamps, confidence, errors and privacy settings.
- **Research questions:** Which providers/on-device engines are required? Which fields are mandatory? How are unsupported languages, streaming, retries and provider-specific behavior represented?
- **Evidence required:** Adapter interface/schema; provider capability matrix; contract tests; language fixtures; timeout/retry/fallback tests; secret redaction; consent/retention propagation; version compatibility tests.
- **First test:** Implement one adapter with a conformance suite before adding providers. Do not imply provider parity where capabilities differ.

#### 30. Cultural Compression
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Operationalize the concept: identify what cultural or pragmatic information is lost when a message is compressed or summarized.
- **Research questions:** Which information units matter? Who judges preservation? How are contested interpretations represented? Is loss measurable across task types?
- **Evidence required:** Concept definition; taxonomy of information loss; consented source/summary pairs; community/linguist annotations; inter-rater agreement; task-based preservation metric; baseline; counterexamples and limitations.
- **First test:** Start with a qualitative study and annotated examples. Do not claim a validated metric until measurement reliability is established.

#### 31. Epistemic Translation Loss
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Study whether translation or cross-language summarization changes certainty, attribution, negation, evidentiality or claim strength.
- **Research questions:** Which epistemic markers must be preserved? How do dialect and discourse context affect them? What is the unit of analysis? How are human disagreements handled?
- **Evidence required:** Operational definition; bilingual source/target corpus; claim and uncertainty annotations; linguist review; agreement measures; error taxonomy; baseline comparisons; held-out language/domain evaluation.
- **First test:** Build a claim-preservation benchmark for possibility, obligation, hearsay, negation, attribution and uncertainty.

#### 32. Salience-Weighted Recall
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Define salience and test whether weighted retrieval improves task success without over-retaining sensitive or outdated information.
- **Research questions:** What determines salience? Who controls it? How does it decay? Can users correct/delete it? Does personalization produce unwanted recall?
- **Evidence required:** Relevance rubric; task/query benchmark; baseline retrieval; precision/recall@k; stale/conflicting memory cases; correction tests; deletion propagation; privacy and surprise-recall study.
- **First test:** Compare against a simple recency/relevance baseline on synthetic or properly governed data.

#### 33. Discourse-Native Benchmarks
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Design evaluation tasks for discourse context, code-switching, pragmatics and multi-turn meaning rather than isolated sentence translation only.
- **Research questions:** Which phenomena are represented? Are examples naturally occurring or elicited? How is contamination prevented? How are varieties and communities represented?
- **Evidence required:** Benchmark specification; provenance/license; task taxonomy; annotation handbook; reviewer agreement; train/dev/test split; baseline scores; contamination checks; versioning and challenge set.
- **First test:** Publish limitations and baseline results before claiming a model ranking or broad language capability.

#### 34. African Cognitive AI Programme
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Define the programme agenda, community governance, language priorities and measurable research outputs.
- **Research questions:** Which communities/institutions participate? Who sets priorities? Who governs data and benefit sharing? What qualifies as programme impact?
- **Evidence required:** Programme charter; stakeholder/advisory record; research ethics process; data stewardship and benefit-sharing principles; workstream plans; partner/funding evidence; publication/release criteria; outcome reporting.
- **First test:** Establish a bounded, community-informed research agenda before aggregating projects under a programme identity.

### D. Context, memory and productivity

#### 35. ContextPocket
- **Current evidence / maturity:** Reported / in development.
- **Research:** Verify current capture, search, permission and memory-lifecycle behavior. Focus on authorization, deletion and actual client approval behavior.
- **Research questions:** Which sources are connected? What is persistent versus ephemeral? How does tenant isolation work? What do Bearer/MCP paths authorize? Is OAuth background sync implemented now? How are corrections and deletions propagated?
- **Evidence required:** Current repository/branch/commit; schema/migrations; auth tests; MCP capture/search integration tests; tenant isolation; storage-denied/ephemeral path; deletion/expiry; memory-injection and poisoning tests; approval tests in target clients; CI/current failures; telemetry that excludes secrets and content by default.
- **First test:** Re-run current tests and add real-client approval, revoke and deletion tests. Earlier implementation notes are historical owner reports until rechecked.

#### 36. RecallGrid
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry. Working name.
- **Research:** Determine whether a memory mesh solves a distinct problem from ContextPocket; define node ownership, federation and trust.
- **Research questions:** What are nodes? Who owns each store? Is retrieval federated or replicated? How are conflicting, revoked or deleted memories reconciled?
- **Evidence required:** Differentiated charter; topology/trust model; federation contract; identity/authorization propagation; provenance/conflict tests; node partition/failure tests; deletion/revocation propagation; centralized-versus-mesh cost and latency comparison.
- **First test:** Validate one cross-node retrieval case and prove why a separate product boundary is needed.

#### 37. Re:Mind Me
- **Current evidence / maturity:** Reported / in development.
- **Research:** Verify capture-to-reminder reliability: extraction of commitments, date/time disambiguation, scheduling, delivery and user correction.
- **Research questions:** Which capture sources are currently connected? How are commitments distinguished from mentions? How are relative dates/time zones resolved? What does the user confirm before scheduling?
- **Evidence required:** Current repository/migrations; authenticated capture tests; extraction precision/recall on consented examples; timezone/ambiguity tests; duplicate reminder tests; scheduler reliability; notification receipts; reschedule/complete/delete tests; connector permission/revocation; export/retention record.
- **First test:** Test the complete lifecycle from capture to delivered reminder across time zones. Recheck old Supabase/MCP and test-failure notes against the current branch.

#### 38. Canonpath
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry. Working name.
- **Research:** Identify the exact document workflow and meaning of a canonical record; avoid building a generic document platform without a user and document class.
- **Research questions:** Which documents? Who is the system of record? What are review, approval, amendment and retention rules? Which storage/records tools must coexist?
- **Evidence required:** Document-type inventory; user/approver interviews; version/provenance model; role/permission matrix; integrity/hash tests; revision/diff tests; approval/rejection; export fidelity; retention/deletion; integration proof.
- **First test:** Prototype one document type and prove version lineage, approval and reversible publication.

### E. Consent and voice interaction

#### 39. MorrowVoice
- **Current evidence / maturity:** Reported / in development.
- **Research:** Verify consent is enforced by an authoritative kernel rather than interface state. Test principal authority, revocation, delegation and default retention/sharing behavior.
- **Research questions:** Who is the principal for each action? How is delegation represented? What are consent scope and expiry? Can an operator override an adult principal? What remains when retention is off?
- **Evidence required:** Canonical consent policy/threat model; principal/delegate test matrix; default-deny tests; revoke-before/during/after-action; retention-off and sharing-off; cross-user isolation; spoof/replay tests if identity features exist; audit evidence; real-client behavior; deletion proof.
- **First test:** Test consent in a real client and direct API path. A UI switch alone does not prove consent authority.

#### 40. SpeakBridge
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry. Working name.
- **Research:** Define its distinct role relative to MorrowVoice, wwhisper and voice adapters: session management, voice operations or an integration product.
- **Research questions:** What is session identity? Who controls capture/playback? Which services are orchestrated? What persists after session closure?
- **Evidence required:** Scope/boundary document; session state machine; audio consent/indicators; identity/role tests; interruption/reconnect; session isolation; retention controls; provider failure tests; architecture comparison with existing components.
- **First test:** Document the differentiated user job before building a second voice stack.

### F. Evidence and entity intelligence

#### 41. GroundedGuide
- **Current evidence / maturity:** Reported / in development.
- **Research:** Validate its user task, guidance domain and sources. Evaluate evidence fidelity, citations, conflict handling and abstention when evidence is insufficient.
- **Research questions:** Which domains/tasks are supported? Which sources are authoritative and current? How are conflicts represented? What is sufficient evidence? How are citations checked?
- **Evidence required:** Current repository/charter; source registry/update policy; retrieval recall/precision; claim-level citation precision/coverage; faithfulness/correctness evaluation; stale/conflicting-source tests; abstention calibration; prompt-injection cases; user task tests; domain limitations.
- **First test:** Build questions with independently verified answers and measure source retrieval, claim support and correct abstention. Keep public differentiation independent of any private reverse-engineering reference.

#### 42. EntityLens
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry. Working name.
- **Research:** Validate an entity-resolution use case and false-match cost for one domain.
- **Research questions:** Which entities and identifiers? What ambiguity requires human review? Who may correct/dispute profiles? Which relationships can be published?
- **Evidence required:** Domain/buyer definition; source inventory; resolution features; precision/recall at threshold; false-merge analysis; claim/edge provenance; correction/dispute process; privacy/retention review; refresh/deletion tests.
- **First test:** Evaluate on a labelled entity set and prioritize false merges and correction paths, not only match rate.

### G. Domain and marketplace products

#### 43. GigPilot
- **Current evidence / maturity:** Reported / prototype.
- **Research:** Verify marketplace liquidity and trust. Test whether employers have repeat demand and workers receive suitable, safe and accurately described opportunities.
- **Research questions:** Which job categories, geography and worker segments are in scope? Who pays? How are employers verified? How are disputes, cancellations, payment and worker protections handled?
- **Evidence required:** Current repo/prototype; employer and worker interviews; eligibility rules; employer verification; matching relevance; fraud/abuse controls; application/completion funnel; dispute/payment reconciliation; privacy review; jurisdiction-specific worker classification and contract review.
- **First test:** Run a narrowly scoped pilot in one job category and geography; measure both sides of liquidity, completion and disputes, not registrations alone.

#### 44. HouseHunter
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Validate buyer/tenant pain, listing quality and property verification in a specified geography before defining matching features.
- **Research questions:** Is the user a renter, buyer, agent or landlord? Which locations and transaction types? How are listings refreshed? What records verify authority to list or ownership?
- **Evidence required:** Geography-specific discovery; listing-source permissions; freshness/duplicate tests; agent/owner verification; property-document checklist reviewed by qualified local professionals; scam/report path; matching tests; trust/conversion evidence.
- **First test:** Start with discovery and listing verification in one location. Do not claim title verification without authorized records and qualified review.

#### 45. Peculiar
- **Current evidence / maturity:** Unknown / domain and maturity must remain unassigned until source recovery.
- **Research:** Recover identity before researching a market or assigning a product domain. The name alone is not evidence.
- **Research questions:** What was Peculiar? Who described it? Is there a brief, repository, design file, prior conversation or source artifact? What must not be claimed? Should the record remain unknown?
- **Evidence required:** Original owner description or source artifact; provenance/date; confirmed scope and non-scope; record owner; explicit decision to retain unknown or reclassify; change history. No inferred domain, users, clinical claim or feature list.
- **First test:** Keep the record minimal and Unknown until the owner supplies or confirms an authoritative description.

#### 46. ToolScout
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Validate the tool-selection job and trust model for discovery and comparison.
- **Research questions:** Who selects tools and for what task? Which criteria matter—capability, cost, privacy, security, integration, support? How are stale or sponsored claims handled?
- **Evidence required:** Tool taxonomy; dated and source-linked vendor claims; update/expiry policy; comparison methodology; reproducible task benchmarks; sponsorship/affiliate disclosure; user decision study; vendor correction mechanism.
- **First test:** Compare a user's tool decision against their current search/spreadsheet process and test whether the result is better supported.

#### 47. Curriculum LMS
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Identify learner, instructor and institutional context; define learning outcomes rather than optimizing for content volume or time-on-platform.
- **Research questions:** Who creates/owns curriculum? What assessment proves learning? Is delivery cohort-based or self-paced? What accessibility, offline and privacy needs exist?
- **Evidence required:** Instructor/learner interviews; curriculum schema; assessment validity review; outcome measures; accessibility tests; grading/feedback; content rights; cohort/progress privacy; export/deletion; pilot mastery evidence.
- **First test:** Pilot one course with defined pre/post learning objectives and review assessment quality.

#### 48. BatchLedger
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry. Working name.
- **Research:** Map the craft-distillery operating model and establish target jurisdiction before designing inventory, batch and regulatory functionality.
- **Research questions:** Which products and batch processes? How are lots, loss, yield, quality and cost recorded? What traceability, licensing, tax/excise, food/beverage and labelling rules apply?
- **Evidence required:** Distillery operator interviews; process observation; batch/lot schema; yield/cost reconciliation; quality/quarantine/recall scenarios; roles; audit exports; jurisdiction-specific regulatory register reviewed by qualified counsel/regulatory expert. In Nigeria, verify the exact NAFDAC product category and applicable rules rather than assuming a generic alcohol workflow.
- **First test:** Validate one batch from raw-material receipt through finished-goods reconciliation with an operator.

#### 49. SiteSpan Ops
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry. Working name.
- **Research:** Treat scaffolding as a safety-critical operational workflow, not just a sales CRM.
- **Research questions:** Which jurisdiction and standards apply? Who is competent to inspect? What evidence is required before handover? How are equipment, crew, site changes, weather and defects handled?
- **Evidence required:** Contractor interviews; site-process observation; inspection/handover forms; equipment traceability; crew competency evidence; hazard and stop-work paths; schedule/quotation flow; incident/corrective-action records; jurisdiction-specific safety review.
- **First test:** Prototype one job from enquiry/survey through readiness, installation, inspection and handover. For Nigeria, consult the Ministry of Labour's OSH framework; do not automatically import UK or US requirements.

### H. Creator and collaboration systems

#### 50. Clip Creator Studio / CLIPIN
- **Current evidence / maturity:** Reported / in development.
- **Research:** Verify end-to-end media-to-clips behavior and ensure media access, transformation and publishing comply with rights and platform terms.
- **Research questions:** Which files/URLs are supported? What rights does the user have? Are transcripts, timestamps and clips accurate? Which publishing APIs and OAuth scopes are truly available?
- **Evidence required:** Current repository/pipeline proof; user rights declaration; ingestion/deletion tests; transcript/timestamp accuracy; highlight-selection evaluation; render QA; export integrity; provider/API policy review; OAuth scope/revocation; queue/retry/cost monitoring; end-to-end test using rights-cleared media.
- **First test:** Demonstrate one rights-cleared asset from ingestion through transcript, clip choice, rendering, approval and export. YouTube API access is not a blanket permission to download or republish arbitrary content.

#### 51. SceneMint
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry. Working name.
- **Research:** Clarify whether this is an explainer, visual authoring tool or asset workflow, and validate the user and output.
- **Research questions:** Who supplies the brief? What claim/concept must be explained? How is semantic fidelity checked? What accessibility and asset-rights rules apply?
- **Evidence required:** Target-user interviews; brief-to-output study; claim traceability; layout/readability evaluation; visual QA rubric; asset provenance/license; accessible output tests; revision/approval; render/export integrity.
- **First test:** Test a small set of real briefs with users and subject reviewers; measure comprehension as well as aesthetic preference.

#### 52. Creative Systems Prompt Compiler
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Determine whether structured compilation improves prompt completeness, controllability and repeatability compared with a normal creative brief.
- **Research questions:** Which input fields matter? How are contradictions and missing constraints handled? Which model/tool output formats are supported?
- **Evidence required:** Input/output schema; versioned templates; validation tests; ambiguity/contradiction fixtures; before/after task evaluation; output consistency; model/tool compatibility; cost/latency; reviewer corrections.
- **First test:** Compare an unstructured brief with a compiled specification on identical tasks using blinded review and explicit acceptance criteria.

#### 53. Human–AI Multi-Lane Protocol
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Define lanes, authority, ownership and handoff semantics for human/AI collaboration.
- **Research questions:** Which actor owns each decision? What is delegated? How are uncertainty and disagreement escalated? How is work resumed after handoff?
- **Evidence required:** Protocol definition; role/permission matrix; task state machine; handoff schema; accountability/provenance records; task benchmark; rework/error rate; override/escalation tests; comparative user study.
- **First test:** Pilot one bounded workflow and measure handoff loss, completion quality, correction effort and user control.

#### 54. Creative Workbench
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Map creator workflows and identify repeated friction that justifies a dedicated workspace.
- **Research questions:** Which creators/disciplines? Which artifacts are managed? What tools already own files? What version, collaboration, import/export and rights needs exist?
- **Evidence required:** Creator interviews; observed task maps; asset/file model; version history; import/export fidelity; collaboration permissions; usability tests; integration feasibility; backup/recovery; adoption or willingness-to-pay evidence.
- **First test:** Build a thin workflow around one repeated task and compare it with the creator's current toolchain.

#### 55. Idea Ledger
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Determine whether the user needs idea capture, searchable recall, decision history or a pathway from ideas to shipped work; these are different jobs.
- **Research questions:** How are ideas captured? What source/context is retained? How are duplicates, decisions and abandoned ideas represented? What retrieval task matters?
- **Evidence required:** Capture/retrieval interviews; data schema; provenance/link tests; search evaluation; correction/merge/delete; decision history; privacy/retention; longitudinal adoption evidence.
- **First test:** Test whether users can retrieve and act on a past idea more reliably than with their current notes and chat history.

#### 56. PublishRail
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry. Working name.
- **Research:** Research a real editorial publishing workflow and determine what differentiates it from an ordinary CMS.
- **Research questions:** Who authors, edits, approves and publishes? What content types/destinations exist? How do scheduling, rollback, canonical URLs and accessibility work?
- **Evidence required:** Editorial interviews; content schema; role/approval matrix; draft/version tests; scheduling/timezone tests; publication verification; unpublish/rollback; preview security; SEO/accessibility; integration/migration assessment.
- **First test:** Pilot one content type and publishing destination with full approval and rollback evidence.

#### 57. LOG_ON Prompt Pattern Library v1.0
- **Current evidence / maturity:** Reported / in design.
- **Research:** Recover and validate patterns P01–P06: definitions, versions, intended use, limitations and examples. Do not claim the patterns improve outcomes without a comparison study.
- **Research questions:** What problem does each pattern solve? Which model/task context is assumed? How are failure and unsafe use described?
- **Evidence required:** Canonical source; version history; authorship/provenance; examples; schema validation; ambiguity and injection cases; baseline comparison; human-rated outcome study; limitations/update policy.
- **First test:** Publish as a versioned knowledge asset with tested examples and explicit limitations, not a performance claim.

### I. Cognitive systems and portfolio engineering

#### 58. Cognitive Gym
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Operationalize cognitive offloading, dependency and skill retention before designing an evaluation product or making causal claims.
- **Research questions:** Which cognitive skills/tasks are measured? What counts as dependency? What is the time horizon? How are practice effects, baseline ability and task difficulty controlled?
- **Evidence required:** Research protocol; construct definitions; literature review; consent/ethics review; preregistered hypotheses where appropriate; baseline and delayed measures; comparison condition; objective task performance; self-report instruments; confounder analysis.
- **First test:** Run a bounded research study. Do not label people cognitively dependent from one usage metric or questionnaire.

#### 59. Portfolio Advancement
- **Current evidence / maturity:** Reported / in development.
- **Research:** Verify how ideas are selected, evidenced, prioritized, funded, spun out, paused or retired. Ensure the process does not reward speculative output over validated demand.
- **Research questions:** What are the stage gates? What advances a track? How are duplicates merged? How are commercial value, feasibility, risk and owner capacity weighted?
- **Evidence required:** Versioned intake schema; decision criteria/scoring rationale; source links; stage history; reviewer decisions; rejected/deferred reasons; historical calibration; conflict/ownership rules; portfolio outcomes/cycle time.
- **First test:** Apply the existing portfolio to transparent decision gates and review whether results are defensible.

#### 60. LOG_ON Main Repository / Portfolio Source of Truth
- **Current evidence / maturity:** Reported / in development.
- **Research:** Verify that the registry is authoritative and that counts, filters, links, relationships and evidence fields remain internally consistent.
- **Research questions:** What is the stable project ID? How are statuses versioned? How are aliases and historical evidence retained? How are migrations and broken references detected?
- **Evidence required:** Schema/migrations; 66 unique stable IDs; count reconciliation; source provenance; independent activity/maturity/evidence/naming fields; relation validation; search/filter tests; audit history; backup/export/restore; browser/accessibility tests.
- **First test:** Add automated invariants: 66 unique track IDs; evidence counts reconcile to records; historical activity is not maturity; unknown records stay unknown.

### J. Historical and retained assets

#### 61. Omdena RAG Mental-Health Chatbot
- **Current evidence / maturity:** Reported / historical activity; maturity should be unknown.
- **Research:** Preserve what was actually built without treating it as a clinical service or implying clinical effectiveness.
- **Research questions:** What was the original question? Which data/model were used? What did the reported evaluation measure? Were clinicians or ethics reviewers involved? What were the limitations?
- **Evidence required:** Original repo/brief; dataset/model provenance and licenses; evaluation code and metric definition; intended-use statement; safety/escalation design; expert/ethics review if any; limitations and archive note. No clinical efficacy claim without appropriate evidence and governance.
- **First test:** Archive with clear historical labeling. Reactivation requires a fresh clinical, privacy, safety and regulatory review.

#### 62. ASE MVP (historical name)
- **Current evidence / maturity:** Reported / historical activity; maturity should be unknown.
- **Research:** Recover the legacy artifact and determine whether it remains archived, is superseded or has reusable components.
- **Research questions:** What did ASE mean in that project? Which repository/scope existed? What functionality was real? What replaced it?
- **Evidence required:** Original source and commits; README/spec; dated screenshot/demo evidence; dependency/license inventory; limitations; successor mapping; archive decision. Do not use ASE as the current agency brand.
- **First test:** Produce a historical record and migration map only; no relaunch or present-tense claim without a new charter.

#### 63. Prompt Protocol Atlas
- **Current evidence / maturity:** Reported / historical activity; maturity should be unknown.
- **Research:** Verify bibliographic record, publication artifact, DOI, authorship, scope and relationship to current work.
- **Research questions:** Does the DOI resolve to the claimed publication? What was actually published or reviewed? What artifact/version exists? Which claims are in the work versus later interpretations?
- **Evidence required:** Publisher/DOI metadata; final paper/proceedings; authorship record; citation; artifact/version; publication status; errata/follow-up. Separate publication evidence from implementation evidence.
- **First test:** Preserve a verified citation and explain its relevance; do not represent the publication as a running product.

#### 64. Behavioral Intelligence Layer
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Define the exact workflow signals required and challenge whether this component is necessary. Guard against covert profiling and sensitive-trait inference.
- **Research questions:** Which events are collected and for what purpose? Who can inspect them? What inferences are prohibited? How can a person correct, opt out or delete?
- **Evidence required:** Purpose/data-minimization assessment; event taxonomy; privacy impact assessment where required; prohibited-inference policy; notice/consent; retention/deletion tests; bias/error analysis; role access; transparency/correction UX.
- **First test:** Start with non-sensitive workflow analytics. Do not infer health, politics, religion or other sensitive personal attributes.

#### 65. PAL Mobile Gateway
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Validate the mobile gateway as a distinct bridge between edge audio devices, speech services and action orchestration.
- **Research questions:** Which device/protocol interfaces are supported? What audio is buffered? What happens offline? How is consent propagated? Which service owns secrets and retry state?
- **Evidence required:** Protocol/interface contract; BLE/Wi-Fi pairing; packet-loss/reconnect; audio integrity; offline queue/deletion; encryption/token scope; consent propagation; latency/battery measures; end-to-end trace with redaction.
- **First test:** Prove one device-to-gateway-to-STT path under normal, interrupted and denied-consent conditions before enabling action execution.

#### 66. GigPilot Six-Agent Workforce
- **Current evidence / maturity:** Proposed / maturity to be reconciled from the registry.
- **Research:** Test whether six agents improve one defined GigPilot task over a simpler workflow; define responsibility and permission for each agent.
- **Research questions:** What are the six roles? Which output is authoritative? How is shared state reconciled? Which agent can contact users, change job status or trigger payment-related work?
- **Evidence required:** Agent role/authority matrix; single-agent baseline; task benchmark; handoff/conflict tests; prompt injection across agent messages; tool scope/permission tests; approval gates; audit trace; latency/cost and error comparison.
- **First test:** Run an ablation study and retain only agents that add measurable value over a simpler baseline.

## 5. Cross-track research programmes

These workstreams should be reused where relevant, but each track still needs its own scope, threat model, evaluation and evidence record.

### A. Agent execution, tools and MCP

Research:
- Identity and principal resolution: who requested the action, on whose behalf, and under which tenant/context?
- Capability contracts: tool name, exact operation, permitted resources, effect, reversibility, rate, and data exposure.
- Authorization: least privilege, scope binding, audience validation, expiry, revocation, delegation and policy version.
- Trust boundaries: user input, retrieved documents, tool output, external agents and model-generated plans are not trusted instructions.
- Action safety: explicit confirmation for consequential side effects; replay protection; idempotency; external outcome reconciliation.
- Runtime isolation: tool sandbox, network restrictions, secrets handling and resource limits.
- Reliability: duplicate delivery, timeout, partial completion, cancellation, compensation, retry and kill-switch behavior.

Required evidence:
- Threat model and asset/actor inventory.
- Tool registry and permission matrix.
- Positive and negative authorization tests.
- Prompt-injection and malicious tool-output scenarios.
- Token expiry/revocation and tenant-isolation tests.
- Tool execution traces and external action verification.
- Failure injection and recovery/rollback demonstration.
- Secrets and sensitive data excluded from default telemetry.

Research anchors: OWASP's 2026 Agentic Applications guidance and 2026 LLM Top 10; MCP's 2026-07-28 specification and authorization security guidance; OWASP API Security Top 10. The July 2026 MCP release changed protocol and authorization details, so MCP tracks must pin the actual spec/SDK version and test against it rather than copy examples from older releases.

### B. AI risk and assurance

Use NIST AI RMF's Govern, Map, Measure and Manage functions as a risk-management structure, not as a mechanical checklist. For each AI-enabled track:
- Govern: identify owners, decision rights, risk tolerance, documentation and ongoing oversight.
- Map: document intended use, users, context, affected parties, third-party models/data/tools and potential impacts.
- Measure: test validity, reliability, robustness, safety, privacy, fairness where relevant, and human-AI interaction.
- Manage: prioritize risks, mitigate, respond to incidents, recover, communicate and monitor after changes.

Required evidence: use-case and prohibited-use statement; impact/threat assessment; test set and baseline; evaluator method; uncertainty/limitations; human oversight; monitoring signals; incident and change process; release decision. A risk-framework mapping does not itself establish compliance or certification.

### C. Secure software and supply chain

Apply NIST SSDF practices across development. For higher-risk build pipelines, review SLSA provenance and artifact verification concepts. Required evidence should include dependency and build provenance, code review, secret scanning, reproducible builds where feasible, vulnerability triage, environment separation, deployment approvals and rollback. Set assurance levels proportionately; do not claim a SLSA level without satisfying its specific requirements.

### D. Observability and audit

Define traces/events around logical actions rather than indiscriminately storing all content. For an agent or workflow action, the evidence record should allow an authorized reviewer to reconstruct:
- principal/tenant (using safe identifiers);
- request and correlation IDs;
- workflow/agent/tool and version;
- policy decision and policy version;
- approval/denial and actor;
- tool call and result status;
- retry/timeout/compensation;
- verified external outcome;
- timestamps and error classification.

Do not record access tokens, secrets or sensitive user content by default. OpenTelemetry's current GenAI semantic conventions are marked as evolving/development material; pin the convention version and review its stability before treating it as a fixed contract.

### E. Multilingual speech, language and cultural meaning

Build a language-data governance file before any collection or model adaptation:
- language, variety, dialect and code-switch pair;
- modality and recording context;
- speaker consent and permitted uses;
- source and license;
- orthography and diacritic handling;
- transcript normalization rules;
- annotation task and handbook;
- reviewer qualifications;
- train/dev/test split policy (speaker separation where applicable);
- retention/deletion and withdrawal process;
- known demographic and domain gaps.

Evaluate ASR using WER/CER but report slices by language, speaker variety, switch boundary, noise, device and domain. For PAL, also assess meaning preservation, pragmatics, discourse context, uncertainty, disagreement and safe action proposal. WER is not a measure of cultural understanding.

Candidate research inputs found in the literature include ÌròyìnSpeech for Yorùbá speech, Mozilla Common Voice language releases and MasakhaNER-X for African-language named-entity work. Their scope differs: a Yorùbá ASR corpus is not automatically a Pidgin/code-switch corpus; an NER dataset is not a speech dataset; neither automatically measures pragmatic meaning. Inspect each release's exact license, consent, version and coverage before use.

### F. Memory, retrieval and grounded answers

Evaluate retrieval and generation separately. At minimum:
- retrieval precision/recall at a chosen k;
- source freshness and provenance;
- answer correctness and relevance;
- faithfulness to retrieved material;
- citation support and citation coverage;
- conflict handling and abstention;
- stale, deleted, poisoned and malicious memories;
- cross-tenant isolation;
- correction, revocation and deletion propagation.

Do not treat a high similarity score as proof that a memory is true or relevant. Do not evaluate a RAG system only by how fluent its answer sounds. Current 2026 RAG review literature emphasizes multidimensional evaluation, including context relevance, faithfulness, answer relevance, correctness and citation quality.

### G. Marketplaces and vertical systems

Research each side of a marketplace separately. Registrations do not prove liquidity. Collect repeat demand, suitable supply, completed transactions, disputes, fraud, cancellations, trust and unit economics. Before a payment, identity, employment, property or regulated workflow is implemented, determine the target geography and obtain a jurisdiction-specific legal/regulatory review.

### H. Creative/publishing/media systems

Research creator workflows and rights separately:
- ownership or license to source media;
- platform API terms and data-use constraints;
- permission to download, transform, store, display or republish;
- user notice and OAuth scopes;
- retention and deletion;
- attribution and third-party asset provenance;
- export fidelity and quality;
- accessibility of final outputs.

An API credential or access to a public URL is not proof of copyright permission. When YouTube API Services are used, evaluate both its API Services Terms and Developer Policies for the actual integration.

### I. Human-subject and behavioral research

For Cognitive Gym, PAL community research, voice/consent studies and related human-participant work, define constructs, hypotheses, recruitment, inclusion/exclusion, consent, privacy, ethics review, instrument validity, confounders, reviewer reliability and replication. Avoid causal claims from convenience samples, one-time surveys or before/after observations without a defensible design. Avoid inferring sensitive personal attributes from behavioral signals.

## 6. Research source library

These are starting points for research. They do not by themselves establish that any track complies, has adopted the standard, or is fit for a particular source/dataset. Check the precise version, date, jurisdiction, terms and applicability before implementation.

1. [NIST AI RMF 1.0](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf) — Govern, Map, Measure and Manage; risk context, measurement, oversight and continual management.
2. [NIST AI RMF Playbook](https://airc.nist.gov/airmf-resources/playbook/) — Voluntary suggested actions mapped to the AI RMF functions; the Playbook itself says it is not a universal checklist.
3. [NIST AI 600-1: Generative AI Profile](https://www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence) — Generative AI-specific risk-management considerations.
4. [NIST SP 800-218: Secure Software Development Framework](https://csrc.nist.gov/pubs/sp/800/218/final) — Secure software development practices to integrate into the SDLC.
5. [OWASP Top 10 for Agentic Applications 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) — Agent-specific risk themes and mitigation starting points.
6. [OWASP GenAI LLM Top 10 2026 source](https://github.com/GenAI-Security-Project/GenAI-LLM-Top10) — Current 2026 LLM risk taxonomy; pin the edition used by each threat model.
7. [MCP 2026-07-28 release notes](https://blog.modelcontextprotocol.io/posts/2026-07-28/) — Current specification release summary, including protocol and authorization changes.
8. [MCP authorization security considerations, 2026-07-28](https://github.com/modelcontextprotocol/modelcontextprotocol/blob/main/docs/specification/2026-07-28/basic/authorization/security-considerations.mdx) — Authorization-specific security considerations for MCP implementations.
9. [OWASP API Security Top 10](https://devguide.owasp.org/en/07-training-education/07-api-top-ten/) — Object/function-level authorization, authentication, resource consumption, SSRF and API inventory risks.
10. [OpenTelemetry GenAI semantic conventions](https://github.com/open-telemetry/semantic-conventions-genai/blob/main/docs/gen-ai/gen-ai-spans.md) — Evolving conventions for GenAI spans; current material cautions against default capture of sensitive prompts/inputs/outputs.
11. [SLSA v1.2](https://slsa.dev/spec/v1.2/) — Software supply-chain provenance and build-integrity specification.
12. [Nigeria Data Protection Commission](https://ndpc.gov.ng/) — Regulator and current NDP Act/GAID resources. The Commission site advertises GAID 2025; review the actual instrument and legal applicability with a qualified privacy professional.
13. [Nigeria Data Protection Act 2023 reference](https://nccc.gov.ng/resources/nigeria-data-protection-act-2023) — Statutory reference; consult the Act and current NDPC guidance directly.
14. [ÌròyìnSpeech: A Multi-purpose Yorùbá Speech Corpus](https://aclanthology.org/2024.lrec-main.812/) — Published Yorùbá ASR/TTS corpus research; inspect exact release, terms and fit.
15. [Mozilla Common Voice: Platform and Dataset](https://www.mozillafoundation.org/en/common-voice/platform-and-dataset/) — Crowdsourced multilingual speech-data process; verify the exact release, language subset and license.
16. [MasakhaNER-X dataset card](https://huggingface.co/datasets/masakhane/masakhaner-x) — Named-entity annotations for 20 African languages including Yorùbá and Nigerian Pidgin; not an audio or pragmatic-reasoning corpus.
17. [2026 survey: Evaluating Retrieval-Augmented Generation](https://link.springer.com/article/10.1007/s42979-026-05134-x) — Review of context relevance, faithfulness, answer relevance, correctness and citation quality.
18. [YouTube API Services Terms of Service](https://developers.google.com/youtube/terms/api-services-terms-of-service) — Terms for applications using YouTube API Services.
19. [YouTube API Developer Policies](https://developers.google.com/youtube/terms/developer-policies) — Requirements for API clients, privacy notice and use of API data.
20. [NAFDAC Product Registration and Regulation](https://nafdac.gov.ng/our-services/product-registrationevaluation/) — Nigerian product-registration process; check the category-specific requirements.
21. [NAFDAC Foods and Related Products Registration Regulations 2025](https://www.nafdac.gov.ng/wp-content/uploads/Files/Resources/Regulations/NAFDAC-Foods-and-Related-Products-Registration-Regulations-2025.pdf) — Relevant only if the actual BatchLedger product/category falls within its scope.
22. [Federal Ministry of Labour and Employment: Occupational Safety and Health](https://labour.gov.ng/professional-operations-departments/occupational-safety-and-health/) — Nigerian OSH mandate and statutory reference points for jurisdiction-specific scaffolding research.
23. [Nigeria Copyright Act 2022 — WIPO Lex](https://www.wipo.int/wipolex/en/legislation/details/21820) — Copyright baseline reference for Nigeria; verify current law and platform terms for each media use.

### Research-source cautions

- ÌròyìnSpeech is a Yorùbá speech corpus reference. Do not assume it covers Nigerian Pidgin, spontaneous speech, every dialect or PAL's pragmatic-action objectives.
- Common Voice is a dataset platform and collection process. Inspect the exact data release, license and contributor conditions before reusing any clips.
- MasakhaNER-X is named-entity recognition data. It is not an ASR dataset or a benchmark for cultural meaning.
- The 2026 ACL workshop thesis proposal on uncertainty-guided code-switched ASR is a research lead, not a completed validated benchmark.
- OpenTelemetry GenAI conventions are evolving. Do not hardwire a draft semantic convention without pinning its version and assessing stability.
- NDPA/GAID, NAFDAC, labor safety, copyright, payments and property rules are jurisdiction- and use-case-specific. This dossier is not legal advice; have the actual workflow reviewed by competent local professionals.

## 7. Stage gates: what must exist before status changes

| Transition | Minimum research/evidence needed |
|---|---|
| Proposed → Research | Defined research question, owner, source register, initial problem hypothesis and feasibility/risk scan |
| Research → Design | Research findings, limitations, validated problem/use case, intended users, outcome definition and decision to proceed |
| Design → In development | Charter, boundaries, user/behavior/operational/data/authorization flows, threat model, contracts, acceptance tests and implementation plan |
| In development → Prototype | Runnable bounded implementation, repository/commit, reproducible setup, core success and denial tests, known limitations |
| Prototype → Verified MVP | Real intended users complete the core job; decision branches tested; security/privacy reviewed; recovery demonstrated; outcome evidence and operator runbook exist |
| Verified MVP → Deployed | Monitored runtime, alerting, incident ownership, rollback/recovery tested, data lifecycle, support owner, deployment record and accepted residual risk |
| Any stage → Paused/Historical | Dated decision, reason, preserved artifacts, discharged user/data obligations and successor mapping if applicable |

A passing build, a polished interface, a case study, a flowchart or an owner report does not independently satisfy the Verified MVP or Deployed gate.

## 8. Evidence record schema for the portfolio registry

Store claims as source-linked records. Do not overwrite old evidence when the status changes; append a new evidence record and retain history.

```ts
type EvidenceLevel =
  | "verified"
  | "reported"
  | "inference"
  | "proposed"
  | "unknown"
  | "historical";

interface EvidenceRecord {
  id: string;
  trackId: string;
  claim: string;
  evidenceLevel: EvidenceLevel;
  sourceType:
    | "repository"
    | "test"
    | "deployment"
    | "owner-report"
    | "interview"
    | "dataset"
    | "publication"
    | "regulator"
    | "vendor-documentation"
    | "other";
  sourceUrl?: string;
  sourcePath?: string;
  sourceVersion?: string;
  commitSha?: string;
  observedAt?: string;
  reviewedAt?: string;
  reviewer?: string;
  limitations?: string[];
  decisionImpact?: string;
}
```

Keep these independent fields on the project record:
- `activityStatus`: ongoing / paused / historical.
- `maturity`: design / in-development / research / prototype / verified-mvp / deployed / unknown.
- `evidenceStatus`: verified / reported / inference / proposed / unknown.
- `namingStatus`: established / working-name / historical-alias.

Do not encode historical activity as maturity. Do not hide working-name projects. Keep Peculiar unknown until its source identity is recovered.

## 9. Prioritized research execution

1. **Registry integrity:** preserve all 66 stable IDs; separate activity, maturity, evidence and naming; reconcile 21 reported, 44 proposed and one unknown; correct historical maturity; add automated count and filter tests.
2. **Reported development tracks:** request exact repository URL, branch, commit, current runnable scope, tests, failing gate and current limitation for LOG_ON OS, AgentBridge-Africa, ArchAudit-CCM, wwhisper, ContextPocket, Re:Mind Me, MorrowVoice, GroundedGuide, CLIPIN, Portfolio Advancement and the source-of-truth repository. Do not infer a repository from a project name.
3. **Reported research/prototype tracks:** recover reproducible research records for Global BI, SafeChain, Cognitive Protocol, PAL and GigPilot. Archive Proverb Activation Library, Omdena RAG, ASE and Prompt Protocol Atlas accurately.
4. **High-risk proposed tracks:** research agent permissions, voice/biometric implications, behavioral data, mental-health adjacency, property verification, marketplace payments/disputes, distillery rules and scaffolding safety before product design.
5. **Remaining proposed tracks:** conduct problem and buyer discovery before producing MVP roadmaps. Preserve proposed names visibly.
6. **Peculiar:** keep Unknown and recover the original source/owner description only; do not invent a domain or product narrative.

## 10. Evidence request template for each project owner/developer

```text
Track ID and display name:
Authoritative repository or source artifact:
Current branch and commit SHA:
What currently runs:
Exact test commands and results:
Decision branches covered (yes and no paths):
Authorization/denial behavior tested:
What is not implemented:
Known defects and currently failing tests:
Data collected, purpose, retention and deletion:
Telemetry and audit evidence available:
Deployment environment and monitoring:
Rollback/recovery demonstrated:
Real user/operator evidence:
Next milestone and acceptance criteria:
Evidence links and date checked:
```

## 11. Final rule

This dossier defines the research and evidence required for all 66 tracks. It does not claim the research is complete, that sources have been integrated, or that any implementation satisfies the requirements. Each track advances only when its own evidence packet exists and has been reviewed.

**No evidence, no promotion. A proposed diagram is a design artifact. A reported track is an owner-described initiative. A verified capability requires reproducible proof from the actual system.**