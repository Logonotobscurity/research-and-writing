# PAL-SF-001 — Runbook

## Purpose
Run read-only structural checks on PAL Markdown artifacts. This is a first-pass integrity aid, not a Yoruba-language validation tool.

## Run
```bash
python pal_sf_001_audit.py PAL_v0.2_fixed.md PAL_V03_ARCHITECTURE.md --json pal_sf_001_results.json
```

## Interpret carefully
- Entry counts apply only to the supplied file.
- `SOURCE_NOT_YET_VERIFIED` flags are blockers for provenance-dependent claims.
- Unicode normalization checks do not prove that tone marks, spelling, or meaning are correct.
- Never modify canonical proverb text as an automatic response to a warning.
- Preserve the raw audit output and source-file hashes with each run.