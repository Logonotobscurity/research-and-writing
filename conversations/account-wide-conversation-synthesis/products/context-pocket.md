# ContextPocket — Product Dossier

## 1. Product intent

ContextPocket is a local-first context and memory utility for preserving useful developer and project context. The user's discussions describe it as a Python/SQLite CLI and MCP-oriented project, intended to reduce the repeated work of reconstructing project state across sessions.

The product sits at the intersection of developer memory, project continuity, structured context capture, and tool-accessible retrieval.

## 2. Intended user problem

Developers and technical operators repeatedly lose working context:
- Why a decision was made.
- Which assumptions were accepted.
- What was tested.
- What remains broken.
- Which branch or subsystem is active.
- What should happen next.
- Which details are stale or superseded.

A useful context system should preserve more than raw notes. It should support retrieval, provenance, freshness, relevance, and safe handoff.

## 3. Product boundary

ContextPocket should not be confused with:
- A full enterprise document-management system.
- A canonical team knowledge base by default.
- An unrestricted personal data vault.
- A complete replacement for source control, project issue tracking, or documentation.
- A guarantee that every AI platform conversation can be accessed automatically.

The user's later discussions distinguish local individual memory from shared team memory and from canonical project documents. Those are different products and governance requirements.

## 4. Architecture and implementation direction

The available context describes:
- Python implementation.
- SQLite persistence.
- CLI access.
- MCP interface.
- Local-first storage.
- Structured context records.
- Import/export and search.
- Provenance and confidence metadata.
- Project-aware and branch-aware context.

The product should define how local state is protected, excluded from source control, backed up, exported, imported, and deleted.

## 5. Hardening and validation history

Two historical snapshots appear in the available project notes and should be kept separate.

### Snapshot A — Local hardening record around 28 October 2026

The record reported:
- 36 tests passing.
- Local branch-aware coverage of 82%.
- Compileall success.
- Wheel build success.
- Install smoke tests success.
- File size limit of 25 MiB.
- Export with exclusive creation, private permissions, and fsync.
- Tests for oversized imports, private export permissions, overwrite handling, non-finite confidence, invalid timestamps, and malformed JSON-RPC.

The same snapshot noted:
- Ruff had not been run locally.
- Hosted GitHub Actions and CodeQL were not run.
- Third-party audit and MCP conformance review were not complete.
- User pilot was not complete.
- The package was not approved for production use with sensitive data.

### Snapshot B — Later publication and repository validation record

A later note reported:
- PR #1 merged.
- 27 file SHAs verified exactly against a source-tree snapshot.
- Hosted CI reported a startup failure with no jobs, leaving hosted tests, lint, and build unverified.
- A separate alpha coverage floor of 74% appeared in that snapshot.
- No security certification was obtained.

These snapshots are not directly interchangeable. Coverage values may reflect different code states, test sets, or measurement conditions. The current repository should be inspected before using either figure as a current status.

## 6. Security and data-lifecycle requirements

The design should address:
- Local directory permissions.
- Secret and credential scrubbing.
- Excluding private state from Git.
- Import size and structure validation.
- Export permissions and overwrite protection.
- Backup and restore.
- Data deletion.
- Provenance.
- Confidence validity.
- Timestamp validity.
- Stale and superseded records.
- MCP input/output boundaries.
- Workspace or project separation where needed.

Local-first does not automatically mean secure. Device compromise, backups, filesystem permissions, import files, and MCP clients remain part of the threat model.

## 7. Product risks and unresolved questions

1. What is the canonical record schema?
2. How are source references retained?
3. How does the system detect stale or superseded context?
4. How are conflicting memories represented?
5. How does project or branch context affect retrieval?
6. Which import/export formats are supported and validated?
7. What is the threat model for MCP access?
8. How can users inspect and delete captured context?
9. What makes the product meaningfully different from notes, Git history, and existing knowledge tools?
10. Is the target individual developer, technical team, or both?

## 8. Current working conclusion

ContextPocket has a clear local-first developer-context direction and documented hardening work. It should remain described as an alpha or development-stage project until current CI, security review, MCP conformance, and real developer use are independently established.
