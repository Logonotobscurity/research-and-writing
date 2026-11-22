# LOG_ON Weekly Newsletter Pipeline

## Purpose

This directory is the operational home for weekly LOG_ON editorial inputs, Stage C draft generation, and quality assurance. The parent repository remains the durable research and writing archive; this directory does not replace the historical conversation records.

## Required inputs

Before Stage C starts, all of the following must be readable from the repository's current target revision:

1. Root-level `CREATOR_PROFILE.json` — completed and owner-approved. `CREATOR_PROFILE.template.json` is a starter only and does not satisfy this requirement.
2. Exactly seven daily logs in `newsletter/daily_logs/`, named `daily_log_YYYY-MM-DD.md`, one for each day Monday through Sunday of the completed week.
3. The canonical ten-section LOG_ON Composer structure, with the exact section names and order. Its source must be supplied or located and verified; do not reconstruct or guess the sections.

Use the completed week in the `Africa/Lagos` timezone. Derive its Monday and Sunday dates explicitly. Do not silently shift the week, scan a wider period, or substitute older logs.

## Stage C gate

- Check the profile, the seven exact filenames, and readability of every file.
- If any input is missing, inaccessible, incomplete, or unapproved, report **BLOCKED**, list the exact missing or invalid inputs, and stop.
- Do not infer daily events from repository activity, unrelated notes, email, or historical archive files.
- When all inputs pass, compose a draft only, using the exact ten-section Composer structure.
- Preserve sourced facts, source dates, uncertainty, attribution, and caveats. Every external factual claim must be traceable to a source in the logs or a clearly attributed source referenced by a log.
- Run every item in `qa/weekly-newsletter-qa-checklist.md` before marking the draft QA-passed.
- Save the artifact as `newsletter/drafts/LOG_ON_Weekly_YYYY-MM-DD_DRAFT.md`, where the date is the Sunday ending the completed week.

## External-action boundary

Stage C is draft-only. Never publish, email, forward, schedule, submit, or distribute a newsletter. Do not make external communications or account changes as part of this pipeline. A successful local/repository draft is not permission to distribute it.

## Daily-log convention

See [daily_logs/README.md](daily_logs/README.md) and [daily_logs/daily_log_TEMPLATE.md](daily_logs/daily_log_TEMPLATE.md). A template file is not a dated log and never counts toward the seven-file gate.

## Composer structure source gap

The repository does not yet contain a verified copy of the exact ten-section LOG_ON Composer structure. See [COMPOSER_STRUCTURE_REQUIRED.md](COMPOSER_STRUCTURE_REQUIRED.md). Stage C remains blocked until the canonical structure is supplied and recorded without editorial reconstruction.
