---
type: paper
node_id: paper:li2026_safe_reinforcement_learning
title: "Safe Reinforcement Learning with Preference-based Constraint Inference"
authors: ["Chenglin Li", "Grant Ruan", "Hua Geng"]
year: 2026
venue: "arXiv"
external_ids:
  arxiv: "2603.23565"
  doi: null
  s2: null
tags: []
added: 2026-09-10T12:00:39Z
---

# Safe Reinforcement Learning with Preference-based Constraint Inference

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

> Safe reinforcement learning (RL) is a standard paradigm for safety-critical decision making. However, real-world safety constraints can be complex, subjective, and even hard to explicitly specify. Existing works on constraint inference rely on restrictive assumptions or extensive expert demonstrations, which are not realistic in many real-world applications. How to cheaply and reliably learn these constraints is the major challenge we focus on in this study. While inferring constraints from human preferences offers a data-efficient alternative, we identify popular Bradley-Terry (BT) models fail to capture the asymmetric, heavy-tailed nature of safety costs, resulting in risk underestimation. It is still rare in the literature to understand the impacts of BT models on the downstream policy learning. To address the above knowledge gaps, we propose a novel approach namely Preference-based Constrained Reinforcement Learning (PbCRL). We introduce a novel dead zone mechanism into preference modeling and theoretically prove that it encourages heavy-tailed cost distributions, thereby achieving better constraint alignment. Additionally, we incorporate a Signal-to-Noise Ratio (SNR) loss to encourage exploration by cost variances, which is found to benefit policy learning. Further, two-stage training strategy is deployed to lower online labeling burdens while adaptively enhancing constraint satisfaction. Empirical results demonstrate that PbCRL achieves superior alignment with true safety requirements and outperforms state-of-the-art baselines in terms of safety and reward. Our work explores a promising and effective way for constraint inference in Safe RL, with great potential in various safety-critical applications.
