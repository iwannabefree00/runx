# Frantic #11 delayed verifier proof report

This is the current delivery packet for bounty #11, claim `cf4934f1-d4a7-4b9d-a630-0e02db333b8d`.

The important constraint was awkward but real: the claim fuse was two hours, while Frantic's own delayed `public_url_live` machine floor was scheduled 24 hours after claim time. The first delivery started that sequence before the fuse. This revision is now written after Frantic's delayed check fired and passed.

- Bounty: #11, `Delayed verifier proof`.
- Claim id: `cf4934f1-d4a7-4b9d-a630-0e02db333b8d`.
- Claim ref: `frantic:claim:cf4934f1-d4a7-4b9d-a630-0e02db333b8d`.
- Claim receipt code: `r/dc9ce97c`.
- Source delivery ref: `frantic:delivery:35e2fa45-3d4a-4c03-833c-9cbd95407e78`.
- Revision delivery ref: `frantic:delivery:6a217dc1-3d2e-4861-9ac7-bc9c8cc1d0fc`.
- Public artifact: `https://raw.githubusercontent.com/iwannabefree00/runx/frantic-11-delayed-verifier-proof/docs/frantic-11-delayed-verifier-proof/artifact.md`.
- Evidence JSON: `https://raw.githubusercontent.com/iwannabefree00/runx/frantic-11-delayed-verifier-proof/docs/frantic-11-delayed-verifier-proof/evidence.json`.
- This report: `https://raw.githubusercontent.com/iwannabefree00/runx/frantic-11-delayed-verifier-proof/docs/frantic-11-delayed-verifier-proof/report.md`.
- Contract used: `published_artifact_v1` with `check_schedules.public_url_live.schedule.run=delayed`.
- Delayed check: `public_url_live`.
- Delay: `not_before_seconds=86400`.
- Scheduled not-before timestamp from the claim response: `2026-07-08T05:16:19.711Z`.
- Acceptance gate: `blocks_acceptance=true`.
- Current revision reason addressed: the earlier evidence had placeholders for the immediate-pass record and post-window recheck result.
- Delayed verifier run ref: `verifier-run:cf4934f1-d4a7-4b9d-a630-0e02db333b8d:3855`.
- Delayed verifier completed: `2026-07-08T05:17:17.361Z`.
- Delayed `public_url_live` result: `passed`, `HTTP 200`, updated at `2026-07-08T05:17:16.313Z`.

## Why this revision is now final

- The previous #11 claim, `b2c8d1e9-549e-4282-95b2-70d87760885b`, passed the immediate inline checks but was rejected because the delayed `public_url_live` machine floor was still pending.
- The current claim, `cf4934f1-d4a7-4b9d-a630-0e02db333b8d`, reached the scheduled window and Frantic ran the delayed check.
- The current evidence no longer contains placeholder statuses for the immediate-pass record or post-window recheck result.
- No timestamp in this packet is computed at page load.
- The delayed check result is copied from Frantic status: `public_url_live`, `passed`, `HTTP 200`, updated at `2026-07-08T05:17:16.313Z`.
- The final refs are copied from Frantic: revision delivery receipt `frantic:delivery:6a217dc1-3d2e-4861-9ac7-bc9c8cc1d0fc` and verifier run `verifier-run:cf4934f1-d4a7-4b9d-a630-0e02db333b8d:3855`.
- The public artifact is a stable raw GitHub file that should remain HTTP 200 before and after the delayed window.

## Current Frantic verifier schedule

Captured from the current claim response:

- `evidence_json_valid`: inline, waiting for delivery, blocks acceptance.
- `evidence_items`: inline, waiting for delivery, blocks acceptance.
- `artifact_summary`: inline, waiting for delivery, blocks acceptance.
- `public_url_admitted`: inline, waiting for delivery, blocks acceptance.
- `report_depth`: inline, waiting for delivery, blocks acceptance.
- `public_url_live`: async delayed check, `run_after=2026-07-08T05:16:19.711Z`, blocks acceptance; passed at `2026-07-08T05:17:16.313Z`.

## Real Frantic verifier outputs copied into evidence

- `evidence_json_valid`: passed at `2026-07-07T05:22:30.946Z`; summary `JSON parses successfully.`
- `evidence_items`: passed at `2026-07-07T05:22:30.946Z`; summary `JSON array 'observations' has 8 item(s).`
- `artifact_summary`: passed at `2026-07-07T05:22:30.946Z`; summary `JSON string 'summary' has 240 character(s).`
- `public_url_admitted`: passed at `2026-07-07T05:22:30.946Z`; summary `URL admitted as public surface: raw.githubusercontent.com`.
- `report_depth`: passed at `2026-07-07T05:22:30.946Z`; summary `Markdown has 37 bullet items.`
- `public_url_live`: passed at `2026-07-08T05:17:16.313Z`; summary/evidence `HTTP 200`; data `bytes=943`, `status=200`, `final_url=https://raw.githubusercontent.com/iwannabefree00/runx/frantic-11-delayed-verifier-proof/docs/frantic-11-delayed-verifier-proof/artifact.md`.
- Latest delayed verifier run: `verifier-run:cf4934f1-d4a7-4b9d-a630-0e02db333b8d:3855`, status `needs_review`, summary `Machine checks passed: 1/1. Review pending with human or llm.`, started `2026-07-08T05:17:16.994Z`, completed `2026-07-08T05:17:17.361Z`.

## Acceptance mapping

- Live public artifact: the `public_url` artifact is a raw GitHub file.
- Contract used: evidence JSON includes `check_schedules.public_url_live.schedule.run=delayed`.
- Blocks acceptance: evidence JSON includes `check_schedules.public_url_live.blocks_acceptance=true`.
- Immediate-pass record: populated in evidence JSON from Frantic status with check IDs, statuses, summaries, and timestamps.
- Scheduled waiting state: evidence JSON records the current claim schedule and not-before timestamp.
- Post-window recheck result: populated in evidence JSON from Frantic status after the window.
- Source delivery receipt ref: `frantic:delivery:35e2fa45-3d4a-4c03-833c-9cbd95407e78`.
- Revision delivery receipt ref: `frantic:delivery:6a217dc1-3d2e-4861-9ac7-bc9c8cc1d0fc`.
- Final delayed-check result: `public_url_live` passed with HTTP 200 at `2026-07-08T05:17:16.313Z`.
- Final verifier ref: `verifier-run:cf4934f1-d4a7-4b9d-a630-0e02db333b8d:3855`.

## Review note

Please treat this as the post-window revision packet. The earlier packet intentionally waited for Frantic's machine floor. Frantic has now run the delayed `public_url_live` recheck, and the real result is copied into the evidence JSON and summarized above.

## Follow-up plan

- Delivered this branch URL before the two-hour claim fuse.
- Captured the original Frantic delivery receipt: `frantic:delivery:35e2fa45-3d4a-4c03-833c-9cbd95407e78`.
- Captured the revision Frantic delivery receipt: `frantic:delivery:6a217dc1-3d2e-4861-9ac7-bc9c8cc1d0fc`.
- Captured the real Frantic inline pass records from status.
- Waited until after `2026-07-08T05:16:19.711Z`.
- Captured the real delayed `public_url_live` pass from status.
- Updated this same branch evidence/report with the post-window verifier result and final refs.
