# 09 — Technical Research and Learning Notebook

## 1. Notebook context

The user shared a Gemini Notebook collection titled **“Build Your Own X: Mastering Technology From Scratch”**, described as containing 50 sources. It brought together material on LLMs, retrieval, agents, software architecture, data systems, automation, security, analytics, and developer learning.

A related request was to establish a durable research-notebook process that preserves sources, synthesis, disagreement, and changes in understanding. The stated aim is to maintain a research record that can inform actual systems and decisions.

This is a synthesis of notebook context. It does not independently verify each source or every notebook-generated claim.

## 2. Main technical domains

- **LLMs and model behaviour:** transformers, deep learning, NLP, local inference, quantisation, structured outputs, and evaluation.
- **RAG and knowledge systems:** RAG patterns, local-first and self-hosted RAG, enterprise retrieval, hybrid search, reranking, vector database benchmarks, source attribution, and context construction.
- **Agent systems:** browser-use agents, multi-agent evaluation, tool calling, MCP, agent memory, loop engineering, and agentic evaluation.
- **Data and analytics:** data science, marketing data, streaming analytics, e-commerce analytics, dbt, headless BI, and Reverse ETL.
- **Software and infrastructure:** GraphQL, APIs, developer tools, n8n, cloud infrastructure, OSINT, and build-from-scratch resources.
- **Security and governance:** OWASP LLM application security, document-level ACLs, local-first data handling, secure tool execution, and untrusted context.

## 3. RAG versus fine-tuning

A recurring distinction:
- **RAG** is suitable when a system needs dynamic, updateable, attributable, or permission-controlled knowledge.
- **Fine-tuning** can influence task patterns, response behaviour, style, formatting, or capabilities that benefit from parameter adaptation.

They are not mutually exclusive. Fine-tuning does not automatically solve knowledge freshness or access control; RAG does not automatically solve reasoning quality or tool-use reliability. Selection depends on the failure mode, data, evaluation, latency, cost, and update requirements.

## 4. Vector database decision framework

Discussed criteria include:
1. Scale and integration.
2. Recall and p99 latency under realistic queries.
3. Index options such as HNSW and IVFFlat where relevant.
4. Dense, sparse, and hybrid retrieval.
5. Fusion and reranking.
6. Multi-vector or late-interaction options where useful.
7. Security pre-filtering, row-level security, tenant isolation, and document ACLs.
8. Write churn versus read-heavy workload.
9. Managed, self-hosted, or embedded deployment.
10. Operational complexity and cost.

The workload should decide. A benchmark is meaningful only when dataset, queries, filters, hardware, concurrency, index parameters, and measurement methods are comparable.

## 5. Memory and retrieval architecture

The notebook connected to Re:Mind Me and ContextPocket. A useful conceptual separation is working memory, episodic memory, semantic memory, task/reminder state, and provenance.

Retrieval should consider relevance, time, permissions, source quality, and current purpose. Similarity alone is not authority.

Redis TTL working state and PostgreSQL/pgvector or Qdrant long-term storage appeared as architectural options. They are candidate designs, not a final decision.

## 6. Tool recommendation retrieval engine

A proposed engine for a catalogue of 547 tools was discussed. Candidate components included GLiNER for entity/capability extraction, dense embeddings such as BGE-M3, sparse retrieval such as BM25 or SPLADE, Reciprocal Rank Fusion, cross-encoder reranking, and structured outputs using XGrammar.

These components require version, licence, quality, latency, and integration evaluation before adoption. The engine must not invent tools or fabricate canonical URLs.

## 7. Enterprise retrieval security

The user repeatedly considered access control as part of retrieval, not merely a UI filter after content has entered model context. Candidate controls include document-level ACLs, identity binding, server-side pre-filtering, RLS where appropriate, tenant isolation, permission-aware metadata, retrieval audit, revocation, and cross-role leakage tests.

The correct implementation depends on the threat model and data architecture. Specific claims from notebook sources require primary-source validation.

## 8. DeepLearning.AI roadmap from the notebook

The notebook-generated roadmap proposed study around:
- Evaluating and Improving Agentic Applications.
- Context Engineering.
- Long-Term Agentic Memory with LangGraph.
- Loop Engineering with LangChain Deep Agents.
- MCP and rich-context AI applications.
- Adaptive AI agents.
- On-device memory with Qdrant.
- Claude Code and spec-driven development.
- Transformer LLM fundamentals and NLP.

It also proposed an eight-week plan at approximately four to six hours per week: evaluation; context and memory; loop engineering and MCP; then on-device memory and adaptive agents.

Course names, provider partnerships, durations, prices, and availability are unverified in this archive. Notebook claims of advanced proficiency in orchestration, hybrid RAG, governance, and data engineering should be treated as inferred from prior work and interests, not independent skills validation.

## 9. Research-notebook method

For each source, record canonical title, author, date, URL/DOI, source type, relevant claim, method, limitations, and the notebook's interpretation. Separate source statements from interpretation. Note contradictions. Identify what would validate the claim. Connect findings to a project decision. Record whether a proposal was adopted, rejected, deferred, or left open.

For architectural choices, maintain a decision record with context, alternatives, evaluation criteria, result, and re-evaluation trigger.

## 10. Claims needing extra caution

The notebook synthesis included claims about automated bidding and anti-bot systems, enterprise RAG leakage, protocol auditing, GPT agreement figures, grammar-constrained generation, and identity-labeling or reactance effects. Do not repeat these as verified conclusions until the exact primary source is checked.

The research rule is: **source first, claim second, implementation decision third.**
