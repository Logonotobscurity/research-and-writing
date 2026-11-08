# 10 — Append-Only Archival Maintenance Protocol

## Principle
Preserve original sequence and append dated corrections, recovered sources, and new outputs. Do not rewrite earlier phases to reflect knowledge acquired later.

## Message capture
1. Copy the user's exact input, including punctuation, URLs, attachments, and formatting.
2. Copy every substantive user-visible assistant response in full.
3. Record order and timestamps/timezone only where available.
4. Separate assistant output, tool output, user-pasted material, and external excerpts.
5. Preserve generated lines, tables, code, prompts, recommendations, and explanations.
6. Label an excerpt if the complete message is unavailable.
7. Never invent a missing turn or timestamp.

## Tool and automation capture
Record the requested operation, destination, actual operation, raw result, status, IDs, timestamps, links, errors, retries, and partial outcomes. Separate local preparation from remote writes. Require destination acknowledgement before reporting delivery. A design is not an executed automation.

## Prompt versioning
Store each full prompt version as a separate immutable file. Include version ID, exact text, date/time, intended behaviour, changes, communicated rationale, linked result, and deployment status.

## Source provenance
For each URL record exact URL/DOI, title, author/organisation, publication date, access date, source class, provenance, claim supported, and whether it was original-session material or added later. Never substitute a newly found page and imply it was used originally.

## Asset capture
For every image/document/spreadsheet/code/package preserve original filename, exact bytes where permitted, date, MIME type, size/dimensions, generating prompt/message if available, and actual public or private reference. A Library file ID is not a public URL. Respect privacy/publication constraints.

## Gap reporting
Use recovered verbatim, recovered original file, partial excerpt, reported from summary, known to have existed but unavailable, existence unknown, not produced in recorded run, restricted from public mirroring, and not verified. Add dated updates without deleting earlier gap records.

## Rationale policy
Preserve reasons the assistant actually communicated. Retrospective explanations must be labelled and limited to observable actions. Do not publish hidden private chain-of-thought.

## Repository integrity
Use dated append-only phases, immutable prompt snapshots, exact source copies separate from summaries, updated indexes, verified links, and normal Git commits. Do not force-push or rewrite history.

## Best next recovery input
A full ChatGPT data export (JSON/HTML) containing conversation IDs, message IDs, and timestamps is the most valuable missing source. Until available, the account-wide transcript remains partial.
