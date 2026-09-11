# Direction-selection evidence (revised)

Date: 2026-09-11
Planning baseline commit: `b11acdd` (`docs: persist research workflow invocation playbook`)
Scope: source verification, paper reading, static code inspection, novelty triage, and planning only. No training, checkpoint loading, GPU use, remote execution, or paper writing was performed.

## Evidence and status conventions

Published conference/journal status, arXiv status, code availability, and local static observations are kept separate. The A− target is a submission-quality bar, not an acceptance prediction. “Human feedback” is used only when the source actually documents human labels; script teachers and LLM evaluators are marked separately.

## Actual calls and limitations

| Call | Actual use | Limitation |
|---|---|---|
| `research-lit` procedure | Local PDF scan, web/arXiv/OpenAlex/Semantic Scholar retrieval, synthesis | No Zotero/Obsidian connector was configured or requested. |
| PDF tooling | `pdfinfo`, `pdftotext`, and one visual render of MAPT page 1 | Font warnings from Poppler/pypdf were non-fatal; extracted text and page layout were readable. |
| `.venv/Scripts/python.exe .aris/tools/arxiv_fetch.py` | Broad A/B searches and exact-ID checks for RENEW, MAGPIE, PbCRL, PreSa | Broad keyword searches were noisy; exact-ID queries were used for status/abstract facts. No PDFs were downloaded. |
| `.venv/Scripts/python.exe .aris/tools/openalex_fetch.py` | One 2023– search for world-model/PbRL/MARL | Returned mostly generic or unrelated works; not used as sole evidence for nearest-neighbor claims. |
| `.venv/Scripts/python.exe .aris/tools/semantic_scholar_fetch.py` | One 2023– search | Returned useful but noisy records, including Kim et al., AMADPO, and GAWM; each was cross-checked against an official/arXiv source where possible. |
| Web search/open | Official proceedings, arXiv pages, GitHub repositories, and a current employer careers page | Dynamic web pages can change; dates and status are recorded as observed on 2026-09-10. |
| MAPT static inspection | `git rev-parse`, `git status`, `rg` at fixed commit `0b4ef2712995681febca7631f9a27e1b0dccccbf` | No install, import, checkpoint deserialization, environment launch, or training. |
| Independent review | One fresh-context `gpt-6-astra`/ultra reviewer completed an A1/A2 adversarial review; prior three route reviewers had failed from quota exhaustion | It is same-family and provisional, not cross-family. The raw response and normalized record are in `.aris/traces/research-review/2026-09-10_run01/` and `direction-selection/REVERSE-REVIEW.md`. |

## The essential distinction: two kinds of preference

1. **Task-behavior preference**: a person or evaluator prefers one agent/team behavior over another because it better satisfies the intended task, cooperation, or user goal. MAPT and standard PbRL target this signal.
2. **Dynamics-rationality preference**: a person prefers one imagined rollout or transition model because it looks physically/causally plausible. RENEW uses preferences to supervise world-model dynamics and repair model exploitation.

These are not interchangeable labels. A task-preference query should not be counted as a dynamics-label query, and a world model’s likelihood or uncertainty should not be presented as human approval of the task behavior.

## Four required local sources

| Source | Version/status | What the source establishes | Relevance and caution |
|---|---|---|---|
| Christiano et al., *Deep Reinforcement Learning from Human Preferences* | arXiv:1706.03741v4 (2023 copy); original NeurIPS 2017 | Humans compare trajectory segments; reward predictor and policy are updated in an online feedback loop; online feedback helps with distribution shift and reward hacking. | Foundational task-behavior preference pipeline, not a world model or MARL method. |
| Zhu et al., *Decoding Global Preferences: Temporal and Cooperative Dependency Modeling in Multi-Agent Preference-Based RL* (MAPT) | AAAI 2024, pp. 17202–17210; local PDF and official code | A cascaded Transformer models temporal and cooperative dependencies to produce differentiated multi-agent preference rewards. The paper’s method is reward modeling, followed by MARL policy optimization. | The paper uses “human preference” terminology, but the official README states that script teachers generate preference data. Treat that data as a controlled proxy unless human labels are independently confirmed. |
| Kaufmann et al., *A Survey of Reinforcement Learning from Human Feedback* | arXiv:2312.14925v3, 28 Dec 2025 | Feedback arity/granularity, active collection, reward-model evaluation, distribution shift, and policy evaluation are separate design choices. | Methodological background; not direct evidence that a particular A1/A2 method works. |
| Zhong et al., *A Comprehensive Survey of Reward Models* | arXiv:2504.12328v1, 12 Apr 2025 | Human/AI preference sources, active collection, reward-model bias/robustness, and evaluation challenges. | LLM-centered survey; useful for terminology and failure modes, not a direct MARL result. |

## Nearest-neighbor synthesis

The requested full comparison is in [NEAREST-NEIGHBORS.md](NEAREST-NEIGHBORS.md). The important revision is that A1 has closer MARL credit-assignment neighbors than previously recorded, while A2 has closer active-query neighbors. Neither is abandoned: the remaining difference is a setting-plus-mechanism intersection that is still unverified, not a proven first claim.

### A1 evidence

- Hindsight PRIORs already uses a forward-dynamics world model for single-agent preference credit assignment.
- MAPT already performs temporal/cooperative attention-based credit allocation in cooperative MARL.
- Kim et al. (arXiv:2503.03796) already proposes agent-level feedback categories for MARL credit assignment, using an LLM evaluator rather than a verified human-label protocol.
- GAWM (arXiv:2501.10116) already studies a global-aware world model for MARL, but without preference feedback.

