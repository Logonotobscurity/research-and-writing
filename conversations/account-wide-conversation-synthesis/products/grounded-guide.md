# Grounded Guide — Product Dossier

## 1. Product intent

Grounded Guide is a product in the user's portfolio:
- https://github.com/Logonotobscurity/grounded-guide

The user has described the core ambition as building a website-grounded assistant that can answer from a site's actual information and support a useful visitor journey.

The product should not be presented publicly through a description of private reverse-engineering or competitor research. Public positioning should stand on its own product purpose, behaviour, and differentiation.

## 2. User problem

A website visitor often needs a reliable answer about a business, service, policy, product, availability, or process but must navigate multiple pages or contact the business.

A business may want to make its existing website knowledge easier to use while turning appropriate visitor intent into a qualified enquiry.

The product must solve both sides honestly:
- The visitor needs accurate, useful answers.
- The business needs grounded, maintainable knowledge and a responsible route to qualified leads.

## 3. Product promise

A defensible promise is not “an AI that knows everything about the business.” It is an assistant that answers within the limits of the business's available and current source material, identifies uncertainty, and provides an appropriate next step.

Potential product mechanisms:
- Website ingestion and crawl controls.
- Structured knowledge extraction.
- Source references and freshness metadata.
- Grounded answer generation.
- Abstention when evidence is insufficient.
- Visitor clarification.
- Lead qualification.
- Consent-aware contact capture.
- Analytics and knowledge maintenance.

## 4. Differentiation principles

The user wants a product with clear differentiation rather than a superficial imitation of another system.

A meaningful differentiation strategy can focus on:
- Evidence-linked answers.
- Crawl scope and source freshness.
- Clear treatment of contradictory or missing information.
- Refusal to invent company policies or service details.
- Tenant isolation.
- Consent-aware lead capture.
- Maintainable knowledge sources.
- Auditable ingestion and answer traces.
- Useful business analytics tied to visitor needs and lead outcomes.

These are product directions. They must be verified in the code before they are described as implemented features.

## 5. Core workflow

A possible full workflow is:

1. Business creates or configures a workspace.
2. Business authorizes a website and defines crawl boundaries.
3. The system ingests pages and metadata.
4. The ingestion pipeline records source URL, timestamp, content, and status.
5. Knowledge is extracted and indexed.
6. Visitor asks a question.
7. The system retrieves relevant source material.
8. The answer is generated and checked against the retrieved evidence.
9. The assistant cites or identifies supporting material where appropriate.
10. If evidence is missing or ambiguous, it clarifies or abstains.
11. If the visitor wants contact, the system captures only appropriate information with consent.
12. The business receives a qualified lead and relevant context.
13. The business can inspect performance and update stale knowledge.

## 6. Trust and security requirements

- Tenant isolation.
- Crawl allowlists and denial of private/internal URLs.
- SSRF protection.
- Rate and resource limits.
- Content sanitization.
- Prompt-injection defence for ingested pages.
- Untrusted content separation.
- Source provenance.
- Retrieval and answer tracing.
- No cross-tenant knowledge leakage.
- Lead data minimization and access control.
- Retention and deletion.
- Clear handling of stale pages and changed policies.

A retrieved website passage is data, not an instruction to the agent.

## 7. Product behaviour requirements

The assistant should:
- State what source supports the answer.
- Avoid adding policies that are not in the knowledge base.
- Ask a follow-up when visitor intent is unclear.
- Say when a page is missing or outdated.
- Distinguish a business claim from a verified external fact.
- Escalate to a human when the question is consequential or evidence is insufficient.
- Avoid pretending that a lead has been sent if no verified write occurred.

## 8. Evaluation

Potential evaluation sets:
- Answerable factual question.
- Missing answer.
- Contradictory pages.
- Outdated page.
- Prompt injection embedded in page content.
- Cross-tenant retrieval attempt.
- Ambiguous visitor request.
- Sensitive question.
- Lead request with consent.
- Lead request without sufficient details.
- Invalid contact data.
- External write failure.

Metrics:
- Grounded answer rate.
- Unsupported claim rate.
- Correct abstention rate.
- Citation/source accuracy.
- Retrieval recall.
- Freshness.
- Cross-tenant leakage rate.
- Lead qualification completeness.
- Successful handoff rate.
- Visitor task completion.
- Business acceptance of leads.

## 9. Open questions

1. What is the authoritative ingestion and refresh model?
2. Which content types are supported?
3. How are dynamic, authenticated, or JavaScript-heavy pages handled?
4. How are page-level contradictions resolved?
5. How can a business correct a bad extracted fact?
6. What does the product consider a qualified lead?
7. Which messages or visitor data require consent?
8. How is lead delivery verified?
9. Which differentiators are implemented in the current repository?
10. What evidence demonstrates customer value?

## 10. Current working conclusion

Grounded Guide should be positioned as an evidence-grounded website knowledge and visitor-support system. Its credibility depends on source fidelity, freshness, abstention, tenant isolation, and honest lead handoff—not on claiming that an LLM has comprehensive business knowledge.
