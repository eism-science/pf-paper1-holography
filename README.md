# Unequal Information as a Post-Selected Signature of Holographic Structure in Quantum Error-Correcting Codes

Data and analysis notebooks for the paper:

> Under Pauli noise models, the entropy reduction &Delta;H from incorporating a backward temporal boundary into quantum error correction is provably zero. On real quantum hardware, we measure &Delta;H > 1 bit on every code tested &mdash; revealing more than one bit per shot of decodable information invisible to all conventional syndrome-only decoders.

## Repository structure

```
data/
  happy_553.npz          # [[5,1,3]] HaPPY code, IBM Fez, 32 circuits x 8192 shots
  steane_713.npz         # Steane [[7,1,3]], IBM Fez, 44 circuits x 8192 shots
  shor_913.npz           # Shor [[9,1,3]], IBM Fez, 44 circuits x 8192 shots
  surface_d3_L{0,1}.npz  # Rotated surface code d=3 (supporting data)
  surface_d5_L{0,1}.npz  # Rotated surface code d=5 (supporting data)
  surface_d7_L{0,1}.npz  # Rotated surface code d=7 (supporting data)
  weak_measurement_553.npz      # [[5,1,3]] weak measurement alpha sweep, IBM Fez, 5 jobs x 32 circuits x 8192 shots
  strength_sweep_results.npz    # Computational beta sweep reference data (projective limit)
  fanout_diagnostic_results.npz # Per-stabilizer fan-out diagnostics from beta sweep

notebooks/
  isotropy_gap_analysis.ipynb            # Main analysis: DeltaH, isotropy CV, permutation tests, ablation
  dbci_shor_913_hardware.ipynb           # Shor [[9,1,3]] as second non-holographic control
  dbci_553_complementary_recovery.ipynb  # Complementary recovery threshold on [[5,1,3]]
  dbci_depth2_happy_simulation.ipynb     # Depth-2 HaPPY [[20,1,d>=3]] simulation
  dbci_weak_measurement_hardware.ipynb   # Physical weak measurement (alpha sweep) and alpha-beta duality
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
pip install numpy matplotlib qiskit
jupyter notebook notebooks/isotropy_gap_analysis.ipynb
```

For notebooks that retrieve results from IBM Quantum (Shor, complementary recovery), set the `IBM_QUANTUM_TOKEN` environment variable or paste your token where indicated. All job IDs are included for data provenance; results can be reproduced from the saved `.npz` files without re-running hardware jobs.

## Citation

Paper in preparation.

## License

Copyright 2026 EISM Science. All rights reserved.

Data and code are provided for review and reproducibility. License terms will be specified upon publication.
