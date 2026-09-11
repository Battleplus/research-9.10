---
type: idea
node_id: idea:route-a1-credit-marl
title: "World-Model-Assisted Spatiotemporal Credit Assignment for Preference-Based Cooperative MARL"
stage: proposed
outcome: pending
added: 2026-09-11T09:58:15Z
based_on: ["paper:zhu2024_decoding_global_preferences", "paper:verma2024_hindsight_priors_reward", "paper:mu2026_multiagent_reinforcement_learning", "paper:kim2025_human_implicit_preferencebased", "paper:shi2025_gawm_globalaware_world"]
target_gaps: ["gap:G1"]
tags: ["follow-up", "a1", "preference-rl", "world-model", "marl", "credit-assignment", "identifiability"]
---

# World-Model-Assisted Spatiotemporal Credit Assignment for Preference-Based Cooperative MARL

**stage:** `proposed`  ·  **outcome:** `pending`

A1 follow-up: distinguish identifiable true individual contribution from a policy-useful reward decomposition.

## Thesis
Recovering true individual contribution requires an identifiability assumption or intervention/reference-credit evidence; finding a policy-useful reward decomposition may avoid true labels but still requires held-out task-preference, policy-shift, independent-task, and decomposition-stability validation.

## Key risks
High overlap with MAPT, Hindsight PRIORs, and agent-level MARL feedback. Team-level preference alone cannot identify unique individual credit; masking or prediction importance is not automatically causal. A sensible decomposition must be evaluated without overclaiming ground-truth credit.

## Connections
_Edges are recorded in `graph/edges.jsonl`; summarize here for human readers._
