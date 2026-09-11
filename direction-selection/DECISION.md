# Direction decision (revised)

Decision date: 2026-09-10
Planning baseline commit: `b11acdd`
Mode: direction planning only; no training, experiment, GPU, remote execution, checkpoint loading, or paper writing.

## Recommendation

### First paper: A2 — world-model-assisted multi-agent preference feedback querying

Working title:

> **Coordination-Aware World-Model Uncertainty for Efficient Preference Querying in Cooperative Multi-Agent Reinforcement Learning**

The first paper should ask one bounded question:

> At matched environment-interaction and task-preference-label budgets, can joint-dynamics uncertainty, corrected for current-policy coverage and coordination impact, select more informative cooperative-MARL behavior queries than policy-likelihood, reward-model disagreement, or diversity heuristics?

The world model is a query instrument, not a second source of task labels. The label remains a task-behavior preference. Dynamics-rationality preferences such as those used in RENEW must be reported as a separate supervision type if used at all.

The first-paper gate is narrow: keep a fixed real-trajectory candidate pool, vary only the query selector, and test whether short-horizon joint-dynamics prediction adds coordination-interaction information beyond policy likelihood, reward-model disagreement, independent-agent scores, and diversity. No agent-time credit redistribution, MPC, or imagined policy training belongs in the first version.

### A1 — follow-up, not discarded

Working title:

> **World-Model-Assisted Spatiotemporal Credit Assignment for Preference-Based Cooperative Multi-Agent Reinforcement Learning**

A1 remains the most natural continuation after A2, but its first-paper overlap is currently less comfortable: Hindsight PRIORs already uses a world model for single-agent preference credit; MAPT already performs temporal/cooperative credit; Kim et al. already introduces agent-level MARL feedback categories. A1 should follow once a credible cooperative agent-time credit diagnostic or A2-generated coordination-failure dataset exists.

The reverse review adds a stricter condition: team-level preference cannot by itself identify unique per-agent credit. A1 therefore needs an explicit intervention or reference-credit target before using “causal credit” as a claim.

## Why A2 wins the first-paper comparison

