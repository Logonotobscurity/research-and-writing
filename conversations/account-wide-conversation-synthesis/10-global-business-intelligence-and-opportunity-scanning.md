# 10 — Global Business Intelligence and Opportunity Scanning

## 1. Purpose

The user has explored a Global Business Intelligence Agent and an opportunity-scanning workflow to convert global and African market signals into evidence-backed decisions.

The ambition is global intelligence with a strong Africa priority lens, not a system that ignores the rest of the world or restricts its research to Africa.

## 2. Intended role of the intelligence agent

The agent is intended to:
- Discover relevant market and technology signals.
- Identify official requirements and changes.
- Verify claims against primary sources.
- Connect signals to market needs and implementation opportunities.
- Identify relationships, contact routes, and possible next actions.
- Rank opportunities transparently.
- Present decisions for human review.
- Record whether proposed actions were actually completed.

It should not manufacture certainty, contacts, eligibility, or market demand.

## 3. Geographic and market priority

The recorded Africa focus includes:
- Nigeria.
- Kenya.
- Ghana.
- Rwanda.
- Uganda.
- Tanzania.
- South Africa.
- Egypt.
- Morocco.
- Ethiopia.
- East African Community.
- AfCFTA-related activity.
- PAPSS and cross-border payment infrastructure.

A six-market MVP was proposed around Nigeria, Kenya, Ghana, Rwanda, Uganda, and Tanzania. This is a prioritization decision, not a claim that the other markets are irrelevant.

## 4. Signal taxonomy

Potential signals include:
- Funding, grants, debt, and prizes.
- Market entry and country launches.
- Partnerships and distribution agreements.
- Acquisitions and investments.
- Regulation, licences, and compliance changes.
- Payment infrastructure and cross-border rails.
- Cloud, data-centre, and connectivity infrastructure.
- Procurement, RFPs, and tenders.
- Hiring and skills demand.
- Accelerators and founder programmes.
- Localization and language support.
- Competitor moves and product launches.
- Government programmes and public-sector initiatives.
- Research publications and technical capability changes.

Every signal should be connected to a dated source and a clear explanation of why it matters.

## 5. Evidence hierarchy

The recorded source discipline is:

- **Tier 1:** official regulator, government, standards body, company filing, company announcement, procurement portal, or first-party documentation.
- **Tier 2:** reputable reporting or analysis that provides evidence and attribution.
- **Tier 3:** social posts, newsletters, community commentary, and discovery-only leads.

A Tier 3 item may initiate research but should not become a material fact without further verification.

For time-sensitive opportunities, record both:
- Publication or announcement date.
- Actual event date, deadline, or effective date.

A newly published article can describe an old event; those dates must not be conflated.

## 6. Signal-to-action chain

**Observation → verified claim → market requirement → implementation opportunity → relationship/contact route → human review → action → outcome.**

### Observation
A source indicates a potentially relevant event.

### Verified claim
The key details are confirmed, ideally from a primary source.

### Market requirement
The researcher explains what the event changes for a customer, country, industry, or technology.

### Implementation opportunity
The signal is translated into a possible product, service, partnership, or market-entry action.

### Relationship and contact route
A genuine route to the relevant organization or person is found. Contacts must not be invented.

### Human review
A person checks the source, relevance, eligibility, risks, and proposed action.

### Action
A permitted outreach, application, or research task is carried out.

### Outcome
The system records confirmation, rejection, no response, further information, or an unresolved state.

## 7. Opportunity scoring

Prior work uses a fit score from 0 to 100, with a strong priority threshold around 90+. These are internal prioritization heuristics, not external facts.

A useful scoring model should expose its components rather than output a naked number:

- Geographic fit.
- User capability fit.
- Strategic alignment.
- Eligibility.
- Deadline urgency.
- Expected value.
- Probability of success.
- Effort and cost.
- Evidence quality.
- Reversibility.
- Relationship or distribution advantage.

Eligibility should be a gating condition, not merely a weak score component. A high strategic fit does not make an ineligible opportunity actionable.

## 8. Opportunity scanner preferences

The user's recorded preferences include:
- Africa-first coverage.
- Funding, grants, accelerators, fellowships, cyber, agent safety, open source, and SME programmes.
- Fresh items, ideally within the last 24–48 hours where that time window is relevant.
- Clear fit score and actionable next step.
- Strong priority for opportunities scoring 90+.
- Evidence and links.
- Focus on closing actions rather than generating endless lists.

The date window should be selected based on the query. A grant deadline that is still open may be relevant even if the announcement is older than 48 hours.

## 9. Pilot concept

A seven-day pilot was proposed with goals of approximately:
- 5–10 verified signals per day.
- Top three signals enriched with a market implication and possible action.
- Precision and usefulness measured, not merely volume.

This is a proposed pilot target, not a proven operating result.

Potential evaluation:
- Source validity.
- Date correctness.
- Duplicate rate.
- Eligibility correctness.
- Geographic relevance.
- Signal precision.
- Opportunity ranking quality.
- Time to decision.
- Human acceptance rate.
- Action completion.
- Useful outcomes per researcher-hour.

## 10. Global Business Intelligence Agent and safe execution

The user discussed building this intelligence workflow in an agent environment, including OpenServ as a planned platform.

The same authority rule applies:

**Can do ≠ may do.**

Before consequential external actions, identify:
- Principal identity.
- Authority.
- Target.
- Scope.
- Data to be shared.
- Side effects.
- Reversibility.
- Approval requirements.
- Verification method.

Human approval should be required for consequential, irreversible, legal, financial, security, or reputational actions unless an explicit policy authorizes a narrower autonomous action.

The previous notes reported that an OpenServ connector was not available in the relevant environment at that time. The current integration status should be rechecked before planning a tool-specific implementation.

## 11. Research leads and source bundle

The user previously supplied or discussed sources spanning:
- AssemblyAI and voice systems.
- Sakana AI / Namazu.
- NIST and OWASP.
- MCP and platform documentation.
- Supabase and OpenRouter.
- Sahara and N-ATLaS.
- African AI and local technology organizations.
- Research papers, datasets, and regional ecosystem initiatives.

The existence of a supplied URL is not evidence that its contents were reviewed or that its claims are accurate. The original source bundle should be retrieved from the research notebook if exact URLs or status are required.

## 12. Open questions

1. Which opportunity categories produce a real decision or action rather than information overload?
2. What are the authoritative sources for each country and signal type?
3. How should stale but still open opportunities be ranked?
4. How are eligibility rules represented and tested?
5. How does the system identify actual contact routes?
6. What is the minimum useful evidence bundle before human review?
7. Which activities can be automated safely?
8. How are outcomes tracked over months rather than only at discovery time?

## 13. Current working conclusion

The opportunity scanner should be a verified intelligence-to-decision system, not a feed of attractive links. Its quality should be measured by the accuracy of its evidence and the usefulness of decisions and actions it enables.
