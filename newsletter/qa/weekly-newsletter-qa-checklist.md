# LOG_ON Weekly Newsletter — Stage C QA Checklist

Run the full checklist after drafting and before saving the final draft artifact. Record PASS, FAIL, or NOT APPLICABLE for every item. Any FAIL on a required item blocks QA approval.

## 1. Input completeness and provenance

- [ ] Root `CREATOR_PROFILE.json` exists, parses, is complete, and is owner-approved.
- [ ] All seven required `daily_log_YYYY-MM-DD.md` files exist for the exact completed Monday–Sunday week.
- [ ] All seven files are readable and their internal dates match their filenames.
- [ ] No missing date was inferred, substituted, or satisfied with an unrelated archive file.
- [ ] The exact canonical ten-section Composer structure and version/source are available.
- [ ] The selected themes are approved in the production creator profile.

## 2. Structure and editorial fidelity

- [ ] The draft contains exactly ten Composer sections.
- [ ] Section names, order, and required structure match the canonical Composer specification exactly.
- [ ] No extra, omitted, renamed, reordered, or reconstructed section is present.
- [ ] The draft follows the approved LOG_ON voice and audience in the creator profile.
- [ ] The issue has a clear editorial through-line without forcing unrelated findings together.

## 3. Factual accuracy and source integrity

- [ ] Every external factual claim is traceable to a recorded source.
- [ ] Sources are accurately attributed; links, dates, publisher/author, and names are checked.
- [ ] Publication date and event date are not confused.
- [ ] Current claims are supported by appropriately recent evidence.
- [ ] Direct quotations are exact, limited, and attributed.
- [ ] No unsupported claim, invented event, fabricated source, or false attribution appears.
- [ ] Reported claims, verified facts, inference, and opinion are visibly distinguished.
- [ ] Disagreements, uncertainty, and material caveats are preserved.
- [ ] Metrics include units, baselines, time periods, definitions, and sources where applicable.
- [ ] No unexplained metric or unsupported performance claim remains.

## 4. Synthesis and usefulness

- [ ] Findings are synthesized rather than copied as disconnected summaries.
- [ ] Each major item explains its relevance to the approved LOG_ON themes.
- [ ] Repetition, stale items, weak evidence, and unrelated material have been removed or qualified.
- [ ] Recommendations are clearly labelled as recommendations, not reported facts.
- [ ] No conclusion exceeds the evidence.

## 5. Safety, rights, and privacy

- [ ] No private, confidential, personal, or sensitive information is disclosed without a clear basis.
- [ ] Source-media, image, quotation, and third-party content rights are respected.
- [ ] No secrets, credentials, private links, or internal-only material are exposed.
- [ ] No defamatory, misleading, or decontextualized statement is introduced.

## 6. Presentation and final artifact

- [ ] Headline, summary, transitions, spelling, grammar, and formatting are checked.
- [ ] Links resolve to the intended sources.
- [ ] The reporting week and all relevant dates are correct for `Africa/Lagos`.
- [ ] The file uses `LOG_ON_Weekly_YYYY-MM-DD_DRAFT.md` with the correct Sunday date.
- [ ] Known limitations and editorial caveats are stated.
- [ ] The draft is marked **DRAFT — NOT PUBLISHED**.

## 7. External-action boundary

- [ ] No publish, email, forward, schedule, submit, or distribution action was attempted.
- [ ] No external communication was sent as part of QA.
- [ ] The final status reports draft creation and QA outcome separately.

**Release rule:** Any failed required check blocks the draft from being labelled QA-passed. Even when all checks pass, this workflow produces a draft only; distribution is outside its authority.