- **Continuity:** it reuses preference labels, MAPT’s trajectory representation, rolling buffers, and online policy interface, while adding a world-model component aligned with the stated background.
- **Innovation space:** PoLiCER covers policy-likelihood query alignment in single-agent PbRL; RENEW covers uncertainty-guided queries for dynamics-rationality feedback. The proposed intersection—joint-dynamics uncertainty for task-behavior queries in cooperative MARL—remains to be verified, but is a clear sentence a reviewer can test.
- **Implementation burden:** query scoring is the intended primary method change, but the active-query loop must first be checked and may require substantial additional engineering and avoids adding policy planning, reward redistribution, and a separate credit ground truth in the first paper.
- **Verification burden:** it still needs fixed-candidate-pool, held-out, coordination-sensitive evaluation, calibration, and an accurate-versus-learned-dynamics check. These are hard but more direct than proving causal agent-time credit.
- **Uncertainty separation:** it must distinguish model knowledge uncertainty, environment randomness, and reward-model disagreement; prediction error alone is not query value.
- **Resource dependence:** the H200 is useful for ensemble/world-model sweeps, but the direction must have a small 4060-compatible diagnostic path. A large world model is not required by the problem statement.
- **Employment migration:** it accumulates world-model dynamics, uncertainty estimation, active data selection, MARL, evaluation, and preference/RLHF skills. This aligns with current roles spanning world models, robotics, agents, and RL, but is not an employment guarantee; see [ByteDance Seed careers](https://seed.bytedance.com/zh/career).

## What would change the decision

Move A2 back to provisional/blocked if a named published or accepted cooperative-MARL paper already contains joint-dynamics-uncertainty task-preference query selection with the same failure target and evaluation. Move A1 ahead only if a source or advisor supplies a validated agent-time credit target and shows the query problem is not the dominant bottleneck. Do not switch to B merely because A’s search remains incomplete.

## B associated extension

B remains:

> **Separating Task Preference from Independent Safety Constraints in Preference-Based Cooperative Multi-Agent Reinforcement Learning**

It is a later extension, not a fallback. Before starting B, confirm an independent observable safety cost/constraint channel, a benchmark with hard violation metrics, and an advisor who can support safe-RL evaluation. Adding a penalty to the preference reward does not satisfy this requirement.

## Continuity and new prerequisites

The intended sequence is:

`existing PbRL/world-model experience → A2 query selection → A1 credit follow-up → B independent constraints`.

### Reusable assets

- **Code/interface:** trajectory-segment and pairwise-preference data interfaces, MAPT-style temporal/joint-agent encodings, preference-model training/evaluation scaffolding, replay/rolling buffers, and the online policy loop can be reused after reproducibility is verified.
- **Data/representation:** joint trajectories, agent masks/IDs, action-observation histories, pairwise task-behavior labels, and a shared held-out query protocol can carry from A2 to A1. A2’s coordination-failure slices can become A1’s diagnostic cases.
- **Evaluation protocol:** fixed label and environment-interaction budgets, policy-shift splits, held-out task-preference agreement, independent task metrics, coordination-success/violation counts, calibration, and cross-map/team generalization should be kept consistent across A2 and A1.

### Conditions that must be added

- **Before A2:** a reproducible joint transition/world-model implementation; a fixed candidate-pool data interface; calibrated uncertainty; genuine task-behavior feedback or an explicitly bounded proxy; and an independent task metric. The A2 selector must be separable from downstream learner changes.
- **Before A1:** distinguish true individual-credit recovery from policy-useful reward decomposition. The former needs identifiability assumptions or intervention/reference evidence; the latter needs policy and decomposition diagnostics, not necessarily true credit labels.
- **Before B:** an independently observable safety cost, constraint indicator, or safety budget with hard violation metrics and safe-RL baselines. A scalar penalty folded into the learned preference reward is not an independent constraint channel.

This sequence preserves continuity without assuming that “world model” experience automatically transfers: the missing data protocol, labels, calibration, and evaluation evidence must be established at each transition.

## C reserve

C remains a reserve only for a genuine stream of changing or agent-specific preferences under partial observability, with adaptation delay/regret metrics. Dynamic preference inference, dynamic MORL, and agent-specific preference work already occupy the broad formulation.

## Submission fit and evidence gap

Potential communities for A2 are PbRL/RLHF, MARL, active learning, robotics, and model-based RL. A method-centric paper may be considered by ICLR/NeurIPS/ICML-level review; an explicitly MARL/agent-systems paper may fit AAMAS; a robotics emphasis may fit CoRL/robotics venues. These are potential fits, not promises or a conversion between venue and school classification. The school’s A−/A mapping and current submission rules must be checked separately.

The current gap to an A−-level submission is not a missing buzzword. It is evidence that:

- the problem exists under cooperative policy shift;
- the query score selects task-relevant uncertainty rather than merely dynamics error;
- method gains hold at matched candidate data, labels, interaction and downstream learner settings with full compute reporting; practical value is then assessed separately under comparable total compute budgets;
- held-out behavior and independent task metrics improve;
- the method generalizes beyond one map and has calibrated failure cases.

No novelty validation or acceptance claim is made at this stage.

## Review status

A fresh-context `gpt-6-astra`/`ultra` review supports A2 first and A1 follow-up, with `same-family / provisional` status. It is not cross-family validation. The strongest objections and required kill conditions are recorded in [REVERSE-REVIEW.md](REVERSE-REVIEW.md); the raw trace is under `.aris/traces/research-review/2026-09-10_run01/`.

## Five questions for senior peers

1. Can the group provide genuine human task-behavior preference labels, or only script/LLM proxy labels?
2. Which cooperative MARL environment has both observable joint transitions and an independent task metric suitable for held-out evaluation?
3. Is the existing world-model implementation real, reproducible, and reusable, or only conceptual experience that must be re-established?
4. Does the advisor consider query efficiency or agent-time credit the more consequential bottleneck for the intended application?
5. Which target venue and school classification list should govern the A−/A submission bar and deadline?

## Practical assessment update — 2026-09-11

A2 remains a conditional first-paper candidate. See [senior-peer perspective](SENIOR-PEER-ASSESSMENT.md): verify the active-query loop, prioritize a reproducible team environment, obtain concrete failure cases, and separate method-effectiveness from compute-matched cost-benefit evaluation. A1 is a possible continuation rather than a promised second paper.
