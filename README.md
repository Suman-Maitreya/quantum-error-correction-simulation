# Simulating Quantum Error Correction

**Pseudo-Threshold Analysis of 3-Qubit Repetition Codes and 9-Qubit Shor Code under Depolarizing and Amplitude Damping Noise**

Team 7 — AID B, Amrita Vishwa Vidyapeetham

## Overview

This project simulates three quantum error correction (QEC) codes using Qiskit and benchmarks their performance against realistic noise models. We measure logical error rates, post-correction fidelity, and empirical pseudo-thresholds — then compare against the analytical scaling law predicted by Thakur et al. (2025).

## Codes Implemented

| Code | Qubits | Corrects | Notebook |
|------|--------|----------|----------|
| 3-Qubit Bit-Flip | 3 data + 2 ancilla | Bit-flip (X) errors | `Phase2_BitFlip_Code.ipynb` |
| 3-Qubit Phase-Flip | 3 data + 2 ancilla | Phase-flip (Z) errors | `Phase2_PhaseFlip_Code.ipynb` |
| 9-Qubit Shor | 9 data + 8 ancilla | Both X and Z errors | `Phase2_Shor_Code.ipynb` |

## Noise Models

- **Bit-Flip Noise** — X error with probability *p*
- **Depolarizing Noise** — random X, Y, or Z error with total probability *p*
- **Amplitude Damping** — energy decay |1⟩ → |0⟩ with probability *gamma*

## Project Structure

```
├── Phase1_Noise_Simulation.ipynb      # Baseline: noise without correction
├── Phase2_BitFlip_Code.ipynb          # 3-qubit bit-flip code
├── Phase2_PhaseFlip_Code.ipynb        # 3-qubit phase-flip code
├── Phase2_Shor_Code.ipynb             # 9-qubit Shor code + final comparison
├── qec_presentation.tex               # LaTeX source for project presentation
├── results/                            # CSV data from all experiments
│   ├── noise_fidelity_results.csv
│   ├── physical_error_rate_results.csv
│   ├── bitflip_error_rates.csv
│   ├── bitflip_fidelity_results.csv
│   ├── phaseflip_error_rates.csv
│   ├── phaseflip_fidelity_results.csv
│   ├── shor_error_rates.csv
│   └── shor_fidelity_results.csv
└── plots/                              # Generated graphs
    ├── all_codes_comparison.png
    ├── bitflip_physical_vs_logical.png
    ├── shor_physical_vs_logical.png
    └── ...
```

## How to Run

### Prerequisites

```bash
pip install qiskit qiskit-aer numpy pandas matplotlib
```

### Execution Order

Run the notebooks in this order (each builds on the previous):

1. `Phase1_Noise_Simulation.ipynb` — generates baseline CSVs
2. `Phase2_BitFlip_Code.ipynb` — generates bit-flip results
3. `Phase2_PhaseFlip_Code.ipynb` — generates phase-flip results
4. `Phase2_Shor_Code.ipynb` — generates Shor results + loads previous CSVs for final comparison

> **Note:** The Shor code notebook takes ~3–4 hours to run due to 17-qubit circuit simulation with classical control flow.

## Key Results

- **Physical vs Logical Error Rate curves** for each code under each noise type
- **Pseudo-threshold estimates** — the breakeven noise level for each code
- **Post-correction fidelity** analysis
- **Scaling law comparison** — measured data vs base paper's predicted P_L ∝ P_p^((d+1)/2)
- **3-way comparison** of all codes under depolarizing noise

## Base Paper

V. S. Thakur, A. Kumar, K. Dev, "Quantum Error Correction in Green Communications: Toward Sustainable Quantum Networks," *IEEE Trans. Green Commun. Netw.*, vol. 9, no. 4, pp. 1566–1576, Dec. 2025.

## References

1. P. W. Shor, "Scheme for reducing decoherence in quantum computer memory," *Phys. Rev. A*, 1995.
2. A. M. Steane, "Error correcting codes in quantum theory," *Phys. Rev. Lett.*, 1996.
3. D. Gottesman, "Stabilizer codes and quantum error correction," Caltech Ph.D. Thesis, 1997.
4. J. Chiaverini et al., "Realization of quantum error correction," *Nature*, 2004.
5. M. D. Reed et al., "Realization of three-qubit QEC with superconducting circuits," *Nature*, 2012.
6. A. D. Corcoles et al., "Demonstration of a quantum error detection code," *Nat. Commun.*, 2015.
7. J. R. Wootton, "Benchmarking near-term devices with quantum error correction," *Quantum Sci. Technol.*, 2020.
8. Google Quantum AI, "Exponential suppression of bit or phase errors with cyclic error correction," *Nature*, 2021.
9. L. Postler et al., "Demonstration of fault-tolerant universal quantum gate operations," *Nature*, 2022.
10. A. Chatterjee & S. Ghosh, "Magic Mirror on the Wall, How to Benchmark QEC Codes, Overall?," *IEEE QCE*, 2024.

## Team

- Harish K (CB.AI.U4AID24118)
- Rajkumar R (CB.AI.U4AID24143)
- Suman Maitreya M (CB.AI.U4AID24156)
- GRS Kartheek (CB.AI.U4AID24116)

## License

This project is for academic purposes at Amrita Vishwa Vidyapeetham.
