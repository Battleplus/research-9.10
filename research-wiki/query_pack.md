# Research Wiki Query Pack

_Auto-generated. Do not edit._

## Open Gaps
# Gap Map

_Field gaps with stable IDs._

## G1

Group-level preference labels in cooperative MARL do not directly expose which agent-time transitions caused the outcome; existing code and papers leave the interaction between temporal credit assignment, uncertainty, and feedback selection under-specified.

## G2

World-model errors can be amplified by preference-reward optimization. A direction needs an explicit model-exploitation or uncertainty-calibration test rather than reporting only policy return.

## G3

Task preference and safety constraints are often conflated in a single scalar objective; the cooperative-MARL setting still needs independent constraint evidence and error-to-violation analysis.

## G4

Dynamic or agent-specific preference adaptation needs a genuine changing-preference process, partial observability, and adaptation/regret metrics; simple preference conditioning is not enough.

## G5

Cooperative-MARL preference querying lacks a verified test of whether short-horizon joint-dynamics uncertainty identifies coordination-decision ambiguity better than policy coverage, reward-model disagreement, independent-agent scores, or diversity under a fixed task-preference
## Key Papers (20 total)
- [paper:bhamidipaty2026_renew_towards_learning] RENEW: Towards Learning World Models and Repairing Model Exploitation from Preferences
- [paper:buetgolfouse2023_robust_multiobjective_reinforcement] Robust Multi-Objective Reinforcement Learning with Dynamic Preferences: Studies robust policies for changing multi-objective preference weights.
- [paper:bui2025_preferenceguided_learning_sparsereward] Preference-Guided Learning for Sparse-Reward Multi-Agent Reinforcement Learning
- [paper:christiano2017_deep_reinforcement_learning] Deep reinforcement learning from human preferences
- [paper:cosner2022_safetyaware_preferencebased_learning] Safety-Aware Preference-Based Learning for Safety-Critical Control: Combines safety-aware preference learning with control barrier functions to tune safe and performant controllers.
- [paper:gong2025_offline_safe_policy] Offline Safe Policy Optimization From Heterogeneous Feedback
- [paper:heo2025_dynamic_preference_multiobjective] Dynamic Preference Multi-Objective Reinforcement Learning for Internet Network Management
- [paper:heo2026_policy_likelihoodbased_query] Policy Likelihood-based Query Sampling and Critic-Exploited Reset for Efficient Preference-based Reinforcement Learning: Policy-likelihood query sampling and critic-triggered reset address stale queries and reward overestimation in single-agent PbRL; it does not use a wo
- [paper:kaufmann2023_survey_reinforcement_learning] A Survey of Reinforcement Learning from Human Feedback
- [paper:kim2025_human_implicit_preferencebased] Human Implicit Preference-Based Policy Fine-tuning for Multi-Agent Reinforcement Learning in USV Swarm
- [paper:kou2025_offline_multiagent_preferencebased] Offline Multi-Agent Preference-Based RL with Agent-aware DPO: Agent-aware preference optimization add
## Recent Relationships (28 total)
  idea:route-b-constraints-marl --inspired_by--> paper:gong2025_offline_safe_policy
  idea:route-b-constraints-marl --inspired_by--> paper:li2026_safe_reinforcement_learning
  idea:route-b-constraints-marl --addresses_gap--> gap:G3
  idea:route-c-dynamic-preference-morl --inspired_by--> paper:heo2025_dynamic_preference_multiobjective
  idea:route-c-dynamic-preference-morl --inspired_by--> paper:mu2026_multiagent_reinforcement_learning
  idea:route-c-dynamic-preference-morl --addresses_gap--> gap:G4
  idea:route-c-dynamic-preference-morl --inspired_by--> paper:record2026_dynamic_preference_inference
  idea:route-c-dynamic-preference-morl --inspired_by--> paper:buetgolfouse2023_robust_multiobjective_reinforcement
  idea:route-a-world-model-marl --inspired_by--> paper:zhu2024_decoding_global_preferences
  idea:route-a-world-model-marl --inspired_by--> paper:heo2026_policy_likelihoodbased_qu
