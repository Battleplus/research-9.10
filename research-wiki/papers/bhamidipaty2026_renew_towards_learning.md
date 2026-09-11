---
type: paper
node_id: paper:bhamidipaty2026_renew_towards_learning
title: "RENEW: Towards Learning World Models and Repairing Model Exploitation from Preferences"
authors: ["Logan Mondal Bhamidipaty", "Mykel Kochenderfer", "Subramanian Ramamoorthy"]
year: 2026
venue: "arXiv"
external_ids:
  arxiv: "2607.14180"
  doi: null
  s2: null
tags: []
added: 2026-09-10T13:05:54Z
---

# RENEW: Towards Learning World Models and Repairing Model Exploitation from Preferences

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

> World models are widely used in offline reinforcement learning (RL) to improve sample efficiency and generate experience beyond a fixed dataset. However, they are vulnerable to model exploitation where data coverage is thin. Prior work addresses this either by collecting more expert demonstrations, which is often expensive, unsafe, or unavailable, or by conservative algorithms that avoid uncertain regions, which limits generalization. We propose instead to repair exploitation directly using human preferences over imagined rollouts, leveraging the strong intuitive physics that allows humans to easily spot egregious dynamics hallucinations. We formalize this as Dynamics Learning from Human Feedback (DLHF), a Bradley-Terry preference loss over trajectory log-likelihoods under a learned dynamics model. Unfortunately, naive DLHF is sample inefficient, so we introduce RENEW, which uses epistemic uncertainty to focus finetuning where the model is most exploitable. We evaluate on several Jumanji and classic control environments and find that while naive DLHF requires an outsize preference budget, RENEW makes the framework practical by improving sample efficiency, limiting catastrophic forgetting, and reducing exploitation in pretrained world models. Taken together, our results provide initial evidence that preferences can supervise world model dynamics directly, offering a new approach to addressing exploitation in offline model-based RL.
