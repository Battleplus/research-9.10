---
type: paper
node_id: paper:bui2025_preferenceguided_learning_sparsereward
title: "Preference-Guided Learning for Sparse-Reward Multi-Agent Reinforcement Learning"
authors: ["The Viet Bui", "Tien Mai", "Hong Thanh Nguyen"]
year: 2025
venue: "arXiv"
external_ids:
  arxiv: "2509.21828"
  doi: null
  s2: null
tags: []
added: 2026-09-10T12:00:39Z
---

# Preference-Guided Learning for Sparse-Reward Multi-Agent Reinforcement Learning

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

> We study the problem of online multi-agent reinforcement learning (MARL) in environments with sparse rewards, where reward feedback is not provided at each interaction but only revealed at the end of a trajectory. This setting, though realistic, presents a fundamental challenge: the lack of intermediate rewards hinders standard MARL algorithms from effectively guiding policy learning. To address this issue, we propose a novel framework that integrates online inverse preference learning with multi-agent on-policy optimization into a unified architecture. At its core, our approach introduces an implicit multi-agent reward learning model, built upon a preference-based value-decomposition network, which produces both global and local reward signals. These signals are further used to construct dual advantage streams, enabling differentiated learning targets for the centralized critic and decentralized actors. In addition, we demonstrate how large language models (LLMs) can be leveraged to provide preference labels that enhance the quality of the learned reward model. Empirical evaluations on state-of-the-art benchmarks, including MAMuJoCo and SMACv2, show that our method achieves superior performance compared to existing baselines, highlighting its effectiveness in addressing sparse-reward challenges in online MARL.
