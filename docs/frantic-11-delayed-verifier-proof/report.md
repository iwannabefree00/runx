# Frantic #11 delayed verifier proof report

This is the current delivery packet for bounty #11, claim `cf4934f1-d4a7-4b9d-a630-0e02db333b8d`.

The important constraint is awkward but real: the claim fuse is two hours, while Frantic's own delayed `public_url_live` machine floor is scheduled 24 hours after claim time. I am therefore delivering before the fuse only to start the real verifier sequence. This report intentionally does not claim the delayed recheck has already passed.

- Bounty: #11, `Delayed verifier proof`.
- Claim id: `cf4934f1-d4a7-4b9d-a630-0e02db333b8d`.
- Claim ref: `frantic:claim:cf4934f1-d4a7-4b9d-a630-0e02db333b8d`.
- Claim receipt code: `r/dc9ce97c`.
- Public artifact: `https://raw.githubusercontent.com/iwannabefree00/runx/frantic-11-delayed-verifier-proof/docs/frantic-11-delayed-verifier-proof/artifact.md`.
- Evidence JSON: `https://raw.githubusercontent.com/iwannabefree00/runx/frantic-11-delayed-verifier-proof/docs/frantic-11-delayed-verifier-proof/evidence.json`.
- This report: `https://raw.githubusercontent.com/iwannabefree00/runx/frantic-11-delayed-verifier-proof/docs/frantic-11-delayed-verifier-proof/report.md`.
- Contract used: `published_artifact_v1` with `check_schedules.public_url_live.schedule.run=delayed`.
- Delayed check: `public_url_live`.
- Delay: `not_before_seconds=86400`.
- Scheduled not-before timestamp from the claim response: `2026-07-08T05:16:19.711Z`.
- Acceptance gate: `blocks_acceptance=true`.

## Why this delivery is intentionally not final yet

- The previous #11 claim, `b2c8d1e9-549e-4282-95b2-70d87760885b`, passed the immediate inline checks but was rejected because the delayed `public_url_live` machine floor was still pending.
- I am carrying that lesson forward: the current evidence marks the post-window recheck result as `not_yet_available`.
- No timestamp in this packet is computed at page load.
- No delayed check result is hand-authored.
- No final delayed-check receipt is invented.
- The public artifact is a stable raw GitHub file that should remain HTTP 200 before and after the delayed window.

## Current Frantic verifier schedule

Captured from the current claim response:

- `evidence_json_valid`: inline, waiting for delivery, blocks acceptance.
- `evidence_items`: inline, waiting for delivery, blocks acceptance.
- `artifact_summary`: inline, waiting for delivery, blocks acceptance.
- `public_url_admitted`: inline, waiting for delivery, blocks acceptance.
- `report_depth`: inline, waiting for delivery, blocks acceptance.
- `public_url_live`: async delayed check, `run_after=2026-07-08T05:16:19.711Z`, blocks acceptance.

## Acceptance mapping

- Live public artifact: the `public_url` artifact is a raw GitHub file.
- Contract used: evidence JSON includes `check_schedules.public_url_live.schedule.run=delayed`.
- Blocks acceptance: evidence JSON includes `check_schedules.public_url_live.blocks_acceptance=true`.
- Immediate-pass record: expected to be produced by Frantic after this delivery; it will be appended from real agent status only.
- Scheduled waiting state: evidence JSON records the current claim schedule and not-before timestamp.
- Post-window recheck result: pending until after `2026-07-08T05:16:19.711Z`.
- Final receipt ref: pending until Frantic emits the actual delivery/check result.

## Review note

Please do not treat this packet as asserting final success before the delayed machine floor completes. The previous failure mode was premature review while `public_url_live` was still pending; this packet is intentionally explicit about that so the real delayed recheck can complete.

## Follow-up plan

- Deliver this branch URL before the two-hour claim fuse.
- Capture the real Frantic delivery receipt.
- Update this same branch evidence/report with the delivery receipt.
- Poll Frantic until inline checks pass and `public_url_live` waits for its delayed run.
- Continue polling after `2026-07-08T05:16:19.711Z`.
- Append the real post-window recheck result and final receipt only after Frantic emits them.
