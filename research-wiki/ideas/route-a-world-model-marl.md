---
type: idea
node_id: idea:route-a-world-model-marl
title: "Coordination-Aware World-Model Uncertainty for Efficient Preference Querying in Cooperative MARL"
stage: proposed
outcome: pending
added: 2026-09-11T09:58:14Z
based_on: ["paper:christiano2017_deep_reinforcement_learning", "paper:zhu2024_decoding_global_preferences", "paper:verma2024_hindsight_priors_reward", "paper:bhamidipaty2026_renew_towards_learning", "paper:heo2026_policy_likelihoodbased_query", "paper:shi2025_gawm_globalaware_world", "paper:kou2025_offline_multiagent_preferencebased"]
target_gaps: ["gap:G2", "gap:G5"]
tags: ["main", "a2", "preference-rl", "world-model", "marl", "active-query", "resource-gate"]
---

# Coordination-Aware World-Model Uncertainty for Efficient Preference Querying in Cooperative MARL

**stage:** `proposed`  ·  **outcome:** `pending`

A2 first-paper scope: a joint-dynamics model is only a query instrument for task-behavior preferences.

## Thesis
Under fixed candidate-pool, task-preference-label and environment-interaction budgets with matched downstream learners and full compute reporting, calibrated short-horizon joint-dynamics epistemic uncertainty conditioned on policy coverage and coordination impact may select real trajectory pairs that reduce coordination-decision ambiguity beyond reward-model disagreement, diversity, random selection, and simple combinations.

## Key risks
Must separate epistemic knowledge uncertainty, aleatoric environment randomness, and reward-model disagreement; prediction error alone is not query value. If only joint-state input is added to a single-agent selector, innovation is weak. Requires genuine task-behavior labels or bounded proxy claims, independent task metrics, matched cost controls, and a MARL-specific interaction/teammate-shift test.

## Connections
_Edges are recorded in `graph/edges.jsonl`; summarize here for human readers._


## Practical planning update — 2026-09-11

Assess compute-matched practical value separately from the controlled method comparison. Verify the active-query loop rather than assuming MAPT supplies it. Obtain reproducible baseline metadata, interpretable preference trajectories, and concrete coordination-failure cases before progressing. See [practical assessment](../../direction-selection/SENIOR-PEER-ASSESSMENT.md). No experiment or validated claim is added.
