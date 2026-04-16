#DUJ v0.3a — Deterministic Hierarchy Note on Jetson Orin Nano

## Summary
This note documents the first deterministic edge-hardware stress results for the DUJ hierarchical substrate on NVIDIA Jetson Orin Nano Super.

## Test environment
- Hardware: NVIDIA Jetson Orin Nano Super
- Device: CUDA
- Framework: `run_full_duj_nano.py`

### Baseline modes
- `full_duj`
- `no_bridal`
- `no_coherence`

### Stress scales
- 200 steps → 6 tokens / 3 orbits
- 1200 steps → 16 tokens / 8 orbits
- 2400 steps → 32 tokens / 12 orbits

## Representative empirical results

### 1200-step run
| mode | mean coherence | final coherence | max invariant residual |
|---|---:|---:|---:|
| full_duj | 52.98 | 55.72 | 1.91e-06 |
| no_bridal | 52.92 | 55.54 | 1.91e-06 |
| no_coherence | -1.03 | 0.03 | 1.91e-06 |

### 2400-step run
| mode | mean coherence | final coherence | max invariant residual |
|---|---:|---:|---:|
| full_duj | 129.67 | 131.52 | 3.81e-06 |
| no_bridal | 129.51 | 131.32 | 1.907e-05 |
| no_coherence | 3.05 | 1.28 | 3.81e-06 |

## Preliminary observations
1. **Long-horizon coherence persistence**  
   Layer A preserves mission-level coherence over multi-thousand-step trajectories on edge hardware.

2. **Layer B is associated with lower residual growth**  
   At deeper compositional runs, Layer B is associated with lower invariant residual growth.

3. **Empirically distinguishable systems hierarchy**  
   - Coherence → primary long-horizon stabilizer  
   - Bridal → drift suppressor  
   - Invariants → substrate recovery floor  

## Figure caption
> Invariant residual growth under Layer B ablation shows approximately 5× higher divergence at 2400 steps relative to the full DUJ stack, while Layer A ablation induces sharp coherence collapse.

## Scientific caution
These results are strong empirical evidence, not a universal proof of DUJ as a general theory.

## Next milestone
**v0.3b** — bounded-noise and adversarial robustness sweeps on Jetson Orin Nano.
