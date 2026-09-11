---
type: paper
node_id: paper:mu2026_multiagent_reinforcement_learning
title: "Multi-Agent Reinforcement Learning via Agent-Specific Preference"
authors: ["Ni Mu", "Yao Luan", "Yiqin Yang", "Qing-Shan Jia"]
year: 2026
venue: "arXiv"
external_ids:
  arxiv: "2608.08604"
  doi: null
  s2: null
tags: []
added: 2026-09-10T13:05:54Z
---

# Multi-Agent Reinforcement Learning via Agent-Specific Preference

## One-line thesis
_TODO: fill in after reading._

## Problem / Gap
_TODO._

## Method
_TODO._

## Key Results
_TODO._

## Assumptions
_TODO._

## Limitations / Failure Modes
_TODO._

## Reusable Ingredients
_TODO._

## Open Questions
_TODO._

## Claims
_TODO._

## Connections
_Edges are recorded in `graph/edges.jsonl`; summarize here for human readers._

## Relevance to This Project
_TODO._

## Abstract (original)

> Multi-agent reinforcement learning (MARL) is a powerful framework for solving complex collaborative tasks, but it relies heavily on well-defined global reward functions. Designing such rewards is challenging, especially in systems with heterogeneous agents, where a single scalar objective may fail to capture diverse behaviors. In this paper, we introduce Multi-AGent Preference-Integrated lEarning (MAGPIE), which addresses these challenges through agent-specific preference modeling. Each agent is evaluated by a dedicated expert through preference signals, eliminating the need for global evaluation. We theoretically prove that optimizing these decentralized preferences converges to a Nash equilibrium policy. To integrate local preferences into a coherent global objective, we construct agent-specific reward models from preference data and combine them via a monotonic aggregation mechanism. We further prove that optimizing this aggregate reward model is equivalent to training the Nash equilibrium policy. Extensive experiments on benchmark multi-agent tasks and a sequential production line task show that MAGPIE achieves performance comparable to reward-engineered baselines, demonstrating its potential to facilitate policy learning in scenarios where precise reward engineering is impractical.
