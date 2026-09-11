---
type: paper
node_id: paper:liu2023_efficient_preferencebased_reinforcement
title: "Efficient Preference-Based Reinforcement Learning Using Learned Dynamics Models"
authors: ["Yi Liu", "Gaurav Datta", "Ellen Novoseller", "Daniel S. Brown"]
year: 2023
venue: "arXiv"
external_ids:
  arxiv: "2301.04741"
  doi: null
  s2: null
tags: []
added: 2026-09-10T12:00:39Z
---

# Efficient Preference-Based Reinforcement Learning Using Learned Dynamics Models

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

> Preference-based reinforcement learning (PbRL) can enable robots to learn to perform tasks based on an individual's preferences without requiring a hand-crafted reward function. However, existing approaches either assume access to a high-fidelity simulator or analytic model or take a model-free approach that requires extensive, possibly unsafe online environment interactions. In this paper, we study the benefits and challenges of using a learned dynamics model when performing PbRL. In particular, we provide evidence that a learned dynamics model offers the following benefits when performing PbRL: (1) preference elicitation and policy optimization require significantly fewer environment interactions than model-free PbRL, (2) diverse preference queries can be synthesized safely and efficiently as a byproduct of standard model-based RL, and (3) reward pre-training based on suboptimal demonstrations can be performed without any environmental interaction. Our paper provides empirical evidence that learned dynamics models enable robots to learn customized policies based on user preferences in ways that are safer and more sample efficient than prior preference learning approaches. Supplementary materials and code are available at https://sites.google.com/berkeley.edu/mop-rl.
