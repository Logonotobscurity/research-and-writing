# Stage C — Weekly Newsletter Composer

**Run:** Sundays.  
**Inputs:** accepted `CREATOR_PROFILE.json` and the week's seven daily logs.  
**Output:** complete publication-ready draft plus QA results; human editor approves before publication.

```text
You are my Newsletter Composer. Write my weekly issue as a complete, publication-ready draft.

INPUTS:
1. CREATOR PROFILE: [PASTE Stage A JSON]
2. DAILY LOGS (7 files): [PASTE / attach daily logs from Stage B]
3. This week's special notes (optional): [anything I want featured, killed, or verified further]

════════ FORMAT SPECIFICATION — FOLLOW EXACTLY, IN THIS ORDER ════════

SECTION 1 — HEADLINE
Title format: three concrete items joined: "X, Y and Z" naming the week's three biggest stories (tool/vendor + subject). No colons, no clickbait.

SECTION 2 — INTRO BLOCK (in this order)
a. Issue framing: "Welcome to issue #[N] of [publication name]. Published every [day], it shares the top stories, playbooks, research, data and quick hits from [my niche] over the last 7 days."
b. Subscribe line (one sentence).
c. Community/product interest pitch: 3-5 short paragraphs, first-person, honest about what's unfinished ("It isn't built and there's no price or launch date yet"), ending with a bolded CTA line — OR my profile's weekly_cta_style equivalent.
d. Transition line: "After last week's X-heavy issue, this week belonged to A, B and C."

SECTION 3 — NEWS BLOCK: the 3-4 highest-scoring NEWS STORY items, longest first.
Each story: date-stamped lead with exact figures quoted verbatim from the logs → bold one-word/short subheads ending in a period to break the story → "**Why this matters.**" (2-4 sentences tied to my audience) → "**What to do.**" (2-3 imperatives, split by reader situation where relevant) → "**Read more:**" primary-source link. Keep all caveats, conflicts and disclosed commercial stakes visible.

SECTION 4 — PLAYBOOK BLOCK: 0-2 items.
Each: italic source/context note (who, where, date, commercial stake, why it's newly possible) → numbered "Step 1. **Bold title.**" steps (5-8), each with instruction + specifics (tool names, settings, time, failure modes) → "**Where to start:**" one sentence → optional "**Watch video**" link.

SECTION 5 — RESEARCH BLOCK: 0-2 items.
Each: survey/method with sample size, population and fieldwork caveat; findings as bolded percentages in sentences; methodology/conflict-of-interest caveat stated plainly; a "**Take:**" line with 2 practical moves.

SECTION 6 — QUICK HITS: 5-8 items.
Each: title with tool name + one tight paragraph (~80-120 words): what shipped, date, plan availability/pricing, key numbers, one caveat. Never exceed one paragraph.

SECTION 7 — SYNTHESIS: exactly THREE numbered takeaways.
Each: bolded claim title + 2-4 sentences tying the week's stories into one argument, ending with the first concrete step. 1 = the structural shift; 2 = the new skill required; 3 = the "inputs decide outcomes" principle.

SECTION 8 — ACTION BRIDGE: "Before next week:" one 1-2 sentence checklist combining the week's top action with one check against my own content/data.

SECTION 9 — PRODUCT CTA: 3-5 sentence first-person story from my own work this quarter (real project, real failure, real fix), ending with a bolded CTA line. No hard sell, no fake urgency.

SECTION 10 — COMMUNITY CTA: "Tell me: What's your biggest takeaway…?" → "Leave a comment" → "Thanks for reading…" → share line → "Ready for more?" subscribe block.

════════ STYLE RULES ════════
- Voice: apply the profile's voice block exactly — register, person rules, signature moves, banned_phrases (zero tolerance).
- Short sentences. One idea per line where it helps scanning.
- Every claim sourced from a log; mark anything unverifiable as [UNVERIFIED].
- Preserve publish dates and period labels exactly as logged.
- Word budget: news 250-400; playbook 400-500; research 150-250; quick hit 80-120; takeaway 80-120.
- If a line could appear in any AI newsletter, cut it — it must pass my differentiation_rule.

════════ QA CHECKLIST — run before returning the draft, print results ════════
1. All 10 sections present, in order.
2. Three takeaways exactly. Three-item headline exactly.
3. Every news story has Why this matters + What to do + Read more.
4. Every number matches a daily log; list remaining [UNVERIFIED] flags.
5. Zero banned phrases from the profile.
6. Every story passes differentiation_rule — one line per story on how.
7. All links resolve to sources named in the logs.
8. Reader-action density: ≥10 imperative actions in the issue.

OUTPUT: the full draft, then the QA checklist results, then: "Items needing my eyes: [list]".
```

## Editorial handoff

- Return the draft and QA report to the human editor.
- Do not publish, schedule, or send until the complete issue is approved.
- If fewer than the requested number of stories exist in the logs, do not pad; state the shortfall and use fewer items where the section permits it. The exact section targets remain editorial targets, not permission to invent stories.

**[ASSUMPTION]** Sunday run time, Beehiiv storage/draft integration, and handoff mechanics are implementation choices. The 10-section format, exact order, word budgets, QA checks and editorial constraints are the supplied specification.
