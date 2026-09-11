---
type: paper
node_id: paper:heo2025_dynamic_preference_multiobjective
title: "Dynamic Preference Multi-Objective Reinforcement Learning for Internet Network Management"
authors: ["DongNyeong Heo", "Daniela Noemi Rim", "Heeyoul Choi"]
year: 2025
venue: "arXiv"
external_ids:
  arxiv: "2506.13153"
  doi: null
  s2: null
tags: []
added: 2026-09-10T12:00:39Z
---

# Dynamic Preference Multi-Objective Reinforcement Learning for Internet Network Management

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

> An internet network service provider manages its network with multiple objectives, such as high quality of service (QoS) and minimum computing resource usage. To achieve these objectives, a reinforcement learning-based (RL) algorithm has been proposed to train its network management agent. Usually, their algorithms optimize their agents with respect to a single static reward formulation consisting of multiple objectives with fixed importance factors, which we call preferences. However, in practice, the preference could vary according to network status, external concerns and so on. For example, when a server shuts down and it can cause other servers' traffic overloads leading to additional shutdowns, it is plausible to reduce the preference of QoS while increasing the preference of minimum computing resource usages. In this paper, we propose new RL-based network management agents that can select actions based on both states and preferences. With our proposed approach, we expect a single agent to generalize on various states and preferences. Furthermore, we propose a numerical method that can estimate the distribution of preference that is advantageous for unbiased training. Our experiment results show that the RL agents trained based on our proposed approach significantly generalize better with various preferences than the previous RL approaches, which assume static preference during training. Moreover, we demonstrate several analyses that show the advantages of our numerical estimation method.
