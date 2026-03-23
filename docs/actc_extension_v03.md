## From Single-Agent ADI to Multi-Agent Composition Failure

ACTC Extension Note — DUJ v0.3

---

## Abstract

The single-agent ACTC setting establishes that when system influence capacity exceeds human counter-control, collapse of viability is inevitable regardless of downstream alignment mechanisms. This note asks whether the converse provides safety: if each agent in a multi-agent system individually satisfies the Autonomy Dominance Invariant (ADI), is shared viability preserved?

We show the answer is no. Individual admissibility is not closed under composition. Jointly admissible-looking agents can induce systematic drift and threshold crossing in a shared task-state through directional interference — not merely additive overload.

---

## 1. Motivation

ACTC v0.1 establishes that when U > A + σ,

collapse is inevitable.

ADI enforces the constraint:

U ≤ A − Δ

Key question:  
If each agent satisfies ADI individually, is the system safe?

Answer: No.

---

## 2. Variable Interpretation

Let x_t ∈ ℝ denote shared task-state consistency.

Viability requires:

|x_t| ≤ V

Each agent contributes an influence on the shared task-state. The system includes a stabilizing force that counteracts drift.

---

## 3. Baseline Lemma

Individual admissibility does not imply joint admissibility.

(Additive case — omitted for brevity)

---

## 4. Main Proposition

Proposition.  
There exist agent influence laws u1 and u2, each satisfying ADI, such that joint dynamics exit viability solely due to interaction terms, even when linear aggregate influence is zero.

### Setup

u1 = A − Δ  
u2 = −(A − Δ)

### Dynamics

x(t+1) = x(t) − k·x(t) + u1 + u2 + γ·u1·u2 + ε

### Key Observation

The linear terms cancel:

u1 + u2 = 0

However, the interaction term remains:

γ·u1·u2 = −γ(A − Δ)²

This introduces a constant drift.

### Shifted Equilibrium

x* = γ(A − Δ)² / k

If x* > V, the system exits the viability region.

### Conclusion

Neither agent alone produces failure.  
Failure emerges from interaction structure.

Admissibility is not closed under composition.

---

## 5. Simulation

The simulation instantiates the analytical dynamics.

| Parameter | Value |
|----------|------|
| k (stabilizer gain) | 0.3 |
| V (viability threshold) | 10.0 |
| A (agent capacity) | 1.0 |
| Δ (robustness margin) | 0.1 |
| γ (interaction coupling) | 4.0 |
| σ (noise) | 0.05 |
| T_max | 500 |
| n_trials | 300 |

For these values:

x* = 10.8 > V

Single agents remain stable.  
Joint system collapses.

---

## 6. Connection to DUJ

This result shows that coordination constraints must operate above individual agents.

Local compliance does not imply global viability.

DUJ acts as a coordination layer enforcing constraints on joint interaction structure rather than individual agents.

---

## 7. Scope and Limits

The model is minimal and structural.

The interaction term is illustrative, not exhaustive.

Grounding the variables in real systems is left for future work.
