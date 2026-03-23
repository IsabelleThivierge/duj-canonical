# From Single-Agent ADI to Multi-Agent Composition Failure

ACTC Extension Note — DUJ v0.3

---

## Abstract

The single-agent ACTC setting establishes that when system influence capacity exceeds human counter-control, collapse of viability is inevitable regardless of downstream alignment mechanisms. This note asks whether the converse provides safety: if each agent in a multi-agent system individually satisfies the Autonomy Dominance Invariant (ADI), is shared viability preserved?

We show the answer is no. Individual admissibility is not closed under composition. Jointly admissible-looking agents can induce systematic drift and threshold crossing in a shared task-state through directional interference — not merely additive overload.

---

## 1. Motivation

ACTC v0.1 establishes that when

U > A + σ

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

Each agent contributes an influence on the shared state. The system includes a stabilizing force that counteracts drift.

---

## 3. Baseline Lemma (Additive Case)

Individual admissibility does not imply joint admissibility.

(Additive case — omitted for brevity.)

---

## 4. Main Proposition (Interaction-Induced Composition Failure)

**Proposition.**  
There exist agent influence laws u^(1), u^(2), each satisfying ADI, such that joint dynamics exit viability solely due to interaction terms, even when linear aggregate influence is zero.

### Setup

u^(1) = A − Δ  
u^(2) = −(A − Δ)

Joint dynamics:

x_{t+1} = x_t − k x_t + u^(1) + u^(2) + γ u^(1) u^(2) + ε_t

### Linear cancellation

u^(1) + u^(2) = 0

### Interaction term

γ u^(1) u^(2) = −γ (A − Δ)^2

### Reduced dynamics

x_{t+1} = x_t − k x_t − γ (A − Δ)^2 + ε_t

### Shifted equilibrium

x* = γ (A − Δ)^2 / k

If x* > V, the system exits viability.

### Key observation

The drift is not produced by either agent individually. It emerges purely from interaction.

### Corollary

Admissibility is not closed under composition and not decomposable: global failure can occur with no local violation.

---

## 5. Simulation

Parameters are chosen such that:

x* = γ (A − Δ)^2 / k > V

This ensures the interaction-induced failure regime is active.

Three conditions:

1. Agent 1 alone  
2. Agent 2 alone  
3. Joint system  

Expected result:

- Single-agent: no collapse  
- Joint system: high collapse probability  

---

## 6. Connection to DUJ

This result shows that enforcing ADI locally is insufficient.

Failure emerges from interaction structure, not individual behavior.

DUJ therefore operates at the level of aggregate influence, enforcing constraints on the joint system rather than on individual agents.

---

## 7. Scope and Limits

The model is minimal and structural. The interaction term γ u^(1) u^(2) is a tractable example, not a claim about all real systems.

Grounding x_t in a concrete measurable system is left for future work.
