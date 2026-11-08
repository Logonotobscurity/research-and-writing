# 07 — Archive Completeness Correction and Verbatim Preservation

**Record date:** 2026-11-08  
**Record type:** Dated archival correction and maintenance decision  
**Applies to:** This conversation folder and future additions to the research-and-writing repository  
**Historical treatment:** Append-only. Earlier phase files remain unchanged.

## 1. Why this addendum exists

The user reviewed the repository archive and reported that it did not contain the full outputs delivered across the original conversation. The user also asked that all URLs used for secondary sources be included, exact message text be preserved whenever available, and new dated phases be appended instead of rewriting the historical record.

The user's instruction is preserved verbatim:

> I didn't get the full outputs you gave on echach result from conversation in the repository folder doc you shared also all URLs used in incase of secondary sources and preserve exact message text when available and append new dated phases rather than rewriting the historical record.

This is a correction to the archive's completeness status. It does not invalidate the original work; it identifies that the repository captured summaries and selected examples where it should have retained complete deliverables and source-level provenance.

## 2. Audit finding: the previous archive is incomplete

The following gaps were identified by comparing the original requested deliverable (as recorded in Phase 01) with the contents of the committed files.

| Expected historical material | What the repository currently preserves | Audit status |
|---|---|---|
| Original user instruction | A verbatim excerpt in Phase 01 | Partial; preserve the original full message when recoverable |
| Eight generated attention lines | Eight example lines in Phase 03 | Recoverable text, but not the complete response |
| Explanation of the psychological mechanism for every line | No complete per-line explanations in Phase 03 | Missing from the current archive |
| Best contexts for each line (ads, DMs, emails, social, sales, etc.) | General purpose described, but no complete per-line context mapping | Missing from the current archive |
| Flyer prompt or design specification for each line | Only a general description of the eight 9:16 cards | Missing from the current archive |
| Eight generated flyer image files | The archive says images were generated, but contains no verified file links or asset manifest | Asset references unavailable in this archive |
| First, second, and third full versions of the automation prompt | Changes are summarised in Phase 04 and Phase 05 | Full prompt snapshots missing |
| Full seven-line first automation output | Only its structure, mechanism names, and some safeguards are summarised in Phase 05 | Exact output missing |
| Deployment table and safeguards from that automation output | Their existence is noted, but their full contents are not reproduced | Missing from the current archive |
| Every external source URL used in the original research | Several practitioner URLs are listed, but some references remain generic or incomplete | Incomplete; see the source addendum |
| Exact assistant messages and intermediate research results | Not preserved as a transcript | Not available in the current archive |

### Specific correction to the earlier wording

Phase 03 currently says:

> **Status:** Generated output. Full text and rationales were delivered in the conversation.

That sentence describes what happened in the conversation, not what this repository file actually preserves. The repository does **not** contain the full rationales or context mapping. This addendum corrects the archive's status without altering the historical Phase 03 file.

Likewise, Phase 05 describes the first seven-line automation output, but does not preserve the exact seven lines, their full explanations, the full deployment table, or the exact safeguards. The description must not be mistaken for the original output.

## 3. Material that is recoverable from the current archive

The following material is explicitly recoverable from the files currently committed:

1. The original task brief excerpt and the explanation of the NotebookLM compilation context in [Phase 01](./01-original-request-and-notebooklm-context.md).
2. The eight exact hook lines reproduced in [Phase 03](./03-generated-lines-and-flyer-production.md).
3. The user-provided automation-result summary and the categories of mechanisms it contained in [Phase 05](./05-first-automation-output-and-refinement.md).
4. The recorded history of prompt refinements in [Phase 04](./04-automation-prompt-iteration.md) and [Phase 05](./05-first-automation-output-and-refinement.md).
5. The known external URLs already listed in [SOURCE_REGISTRY.md](./SOURCE_REGISTRY.md), now separated from newly checked bibliographic references in [the dated source registry addendum](./SOURCE_REGISTRY-ADDENDUM-2026-11-08.md).

These are the limits of what can be called recoverable from the current repository and available conversation context. An exact quotation must not be reconstructed from a summary.

## 4. Material that cannot currently be restored verbatim