The defensible A1 gap would therefore need to be **identifiable, intervention-backed agent-time credit for task-behavior preferences in cooperative MARL**, not merely “attention plus a world model.” Team-level preference alone cannot uniquely identify per-agent credit; an explicit intervention or reference-credit target is required. That gap remains a hypothesis requiring a last-mile literature check and a measurable credit target.

### A2 evidence

- Christiano et al. established uncertainty-oriented online preference querying, but not world-model uncertainty in MARL.
- PoLiCER (ICLR 2026) directly addresses stale/off-policy query selection using current-policy likelihood and critic-triggered reset, but is single-agent and has no world model.
- RENEW uses epistemic uncertainty to query preferences, but the queried object is imagined-rollout dynamics plausibility and the setting is single-agent/offline world-model repair.
- MAPT supplies a multi-agent preference reward/policy pipeline but does not supply active query selection or model uncertainty.

The defensible A2 gap is therefore narrower and cleaner: **under a fixed task-preference label budget, can short-horizon joint-dynamics prediction select real trajectory pairs that most reduce ambiguity about coordination decisions, beyond policy likelihood, reward-model disagreement, independent-agent scores, and diversity?** The world model must add joint interaction information, not just generic uncertainty. This is not yet a validated novelty claim.

## MAPT static-code boundary

At fixed commit `0b4ef2712995681febca7631f9a27e1b0dccccbf`:

- `README.md:43,45` says script teachers generate preference data and points to a downloadable preference-data share; `README.md:60,78,87-90` documents a pre-trained preference reward model used in policy learning.
- `mat/scripts/train_reward/train_reward_model.py:27-52,78-101,145-171` loads a pickled preference dataset and trains the preference/reward model offline. No transition/world-model learner appears in this path.
- `mat/algorithms/reward_model/utils/dataloader.py:6-63` uses `pickle.load`, a sequential 80/20 split, and derives `max_len` from `traj0`; the following shorter-than-`max_len` branch cannot detect a shorter `traj0`. This is a reproducibility risk, not proof of total non-runnability.
- `mat/algorithms/reward_model/models/MultiPrefTransformer.py:67-116` trains a Bradley–Terry-like pairwise preference predictor and has no explicit constraint or preference-state adaptation.
- `mat/utils/pref_reward_assistant.py:64-151,153-215` loads a serialized reward model and maintains a rolling trajectory history; it has no imagined rollout or uncertainty-driven query code.
- `mat/runner/shared/smac_runner.py:23-84,139-150` steps the environment online, calls the preference assistant, and trains the policy with its output. Thus MAPT is offline preference-model training plus online policy interaction, not offline RL end-to-end.
- `mat/scripts/train_smac_3m_policy.sh:11-14` contains 10M environment steps, 32 rollout threads, hard-coded paths, duplicate `save_interval`, and a typo-prone `-log_interval`. These imply future porting/reproducibility work; none was executed.

## Source and code status

- MAPT: official repository exists; local fixed commit was inspected statically. No local environment run.
- REED/Dynamics Aware Rewards: official [apple/ml-reed](https://github.com/apple/ml-reed) is accessible and accompanies CoRL 2023; no code was run.
- Hindsight PRIORs: the ICLR 2024 paper is published, but the paper-listed [GitHub URL](https://github.com/apple/ml-rlhf-hindsight-prior) returned 404 on 2026-09-10. Code availability is therefore **not verified**.
- RENEW: [official repository](https://github.com/FlyingWorkshop/RENEW) is accessible; README identifies it as RLC 2026 Finding the Frame Workshop. It is not treated as a main-conference result.
- PoLiCER: [official repository](https://github.com/JongKook-Heo/PoLiCER) is accessible and identifies itself as ICLR 2026 official code; installation requires an old MuJoCo/PyTorch-style stack, not installed here.
- Kim et al. USV-swarm paper: arXiv record is available; no official code repository was verified in this pass. Secondary indexes suggest IROS 2025, but this was not treated as primary venue proof.
- AMADPO: the official AAMAS 2025 proceedings PDF is accessible; no official code repository was verified in this pass.

## Current evidence judgment

A2 is the better first-paper scope because it isolates one failure phenomenon—uninformative or stale task-preference queries under joint-policy shift—and has a clean comparison against PoLiCER and RENEW without claiming either is a direct duplicate. A1 is retained as the follow-up because its closest neighbors already cover single-agent world-model credit and MARL attention/agent-level credit; a first paper would need stronger causal-credit evidence than is currently available.

The fresh review supports A2 first and A1 follow-up, but only provisionally and within the same model family; it is not cross-family validation. If a named published or accepted paper already contains the A2 result in cooperative MARL, or if a world-model-free selector matches it under matched compute and candidate pools, the decision must be revisited. Otherwise proximity alone is not a reason to abandon it. See [REVERSE-REVIEW.md](REVERSE-REVIEW.md).

## Resource-planning update

No new literature search was performed in this update. The planning artifact [MENTOR-DISCUSSION-RESOURCE-CHECKLIST.md](MENTOR-DISCUSSION-RESOURCE-CHECKLIST.md) separates model knowledge uncertainty, environment randomness, and reward-model disagreement; specifies fixed candidate-pool and cost-accounting requirements; records the boundary of script/LLM proxy labels; and lists the exact materials still needed from the group. These are prerequisites for a future test, not experimental evidence.
