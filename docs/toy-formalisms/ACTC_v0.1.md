# DUJ Toy Formalism v0.1  
## The Autonomy-Constrained Token Channel (ACTC)

**Note:** This is a *toy formalism inspired by DUJ (Dynamiques Unifiées des Jetons)*, designed to demonstrate why **substrate-level invariants** are necessary for preserving human agency in multi-agent systems. It is **not** the DUJ framework itself.

---

## Objects
- Agents: a **human** \(H\) and a **system** \(S\).
- Token channel: a flow of abstract **influence tokens** \(u_t\) from \(S\) to the environment that affects the feasible action set of \(H\).

---

## State
Let the human’s state be \(x_t \in \mathbb{R}\), interpreted as an **autonomy margin**:
- \(x_t > 0\): human retains meaningful control/options,
- \(x_t \le 0\): human is functionally marginalized (collapse of agency).

---

## Dynamics
\[
x_{t+1} = x_t + a_t - u_t + \eta_t
\]
where:
- \(a_t \in [-A, A]\) is the human’s chosen action (bounded capability),
- \(u_t \in [0, U]\) is the system’s token influence (bounded authority),
- \(\eta_t\) is disturbance/noise (stochastic or adversarial).

This deliberately minimal dynamic captures **direct competition between system influence and human counter-control**, without rewards, preferences, or intent modeling.

---

## Viability and Human Agency
Define the **viability set**:
\[
\mathcal{V} = \{x \in \mathbb{R} \mid x \ge 0\}.
\]

Human agency is treated as a **structural viability condition**:
\[
\Pr(x_t \in \mathcal{V}\ \forall t) \ge 1-\epsilon
\]
(or deterministically \(x_t \ge 0\ \forall t\)).

---

## The DUJ-Inspired Substrate Invariant
**Autonomy Dominance Invariant (ADI).**  
The system’s influence capacity must be bounded such that human counter-control can always offset it, even under disturbance:
\[
U \le A - \Delta,
\]
for some robustness margin \(\Delta > 0\).

ADI is a **substrate constraint on channel authority**, not a policy or objective.

---

## Forced Distinction Theorem
**Collapse under invariant violation.**  
Assume worst-case disturbance \(\eta_t \in [-\sigma, \sigma]\).  
If
\[
U > A + \sigma,
\]
then for any initial \(x_0\) there exists a valid sequence of system influences \(\{u_t\}\) and disturbances \(\{\eta_t\}\) such that **for every human strategy** \(\{a_t\}\),
\[
\exists T:\ x_T < 0.
\]

**Proof sketch.**  
Choose \(u_t = U\) and \(\eta_t = -\sigma\) at each step. Then
\[
x_{t+1} \le x_t + A - U - \sigma,
\]
which is strictly negative when \(U > A + \sigma\), forcing \(x_t\) to cross below zero in finite time.

**Interpretation.**  
When system influence authority exceeds human counter-control (plus disturbance), **collapse of human viability is inevitable**, regardless of downstream alignment mechanisms (policies, constitutions, rewards, oversight). This establishes a structural necessity for substrate-level constraints.

---

## Scope and Limits
The ACTC model is intentionally minimal. It does not attempt to model real human cognition, full AI systems, or concrete token semantics. Its sole purpose is to demonstrate a structural distinction: **when system influence capacity exceeds human counter-control, collapse of human viability is inevitable regardless of downstream alignment mechanisms**. No claim is made that ADI is the only relevant invariant, nor that this model captures all real-world failure modes.

---

**Status:** **v0.1 locked.** This toy is complete as a minimal counterexample to protocol-only alignment and will not be expanded except to clarify assumptions or correct errors.
