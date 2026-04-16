# DUJ v0.3b — Multi-Agent Interaction Baseline (Jetson Orin Nano)

## Objective

Evaluate whether the DUJ hierarchical structure remains observable under dual-agent interaction, including adversarial coupling and stochastic perturbation.

This experiment is not intended to demonstrate optimality or universality, but to establish a reproducible multi-agent baseline.

---

## Setup

**Hardware**
- NVIDIA Jetson Orin Nano

**Agents**
- Two agents (A, B)
- Shared state interaction

**Scenarios**
- `aligned`
- `mild_conflict`
- `adversarial`

**Modes (Ablations)**
- `full_duj` → full hierarchy active
- `no_bridal` → Layer B removed
- `no_coherence` → Layer A removed

**Parameters**
- Steps: 1200 → 2400
- Coupling: 0.15 → 0.6
- Noise scale: 0.002 → 0.02
- Seed: 7

---

## Commands Used

```bash
python3 run_duj_multi_agent.py --steps 1200 --all-modes --all-scenarios --write-results

python3 run_duj_multi_agent.py --steps 2400 --scenario adversarial --all-modes --coupling 0.3 --write-results

python3 run_duj_multi_agent.py --steps 2400 --scenario adversarial --all-modes --coupling 0.6 --noise-scale 0.02 --write-results


⸻

Results (Batch Summary)

Baseline (1200 steps)

aligned        | full_duj     | finalA= 98.9 | finalB= 98.9 | maxRes=0
aligned        | no_bridal    | finalA= 98.9 | finalB= 98.9 | maxRes=0
aligned        | no_coherence | finalA=-50.0 | finalB=-50.0 | maxRes=0

mild_conflict  | full_duj     | finalA= 72.3 | finalB= 72.1 | maxRes=0
mild_conflict  | no_bridal    | finalA= 72.7 | finalB= 72.4 | maxRes=0
mild_conflict  | no_coherence | finalA= 69.2 | finalB= 55.2 | maxRes=0

adversarial    | full_duj     | finalA=-217  | finalB=-217  | maxRes=7e-02
adversarial    | no_bridal    | finalA=-216  | finalB=-216  | maxRes=7e-02
adversarial    | no_coherence | finalA=-201  | finalB=-201  | maxRes=1.6e-01


⸻

Extended Stress (2400 steps, coupling = 0.3)

adversarial | full_duj     | finalA=-217 | finalB=-217 | maxRes=2.37e-01
adversarial | no_bridal    | finalA=-216 | finalB=-216 | maxRes=2.38e-01
adversarial | no_coherence | finalA=-205 | finalB=-205 | maxRes=3.42e-01


⸻

High Stress (2400 steps, coupling = 0.6, noise = 0.02)

adversarial | full_duj     | finalA=-217 | finalB=-217 | maxRes=6.84e-01
adversarial | no_bridal    | finalA=-216 | finalB=-216 | maxRes=6.85e-01
adversarial | no_coherence | finalA=-210 | finalB=-210 | maxRes=7.89e-01


⸻

Key Observations
	1.	Coherence layer (Layer A) removal increases instability
	•	no_coherence consistently shows higher joint residual than full_duj
	2.	Bridal layer (Layer B) has limited effect in this configuration
	•	no_bridal remains close to full_duj across tested regimes
	3.	System remains bounded under stress
	•	No collapse events observed
	•	No numerical divergence
	•	Stability preserved despite increased coupling and noise

⸻

Interpretation

These results indicate that:
	•	The DUJ hierarchy remains empirically distinguishable under multi-agent interaction
	•	The coherence layer contributes to residual suppression
	•	However, the current system does not exhibit catastrophic failure modes under tested conditions

This suggests the system is operating in a controlled instability regime, rather than near a collapse boundary.

⸻

Limitations
	•	No observed collapse → cannot yet demonstrate necessity of invariant constraint
	•	Toy environment → limited dimensionality and interaction complexity
	•	Invariant projection remains active → prevents unconstrained divergencej

⸻

Next Steps

Future experiments will target structural failure regimes, including:
	•	Removal of invariant projection
	•	Stronger adversarial coupling
	•	Extended horizon stress tests
	•	Cross-agent determinism validation

Goal:

Determine whether DUJ acts as a necessary substrate constraint for multi-agent stability.

⸻

Status

This document represents a baseline empirical result, not a final claim.

It establishes the first reproducible multi-agent DUJ test on edge hardware.

---
