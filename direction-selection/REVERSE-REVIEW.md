# A1/A2 reverse review record

Date: 2026-09-10
Review type: fresh same-family review; independent context, not cross-family
Reviewer: `01a08b60-2ff3-7d12-b540-ab85ee572683` (`Wegener`)
Model/reasoning: `gpt-6-astra` / `ultra`
Independence label: `same-family`, `provisional`
Raw trace: `.aris/traces/research-review/2026-09-10_run01/response.md`

## Verdict

- A1 should not be the first paper at the current evidence level.
- A2 is the provisional first-paper choice after narrowing its claim to coordination-aware query selection.
- The review is useful adversarial evidence, not an acceptance or novelty guarantee.

## Strongest objections

### A1

The proposed stack can look like MAPT plus Hindsight PRIORs: temporal/cooperative preference credit from MAPT, a world-model credit module from Hindsight, and agent-level feedback categories from recent MARL work. More importantly, team-level preference alone does not identify unique per-agent credit. In an additive team reward, shifting a time-dependent amount `c_t` from one agent's latent credit to another while preserving the team sum leaves the observed team preference unchanged. A world model does not remove this identifiability problem. State-prediction importance, masking, or token deletion must not be called causal credit without an explicit intervention or reference-credit target.

### A2

A2 can collapse to ordinary active PbRL moved into MARL. A joint-dynamics uncertainty score is not enough: the paper must show that the score captures interaction information that changes coordination decisions, rather than generic model error, reward-model disagreement, or extra pretraining/simulation. If a selector without a world model matches it, or if the gain comes from unmatched compute, the world-model contribution disappears.

## Required narrowing and future gate

Use the following bounded question:

> Under a fixed team task-preference label budget, can short-horizon joint-dynamics prediction select real trajectory pairs that most reduce ambiguity about coordination decisions, beyond preference disagreement, independent-agent scores, policy likelihood, and diversity?

The future design should keep real trajectory comparisons and use the world model only to estimate query value. It should include a fixed candidate pool, identical downstream learners, matched interaction/label/compute budgets, and an accurate-versus-learned-dynamics check. A low-dimensional two-agent delayed-coordination diagnostic should separate additive from genuinely joint outcomes and include unrelated dynamic noise.

## Decision impact

The review strengthens, rather than proves, the current A2-first decision. A1 remains a follow-up once a measurable agent-time credit target or an A2-generated coordination-failure dataset exists. The main unresolved novelty question is whether a named 2025–2026 cooperative-MARL paper already performs joint-dynamics-uncertainty selection for task-behavior preference queries.
