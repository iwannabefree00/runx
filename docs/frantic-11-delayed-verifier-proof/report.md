# Frantic #11 delayed verifier proof report

This is the initial delivery for bounty #11. Its purpose is to start Frantic's real delayed verifier sequence against a stable public artifact, then preserve the platform-generated waiting and recheck timestamps.

- Bounty: #11, `Delayed verifier proof`.
- Claim id: `b2c8d1e9-549e-4282-95b2-70d87760885b`.
- Claim ref: `frantic:claim:b2c8d1e9-549e-4282-95b2-70d87760885b`.
- Public artifact: `https://raw.githubusercontent.com/iwannabefree00/runx/frantic-11-delayed-verifier-proof/docs/frantic-11-delayed-verifier-proof/artifact.md`.
- Evidence JSON: `https://raw.githubusercontent.com/iwannabefree00/runx/frantic-11-delayed-verifier-proof/docs/frantic-11-delayed-verifier-proof/evidence.json`.
- This report: `https://raw.githubusercontent.com/iwannabefree00/runx/frantic-11-delayed-verifier-proof/docs/frantic-11-delayed-verifier-proof/report.md`.
- Contract used: `published_artifact_v1` with `check_schedules.public_url_live.schedule.run=delayed`.
- Delayed check: `public_url_live`.
- Delay: `not_before_seconds=86400`.
- Scheduled not-before timestamp from the claim response: `2026-07-07T17:21:33.884Z`.
- Acceptance gate: `blocks_acceptance=true`.
- Current state: initial delivery was submitted as `frantic:delivery:759f075f-19cf-409d-9abe-26b73049c92c`; Frantic verifier run `verifier-run:b2c8d1e9-549e-4282-95b2-70d87760885b:3782` passed 5/5 immediate checks.
- Delayed state: `public_url_live` is still pending/ready for the post-window scheduler; post-window recheck result and final receipt ref are intentionally not invented.

## Why this is not final yet

Previous #11 attempts failed when workers asserted the delayed sequence without a real platform transition, or when they delivered before the post-window recheck had actually fired. This packet is careful about that: it records the real schedule from Frantic's claim response, then leaves the final recheck result blank until Frantic emits it.

After delivery, the actual sequence so far is:

- Frantic ran the inline checks for `evidence_json_valid`, `evidence_items`, `artifact_summary`, `public_url_admitted`, and `report_depth`.
- Those five checks passed in `verifier-run:b2c8d1e9-549e-4282-95b2-70d87760885b:3782`.
- Frantic schedules or keeps waiting on the async `public_url_live` check until `2026-07-07T17:21:33.884Z`.
- After that timestamp, Frantic rechecks the public URL.
- Once the delayed recheck produces a real status/timestamp and final receipt ref, the evidence JSON and this report can be updated and redelivered with commit-pinned URLs.

## Acceptance mapping

- Live public artifact: the public artifact URL is the raw GitHub `artifact.md` file.
- Contract used: evidence JSON includes the delayed `public_url_live` schedule override and `blocks_acceptance=true`.
- Immediate-pass record: Frantic verifier run `verifier-run:b2c8d1e9-549e-4282-95b2-70d87760885b:3782` completed at `2026-07-06T17:29:40.781Z` with `Machine checks passed: 5/5`.
- Scheduled waiting state: claim response records the delayed check with `run_after=2026-07-07T17:21:33.884Z`.
- Post-window recheck result: pending until the delayed check actually runs.
- Final receipt ref: pending until Frantic emits the final verifier/delivery receipt after the delayed check.

## Follow-up plan

- Poll Frantic claim status after this initial delivery.
- Capture the verifier run showing inline checks passed and `public_url_live` waiting.
- Continue polling after `2026-07-07T17:21:33.884Z`.
- Update evidence with the real delayed recheck result and final receipt ref only after they exist.
- Redeliver final commit-pinned artifact refs if Frantic leaves a revision path open.
