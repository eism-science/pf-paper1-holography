# Hardware Evidence for Unequal Information Distribution in Holographic Quantum Codes

Data and analysis notebooks for the paper:

> Under Pauli noise models, the entropy reduction &Delta;H from incorporating a backward temporal boundary into quantum error correction is provably zero. On real quantum hardware, we measure &Delta;H > 1 bit on every code tested, revealing structured entropy reduction from a calibration-based backward boundary whose spatial distribution distinguishes holographic from non-holographic codes.

## Repository structure

```
data/
  happy_553.npz                   # [[5,1,3]] HaPPY code, IBM Fez, 32 circuits x 8192 shots
  steane_713.npz                  # Steane [[7,1,3]], IBM Fez, 44 circuits x 8192 shots
  shor_913.npz                    # Shor [[9,1,3]], IBM Fez, 44 circuits x 8192 shots
  surface_d{3,5,7}_L{0,1}.npz    # Rotated surface codes (supporting data)
  weak_measurement_553.npz        # [[5,1,3]] alpha sweep, IBM Fez
  strength_sweep_results.npz      # Computational beta sweep reference
  fanout_diagnostic_results.npz   # Per-stabilizer fan-out diagnostics

notebooks/primary/                # Core experiments (one per main result)
  dbci_553_holographic_hardware   # §3.1  DeltaH > 0 on HaPPY hardware
  dbci_isotropy_reanalysis        # §3.2  Isotropy gap (37x HaPPY vs Steane)
  dbci_553_complementary_recovery # §3.3  Four-boundary ablation (109x degradation)
  dbci_weak_value_strength_sweep  # §3.4  Beta sweep, per-stabilizer curves, 42x peak
  dbci_weak_measurement_hardware  # §3.6  Alpha-beta duality (spread ratio 1.000)

notebooks/supporting/             # Controls, validations, and secondary analyses
  dbci_steane_713_hardware        # Steane [[7,1,3]] non-holographic control
  dbci_shor_913_hardware          # Shor [[9,1,3]] non-holographic control
  dbci_readout_conditioned_delta_H # §3.5  Readout-conditioned null (controlled negative)
  dbci_repeated_syndrome_happy    # §3.5  Repeated syndrome null (controlled negative)
  dbci_cross_device_marrakech     # §4.1  Cross-device validation (Fez vs Marrakesh)
  dbci_prior_free_isotropy        # §4.1  Forward-only isotropy (CV < 0.03%)
  dbci_modular_weak_value_correlation # §4.3  Complement qubit mapping (rho = 1.000)
  dbci_isotropy_weighting         # §4.3  DeltaH vs fidelity anti-correlation
  dbci_delta_H_hardware           # §3.1  Cross-code DeltaH computation
  dbci_depth2_happy_simulation    # Depth-2 HaPPY [[20,1,d>=3]] prediction
```

## Hardware

All experiments were run on IBM quantum processors via the Qiskit SDK and SamplerV2 runtime primitive:

| Backend | Processor | Qubits | Role |
|---------|-----------|--------|------|
| IBM Fez | Heron r2 | 156 | Primary |
| IBM Marrakesh | Heron r2 | 156 | Cross-device validation |

## Key results

| Code | &Delta;H (bits) | SEM | CV (isotropy) |
|------|-----------------|-----|---------------|
| [[5,1,3]] HaPPY | 1.230 | &pm;0.0012 | 6.6&ndash;8.2% |
| Steane [[7,1,3]] | 2.210 | &pm;0.0004 | 0.1&ndash;0.2% |
| Shor [[9,1,3]] | 2.008 | &pm;0.0008 | 1.9&ndash;3.3% |

## Reproducing the analysis

The notebooks load raw data from `data/` and reproduce all figures and statistics reported in the paper. No QPU access is required.

```bash
pip install numpy scipy matplotlib qiskit
jupyter notebook notebooks/primary/dbci_553_holographic_hardware.ipynb
```

## Citation

Paper in preparation.

## License

Copyright 2026 EISM Science. All rights reserved.

Data and code are provided for review and reproducibility. License terms will be specified upon publication.
