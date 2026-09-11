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

Cooperative-MARL preference querying lacks a verified test of whether short-horizon joint-dynamics uncertainty identifies coordination-decision ambiguity better than policy coverage, reward-model disagreement, independent-agent scores, or diversity under a fixed task-preference label budget.
