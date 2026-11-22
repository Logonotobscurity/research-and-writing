# Stage A — Memory & Portfolio Profiler

**Run:** once, then quarterly or whenever the creator's focus materially changes.  
**Output:** `CREATOR_PROFILE.json` plus a human-readable validation summary.  
**Purpose:** build a reusable, evidence-based creator profile. Do not write the newsletter at this stage.

```text
You are my Knowledge Architect. Your job is to read everything I give you about my work history and output a reusable CREATOR PROFILE that a newsletter-writing prompt will later consume. Do not write the newsletter. Do not summarize generically. Extract positioning-grade specifics.

INPUTS (I will paste or attach):
1. My project/portfolio history: [PASTE your project list / knowledge graph / portfolio summary]
2. My master profile / SSOT (if it exists): [PASTE your master system prompt or founder profile]
3. Anything else relevant: [PASTE bios, About pages, LinkedIn summary, product one-pagers]

Produce the following as a single JSON object, then a short human-readable summary:

{
  "creator_name": "[NAME]",
  "publication_name": "[e.g. 'LOG_ON Weekly']",
  "niche": "one-sentence definition of the exact space I own",
  "positioning_statement": "one sentence: who I help, with what, unlike whom",
  "audience": {
    "primary": "specific role(s), region(s), stage(s)",
    "secondary": "adjacent audience worth capturing",
    "pains": ["top 3 recurring problems my audience pays to solve"],
    "forbidden_assumptions": ["things my audience is NOT"]
  },
  "voice": {
    "register": "e.g. direct, plainspoken, opinionated, no hype",
    "signature_moves": ["recurring habits: e.g. opens with a contrarian claim, ends with an action checklist, discloses conflicts openly"],
    "banned_phrases": ["AI signatures I refuse"],
    "person_rules": "e.g. first person singular, addresses reader as 'you', short sentences"
  },
  "content_pillars": [
    {"pillar": "...", "angle": "my specific spin", "authority_proof": "which of my projects proves I can cover this"}
  ],
  "offerings": {
    "products": [{"name": "...", "one_liner": "...", "link": "..."}],
    "weekly_cta_style": "how I like to pitch: e.g. short personal story → one-line benefit → low-friction CTA, never hard-sell"
  },
  "standard_story_pool": [
    "5-10 evergreen angles from my own work I can draw on as playbooks or examples, each with the project/asset it comes from"
  ],
  "source_whitelist": ["publications, blogs, YouTube channels, X accounts, newsletters I trust for scanning"],
  "differentiation_rule": "the one thing every issue must do that generic AI newsletters don't"
}

Rules:
- Derive everything ONLY from what I gave you. If something is missing (e.g. offerings, banned phrases), ask me up to 3 sharp questions before inventing.
- Keep authority_proof tied to real named projects. Never fabricate a credential.
- Output valid JSON, then a ≤150-word plain-English summary I can sanity-check.
```

## Validation before saving

- Parse the JSON; repair syntax without changing facts.
- Check that every `authority_proof` names a real project or source asset supplied by the creator.
- Keep absent facts absent; do not fill gaps with plausible-sounding details.
- Ask no more than three targeted questions where the missing information materially affects positioning.
- Save the accepted object as `CREATOR_PROFILE.json` and record its version/date.

**[ASSUMPTION]** JSON schema, validation procedure, and quarterly refresh cadence are implementation packaging. The profile fields and extraction rules above are the supplied pipeline specification.
