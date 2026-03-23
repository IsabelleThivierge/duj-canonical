# From Single-Agent ADI to Multi-Agent Composition Failure

ACTC Extension Note — DUJ v0.3

---

## Abstract

The single-agent ACTC setting establishes that when system influence capacity exceeds human counter-control, collapse of viability is inevitable regardless of downstream alignment mechanisms. This note asks whether the converse provides safety: if each agent in a multi-agent system individually satisfies the Autonomy Dominance Invariant (ADI), is shared viability preserved?

We show the answer is no. Individual admissibility is not closed under composition. Jointly admissible-looking agents can induce systematic drift and threshold crossing in a shared task-state through directional interference — not merely additive overload.

This establishes a structural necessity for coordination constraints that operate above the level of individual agents.

---

## 1. Motivation

ACTC v0.1 establishes that when U > A + σ, collapse is inevitable.

ADI enforces the constraint:

U ≤ A − Δ

Key question:  
If each agent satisfies ADI individually, is the system safe?

Answer: No.

---

## 2. Variable Interpretation

Let x_t ∈ ℝ denote the shared task-state consistency of a multi-agent system at time t.

The dynamics are interpreted as a stabilized system subject to external influence terms, where viability corresponds to boundedness of the state trajectory.

- Small |x_t|: system remains coherent, jointly interpretable, and aligned  
- Large |x_t|: system drifts, fragments, or enters incompatible update pressure  

Viability requires:

|x_t| ≤ V

Each agent contributes a signed influence on the shared state. The system includes a stabilizing force that counteracts drift.

Single-agent admissibility (ADI):

|u^(i)| ≤ A − Δ

---

## 3. Baseline Lemma (Additive Case)

Lemma. Individual admissibility does not imply joint admissibility under additive composition.

Two agents can each satisfy ADI individually while their combined influence exceeds system capacity, leading to viability failure.

This case is structurally correct but arithmetically thin. The main proposition shows that failure can arise purely from interaction structure, even when linear aggregate influence is zero.

---

## 4. Main Proposition (Interaction-Induced Composition Failure)

Proposition.  
There exist agent influence laws u^(1), u^(2), each satisfying ADI, such that joint system dynamics admit trajectories exiting the viability set due solely to interaction terms, even when linear aggregate influence is zero.

### Setup

u^(1) = A − Δ  
u^(2) = −(A − Δ)

Joint dynamics:

x_{t+1} = x_t − k x_t + u^(1) + u^(2) + γ u^(1) u^(2) + ε_t

### Linear cancellation

u^(1) + u^(2) = 0

The additive lemma does not apply.

### Interaction term

γ u^(1) u^(2) = −γ (A − Δ)^2

This introduces a constant drift independent of x_t, not counteracted by the stabilizer at equilibrium.

### Reduced dynamics

x_{t+1} = x_t − k x_t − γ (A − Δ)^2 + ε_t

### Shifted equilibrium

Setting x_{t+1} = x_t:

x* = γ (A − Δ)^2 / k

If x* > V, the equilibrium lies outside the viability set, implying eventual threshold crossing under the induced drift.

### Key observation

Neither agent alone produces this drift. It is generated purely by their interaction — invisible at the level of individual agent analysis.

### Corollary

Admissibility is not only non-closed under composition, but non-decomposable: there exist global violations with no local witness.

---

## 5. Simulation

The simulation directly instantiates the analytical dynamics above. Parameters are calibrated so that the interaction-shifted equilibrium satisfies x* > V.

### Parameter regime

| Parameter | Value |
|----------|------|
| k (stabilizer gain) | 0.3 |
| V (viability threshold) | 10.0 |
| A (agent capacity) | 1.0 |
| Δ (robustness margin) | 0.1 |
| γ (interaction coupling) | 4.0 |
| σ (noise std) | 0.05 |
| T_max | 500 |
| n_trials | 300 |

For these values:

x* = γ (A − Δ)^2 / k = 10.8 > V

The system is therefore analytically expected to exit the viability set under joint dynamics, while remaining stable under single-agent conditions.

Three conditions are simulated:

1. Agent 1 alone  
2. Agent 2 alone  
3. Joint system  

Expected outcome:

- Single-agent: near-zero collapse probability  
- Joint system: high collapse probability  

The coefficient γ captures interaction coupling strength — second-order effects such as interference, feedback amplification, or update-order sensitivity.

---

## 6. Connection to DUJ

This result establishes why coordination constraints must operate above the level of individual agent properties.

If ADI is enforced only locally — each agent checked in isolation — composition failure remains possible.

Failure emerges from interaction geometry, not individual behavior.

DUJ therefore operates on the closure properties of admissibility under composition.

---

## 7. Scope and Limits

The model is intentionally minimal. The interaction term γ u^(1) u^(2) is one tractable formalization of agent interference and is not claimed to be exhaustive.

The result is structural: it demonstrates that the failure mode exists, not that it is ubiquitous.

The variables remain abstract. Grounding x_t in a concrete measurable system state is left for subsequent work.
