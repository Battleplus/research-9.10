# Direction-selection status (revised)

Status: **A2 selected as first-paper scope; A1 retained as follow-up; B associated; C reserve. Implementation paused.**
Date: 2026-09-11
Planning baseline commit: `b11acdd`

## Inputs read

- `AGENTS.md`
- `WORKFLOW.md`
- `HANDOFF.md`
- `direction-selection/EVIDENCE.md`
- `direction-selection/OPTIONS.md`
- `direction-selection/DECISION.md`
- `docs/direction-selection-execution-plan.md`
- `docs/continuous-research-roadmap.md`
- `docs/tooling-setup.md`
- Active `research-wiki/`

## Actual tools/calls used

- Local PDF reading: `pdfinfo`, `pdftotext`, and `pdftoppm` plus visual inspection of MAPT page 1.
- Literature retrieval: `.venv/Scripts/python.exe .aris/tools/arxiv_fetch.py` (broad searches and exact IDs), `openalex_fetch.py`, and `semantic_scholar_fetch.py`.
- Web verification: official proceedings, arXiv pages, GitHub repositories, and a current employer careers page.
- Static code inspection: `git rev-parse`, `git status`, and `rg` against MAPT at `0b4ef2712995681febca7631f9a27e1b0dccccbf`.
- Research Wiki: canonical `research_wiki.py` ingest/update/edge/index/query-pack helpers.
- Planning-note hygiene: `.aris/tools/capture_filter.py` returned `ok to capture (mechanical screen clean)` for the new resource checklist.
- Independent review: fresh `gpt-6-astra` with `ultra` reasoning completed as a same-family, fresh-context provisional review (`01a08b60-2ff3-7d12-b540-ab85ee572683`). Three previous route reviewers had failed because of the account usage limit. The review record is [REVERSE-REVIEW.md](REVERSE-REVIEW.md), with raw trace under `.aris/traces/research-review/2026-09-10_run01/`.

## Completed this revision

- Re-read the required workflow and current direction documents.
- Added [NEAREST-NEIGHBORS.md](NEAREST-NEIGHBORS.md) with feedback-object, updated-object, online-interaction, credit/query, MARL-transfer gap, substantive-difference, venue/status, and code-availability columns.
- Re-read the local MAPT PDF and static code boundary; verified the exact current commit.
- Added A1/A2 comparison with failure phenomena, hypotheses, world-model necessity, MARL-specific difficulty, minimal method, strongest neighbors, alternatives, and falsifiers.
- Corrected the Hindsight PRIORs code status from “available” to “paper-listed URL returned 404; unverified.”
- Added the distinction between task-behavior preference and dynamics-rationality preference, especially for RENEW.
- Removed exact route scores and unsupported “B has higher academic ceiling” language.
- Added [MENTOR-ONE-PAGER.md](MENTOR-ONE-PAGER.md) for discussion with senior peers.
- Synced the new A1/A2 ideas and nearest papers into Research Wiki while preserving prior source pages and unresolved questions.
- Incorporated the fresh review's A1 identifiability objection and A2 joint-interaction-information gate.
- Added [MENTOR-DISCUSSION-RESOURCE-CHECKLIST.md](MENTOR-DISCUSSION-RESOURCE-CHECKLIST.md) with a falsifiable A2 hypothesis, uncertainty-type separation, minimal non-executed validation design, resource table, five confirmation questions, and continue/pause/unknown criteria.
- Refined A1 into separate “true individual contribution” and “policy-useful reward decomposition” claims.

## Deliberately not done

- No package installation, training dependency setup, checkpoint loading, environment launch, pilot, ablation, GPU/4060/H200 run, remote execution, or human-label collection.
- No external repository was cloned or executed; code availability was checked only through public pages and the local MAPT checkout.
- Earlier planning rounds performed no Git commit or push. On 2026-09-11 the user explicitly authorized publishing these planning materials; publication is recorded in Git history. No unrelated task changes are included.

## Review limitation

The fresh review is **same-family provisional**, not cross-family review. The decision therefore remains provisional and self-reviewed with respect to cross-family scrutiny. The prior three failed reviewer attempts and the completed reviewer id/trace are recorded under `.aris/traces/`.

## Open decision-critical unknowns

- Whether any 2025–2026 cooperative-MARL paper already combines joint-dynamics uncertainty with task-preference query selection.
- Whether the user’s existing world-model/PbRL code and results are reproducible and can be reused.
- Whether actual human task-preference labels are available; script-teacher results alone cannot establish real-human-feedback benefits.
- Which environment, independent metric, and advisor support can satisfy the A− evidence bar.
- Whether the available artifacts support a planning-only A2 gate; no experimental support is claimed.

## Publication and practical assessment — 2026-09-11

Added [SENIOR-PEER-ASSESSMENT.md](SENIOR-PEER-ASSESSMENT.md) and synchronized the decision, resource checklist and README. This is an AI planning assessment, not an actual senior-peer interview or new independent review. It adds active-query-loop verification and separates method comparison from compute-matched evaluation. No new literature validation or experiments were performed during publication preparation.
