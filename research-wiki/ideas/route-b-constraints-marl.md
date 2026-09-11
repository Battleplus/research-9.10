---
type: idea
node_id: idea:route-b-constraints-marl
title: "Separating Task Preference from Safety Constraints in Preference-Based Cooperative MARL"
stage: proposed
outcome: pending
added: 2026-09-10T12:06:01Z
based_on: ["paper:cosner2022_safetyaware_preferencebased_learning", "paper:gong2025_offline_safe_policy", "paper:li2026_safe_reinforcement_learning"]
target_gaps: ["gap:G3"]
tags: ["related", "safe RL", "preference-based RL", "constraints", "MARL"]
---

# Separating Task Preference from Safety Constraints in Preference-Based Cooperative MARL

**stage:** `proposed`  ·  **outcome:** `pending`

Related direction: separate task preference feedback from independent safety constraints and measure error-to-violation propagation.

## Thesis
Independent task-preference and safety-constraint channels can preserve preferred behavior while reducing hard violations and tail risk in cooperative MARL.

## Key risks
Requires a real independent safety signal, suitable benchmark, constrained optimization expertise, and stronger evaluation; a penalty-shaped reward would not be a contribution.

## Connections
_Edges are recorded in `graph/edges.jsonl`; summarize here for human readers._
