# Quantum State Tomography – Technical Report

## Overview
This project implements **single-qubit quantum state tomography** using measurement data obtained in the **Pauli basis**. The primary goal is to simulate measurement outcomes, reconstruct the corresponding quantum state (density matrix), and validate the results.  

The reconstruction process demonstrates how experimentally accessible measurements can be used to infer the underlying quantum state—an essential step in quantum computing calibration and verification.

## Dataset Generation
Synthetic measurement datasets are generated for known **reference states**:

- \( |0\rangle \) — ground state  
- \( |1\rangle \) — excited state  
- \( |+\rangle = (|0\rangle + |1\rangle)/\sqrt{2} \) — superposition along X  
- \( |-\rangle = (|0\rangle - |1\rangle)/\sqrt{2} \) — superposition along -X  

For each reference state, simulated measurement results are obtained in the **Pauli X, Y, and Z** bases. These are stored as **NumPy arrays** alongside metadata containing information about:

- The prepared state vector  
- The measurement basis  
- The number of shots or samples per basis  

This structured dataset provides reproducible input for tomography analysis.

## Measurement and Reconstruction
Quantum state tomography is performed using the expectation values of the Pauli operators.  
The **expectation values** \( \langle X \rangle, \langle Y \rangle, \langle Z \rangle \) are estimated directly from simulated measurement frequencies.

The **density matrix reconstruction** for a single qubit is carried out using the **linear inversion method**:

\[
\rho = \frac{1}{2}(I + \langle X \rangle X + \langle Y \rangle Y + \langle Z \rangle Z)
\]

where \( I \) is the identity operator and \( X, Y, Z \) are the Pauli matrices.  
This method assumes ideal, noise-free measurements and full knowledge of the measurement statistics.

## Validation Results
The reconstructed density matrices are validated against three primary physical constraints:

- **Hermiticity:** \( \rho = \rho^\dagger \)  
- **Trace normalization:** \( \mathrm{Tr}(\rho) = 1 \)  
- **Positivity:** All eigenvalues of \( \rho \ge 0 \)

Validation confirms that the reconstructed states are **physically consistent** and closely match the expected analytical density matrices for the test states.  
Quantitative comparisons (e.g., fidelity scores) indicate near-unity overlap for synthetic, noiseless data.

## Visualizations
Visual inspection is performed using **3D Bloch sphere plots** and **density matrix visualizations**.  
Interactive **HTML plots** are generated to represent:

- Real and imaginary parts of reconstructed matrices  
- Bloch vector representation of each state  

These visualizations provide intuitive insight into state reconstruction accuracy and any potential reconstruction bias.

## Limitations
While the current implementation accurately reconstructs single-qubit states under ideal conditions, several limitations remain:

- The approach assumes **perfect measurement statistics** without noise.  
- Only **single-qubit tomography** is supported (no multi-qubit extension yet).  
- Does not incorporate **maximum likelihood estimation (MLE)** for physically constrained reconstruction under experimental noise.  

Future improvements could include:
- Extending the framework to multi-qubit systems.  
- Incorporating noise modeling and MLE reconstruction.  
- Automating fidelity analysis and confidence estimation.

## Summary
This project successfully demonstrates single-qubit quantum state tomography through simulated measurement data. The workflow integrates dataset generation, reconstruction using Pauli expectations, and automated validation. The results confirm the theoretical predictions, establishing a foundation for extending these methods to experimental and multi-qubit systems.

---

# Reflection

## Tools Used
Python, NumPy, Matplotlib, Jupyter Notebook, and Qiskit were used for simulation and analysis.

## Open Questions
- How do measurement noise and finite sampling affect reconstruction accuracy?  
- How does SIC-POVM tomography compare quantitatively with Pauli-based tomography?  

## Planned Improvements
Future work includes extending the framework to multi-qubit states, implementing SIC-POVM measurements, and adding noise models.
