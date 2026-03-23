# From Single-Agent ADI to Multi-Agent Composition Failure  
**ACTC Extension Note — DUJ v0.3**

---

## Abstract

The single-agent ACTC setting establishes that when system influence capacity exceeds human counter-control, collapse of viability is inevitable regardless of downstream alignment mechanisms. This note asks whether the converse provides safety: if each agent in a multi-agent system individually satisfies the Autonomy Dominance Invariant (ADI), is shared viability preserved?

We show the answer is no. Individual admissibility is not closed under composition. Jointly admissible-looking agents can induce systematic drift and threshold crossing in a shared task-state through directional interference — not merely additive overload.

---

## 1. Motivation

ACTC v0.1 establishes that when  
\[
U > A + σ
\]  
collapse is inevitable.

ADI enforces:  
\[
U \le A - \Delta
\]

Question:  
If each agent satisfies ADI individually, is the system safe?

Answer: No.

---

## 2. Variable Interpretation

Let \(x_t \in \mathbb{R}\) denote shared task-state consistency.

Viability requires:
\[
|x_t| \le V
\]

Dynamics:
\[
x_{t+1} = x_t - k x_t + \text{influences} + \varepsilon_t
\]

---

## 3. Baseline Lemma

Individual admissibility does not imply joint admissibility.

(Additive case — omitted for brevity)

---

## 4. Main Proposition

**Proposition.**  
There exist agent influence laws \(u^{(1)}, u^{(2)}\), each satisfying ADI, such that joint dynamics exit viability solely due to interaction terms, even when linear aggregate influence is zero.

### Setup

\[
u^{(1)} = A - \Delta,\quad u^{(2)} = -(A - \Delta)
\]

Joint dynamics:

\[
x_{t+1} = x_t - k x_t + u^{(1)} + u^{(2)} + \gamma u^{(1)} u^{(2)} + \varepsilon_t
\]

### Linear cancellation

\[
u^{(1)} + u^{(2)} = 0
\]

### Interaction term

\[
u^{(1)} u^{(2)} = -(A-\Delta)^2
\]

### Reduced dynamics

\[
x_{t+1} = x_t - k x_t - \gamma (A-\Delta)^2 + \varepsilon_t
\]

### Equilibrium

\[
x^* = \frac{\gamma (A - \Delta)^2}{k}
\]

If:
\[
x^* > V
\]

then viability fails.

---

## 5. Simulation

Parameters chosen such that:

\[
x^* > V
\]

---

## 6. Connection to DUJ

Local admissibility ≠ global viability.  
Interaction structure induces failure.

DUJ operates at the level of:
> aggregate interaction constraints.

---

## 7. Scope

Minimal model.  
Interaction term illustrative, not exhaustive.

---