The following original material is not present in the repository or the conversation context available for this correction:

- The full assistant response containing the eight lines, each complete mechanism explanation, and each recommended context.
- The complete image-generation prompt or visual specification attached to every one of the eight cards.
- The original generated image files or verified links to those assets.
- The exact text of automation prompt versions one, two, and three.
- The full seven-line automation result supplied by the user, including every line, rationale, flyer prompt, deployment-table cell, and safeguard.
- The complete list of URLs opened or cited during the original research session.
- Any exact assistant wording or intermediate research output that was not copied into the committed files.

These items are marked **not currently recoverable**, not “never existed.” The original conversation export or the missing messages/assets would be needed to restore them reliably. No new text should be represented as a verbatim historical output merely because it sounds consistent with the earlier summary.

## 5. Preservation rules from this date forward

### 5.1 Exact message text

When source messages are available, archive them without paraphrase in a transcript or message record. Preserve:
- Speaker/role.
- Original message text, including headings, lists, tables, code, and wording.
- Message order and date/time when available.
- Assistant outputs in full, not just descriptions of the outputs.
- User corrections and the assistant's response to those corrections.
- Any distinction between text generated by the assistant and text pasted by the user.

Do not silently correct spelling, grammar, punctuation, or formatting inside a verbatim block. An edited reading copy may be provided separately and labelled as edited.

### 5.2 Separate transcript from synthesis

Use distinct records for:
- **Transcript:** exact messages, where available.
- **Deliverable archive:** complete generated outputs, prompt versions, tables, code, and other artifacts.
- **Phase synthesis:** explanation of what happened, why it changed, and what was concluded.
- **Evidence/source register:** every source locator and its relationship to the claims or outputs.

A synthesis is not a substitute for a transcript. A statement that an output was delivered is not the output itself.

### 5.3 External sources and URLs

Every external source actually opened, used, cited, or materially relied upon must receive an individual registry entry. Do not group multiple pages under “multiple URLs” or replace an exact URL with a domain.

Each entry should include:
- Stable source ID.
- Exact canonical URL (and DOI where applicable).
- Title, author/organisation, and publication date if available.
- Source class: primary research, secondary research, practitioner commentary, official documentation, news, or user-supplied source.
- Whether it was opened and used in the original phase, merely mentioned, or added during a later audit.
- The claim, line, or section it supports.
- Access or verification date.
- Any limitation, disagreement, or reason not to rely on it.

If an original URL cannot be recovered, record **URL not preserved** and explain what is missing. Do not silently substitute a newly found URL and imply it was used in the original conversation. Newly discovered sources belong in a dated addendum.

### 5.4 Generated assets and prompt versions

For every generated visual or other asset, preserve the original prompt, output filename or stable asset link, dimensions/aspect ratio, date, and the message/result it belongs to when these details are available.

For iterative prompts, save each complete version separately (for example, `prompt-v1.md`, `prompt-v2.md`, `prompt-v3.md`). A change log may explain differences, but must not replace the full versions.

### 5.5 Append-only historical record

- Do not edit an old phase to make it look as though later knowledge was present at the time.
- Add a new dated phase for corrections, new evidence, or new outputs.
- Keep earlier claims visible and add a dated correction when they are incomplete or superseded.
- Update an index or table of contents only to point to new records; do not rewrite the historical narrative.
- Identify the provenance and date of every retrospective reconstruction.

## 6. Current archival status

<badge-placeholder />

**Status: PARTIAL / NOT A COMPLETE TRANSCRIPT.**

This folder is a useful phase summary, but it is not yet a complete archive of all conversation outputs. The eight lines and the recorded user brief are recoverable; several substantial assistant and user-pasted deliverables are not. The source registry also remains incomplete for the original research session.

The next reliable recovery step is to use the original conversation export or the original messages and assets, if available, to add a dated transcript-and-deliverables supplement. The recovered material should be copied exactly and assigned source references; any content that remains unavailable must stay marked as unavailable.

## 7. Editorial decision

The user's request establishes the preservation standard for this repository: **full outputs, exact message text whenever available, URL-level source provenance, and append-only dated phases.** Future archives must meet this standard and disclose gaps rather than imply completeness.
