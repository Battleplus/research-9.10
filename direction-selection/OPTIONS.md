# A-route scope decision (revised)

This document compares only two A-route first-paper scopes. B remains a later associated extension; C remains a reserve. No numerical score is used because the evidence does not justify precision.

## A1 — world-model-assisted multi-agent spatiotemporal credit assignment

### Failure phenomenon to explain

MAPT’s group-level preference label is coarse, while the behavioral cause may be one agent’s action at one time interacting with teammates and changing the future joint state. Attention-based importance can be correlational or diffuse. Hindsight PRIORs shows that forward dynamics can help single-agent credit, but does not establish the cooperative case.

### Core hypothesis

**For task-behavior preference labels in cooperative MARL, an explicitly intervention-backed centralized action-conditioned world model can provide a more identifiable agent-time credit signal than preference-attention weights alone, improving held-out preference-to-policy alignment at matched feedback.**

This wording covers two different A1 claims. “Recovering true individual contribution” requires an identifiability assumption or intervention/reference evidence. “Finding a reward decomposition that helps policy learning” does not necessarily require true credit labels, but it still requires held-out task-preference alignment, policy-shift tests, independent task metrics, and counterfactual or decomposition-stability diagnostics. These claims must not be reported as equivalent.

### Why a world model is necessary

The proposed role is not to judge whether a rollout looks physically plausible. It estimates how an agent-time action changes the next joint state or future coordination-relevant prediction, which is information not contained in a static preference label or attention map. This is only a candidate causal proxy until an intervention or reference-credit target validates it.

### Why MARL is uniquely difficult

The outcome depends on joint actions; agents are partially observed; teammate policies make the effective transition non-stationary; and credit is not identifiable from a single team-level label. A local perturbation can help one agent while hurting the team or another agent.

### Minimal method change

Keep MAPT’s task-preference objective and policy interface. Add a centralized action-conditioned transition model and use a conservative agent-time transition-effect/importance signal as an auxiliary credit allocator for the preference reward. Do not use dynamics-plausibility labels in the first version. Start with a fixed offline dataset or controlled proxy labels for diagnosis; do not claim human alignment unless human labels are collected.

### Strongest neighbor and simple alternatives

Strongest neighbor: Hindsight PRIORs for world-model credit, with MAPT and Kim et al. as the MARL credit neighbors. Simple alternatives: MAPT attention only, difference-reward/counterfactual baseline, uniform temporal credit, or a learned reward-model ensemble without dynamics.

### Falsifier

The hypothesis is weakened or rejected if the transition-effect signal does not improve held-out task-preference agreement or an explicitly defined intervention/reference-credit diagnostic; if gains vanish after parameter/compute matching; if attention/difference reward is as good; or if the only improvement is training return on the same teacher distribution. Team-level preference alone is not a sufficient ground truth for unique per-agent credit.

### Assessment

A1 is highly continuous with both named areas, but the first-paper delta is currently thinner because prior work separately covers world-model credit and MARL preference credit. It is better as a follow-up after A2 produces a query/shift diagnostic or after a real agent-time credit target is established.

## A2 — world-model-assisted multi-agent preference feedback querying

### Failure phenomenon to explain

In online PbRL, the policy distribution changes. Queries drawn from stale or low-likelihood behavior can be uninformative; in MARL, a team clip can look globally decisive while the uncertainty lies in a coordination transition or a subset of agents. PoLiCER addresses current-policy alignment in single-agent PbRL; RENEW addresses uncertainty-guided queries for dynamics-rationality feedback, not task-behavior feedback.

### Core hypothesis

**For task-behavior preferences in cooperative MARL, short-horizon joint-dynamics prediction conditioned on current-policy coverage and coordination impact selects real trajectory pairs that reduce coordination-decision ambiguity more label-efficiently than policy likelihood, reward-model disagreement, independent-agent scores, or diversity alone.**

The hypothesis is specifically about knowledge uncertainty that exposes missing interaction structure. Environment randomness and reward-model disagreement are separate quantities; large next-state prediction error alone is not evidence that a human task-preference query is valuable.

### Why a world model is necessary

The query should target uncertainty about future joint outcomes under candidate actions, not only uncertainty in the reward predictor or how often a segment occurs. A learned transition model provides object-level predictive uncertainty and interaction information; task preference remains the label. If it adds only generic model error, it is not the proposed contribution.

### Why MARL is uniquely difficult

The query space is combinatorial over joint actions; local observations hide teammates’ state; coordination failures are temporally delayed; and a global label may conceal which agent interaction is decision-relevant. Model uncertainty can also reflect teammate non-stationarity, so calibration matters.

### Minimal method change

Keep MAPT’s task-preference representation and online policy loop. Add a small ensemble or bootstrapped joint transition predictor and define a query score combining (i) current-policy likelihood/coverage, (ii) predictive disagreement over the next joint state or short-horizon coordination outcome, and (iii) diversity. The first paper should use a fixed candidate pool and change only the selector; it should compare accurate versus learned dynamics and match labels, interaction, learner parameters, and selector compute. It should not add model-predictive control or imagined policy training; the world model is only a query instrument.

### Strongest neighbor and simple alternatives

Strongest algorithmic neighbor: PoLiCER. Strongest uncertainty/query neighbor: RENEW. Strong MARL infrastructure neighbors: MAPT and GAWM; AMADPO is an offline preference-policy baseline. Simple alternatives: PoLiCER likelihood-only, a multi-agent PoLiCER adaptation, reward-model ensemble entropy, random/diverse segments, or uncertainty without policy-coverage correction.

### Falsifier

The hypothesis is weakened or rejected if world-model query scores do not reduce labels for a fixed held-out task-preference/policy-alignment target; if gains disappear after matching coverage, candidate pools, and query diversity; if uncertainty predicts dynamics error but not task-preference disagreement or coordination-decision ambiguity; if a world-model-free selector is equally effective; or if gains come from unmatched pretraining, simulation, or compute.

### Assessment and recommendation

A2 is recommended for the first paper. It has one primary mechanism, a measurable fixed-budget question, a direct MARL-specific failure mode, and a clean separation between task-behavior labels and dynamics-rationality signals. The novelty remains provisional: the decisive missing evidence is a final search for any 2025–2026 cooperative-MARL work that already combines joint-dynamics uncertainty with task-preference query selection.

The fresh same-family review agrees with this ordering, while warning that A2 must demonstrate joint interaction information rather than generic uncertainty. This warning is a design gate, not a completed experiment.

## A1 versus A2

| Criterion | A1 credit assignment | A2 feedback querying |
|---|---|---|
| First-paper scope | Wider: transition model, credit target, reward redistribution, and policy effect | Narrower: one query score, one label budget, one downstream alignment target |
| Closest overlap | Hindsight PRIORs + MAPT + Kim et al. | PoLiCER + RENEW, but their feedback object/setting differs |
| Reuse of MAPT | High | High |
| Dependence on ground-truth credit labels | Potentially high; a credible credit diagnostic is needed | Lower; held-out preference and downstream behavior can be primary |
| Risk of semantic confusion | Dynamics importance may be mistaken for task preference | Must keep dynamics uncertainty as selector, not as a label |
| Recommended role | A follow-up after a query/shift diagnostic | **First A paper** |

## B and C remain conditional

B is not a fallback for an unresolved A novelty question. It should start only with an independent, observable safety cost or constraint signal. C should remain reserved for a genuine changing-preference process with adaptation-delay/regret metrics.
