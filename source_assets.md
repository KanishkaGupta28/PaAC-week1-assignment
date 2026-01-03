# Source Assets

This project is primarily implemented in a single Jupyter notebook, supported by structured data artifacts
and reference files. The following assets were used to generate datasets, perform tomography,
and validate reconstructed quantum states.

---

## Notebook

### PAAC_week1_assignment.ipynb

This notebook contains the complete end-to-end workflow of the project, including:

#### Dataset Generation
- Definition of reference quantum states (|0>, |1>, |+>, |->, and phase states)
- Construction of ideal density matrices for these states
- Generation of synthetic measurement data using Pauli X, Y, and Z measurements
- Saving measurement outcomes as NumPy `.npy` files along with metadata

#### Tomography
- Computation of expectation values from measurement samples
- Reconstruction of single-qubit density matrices using linear inversion
- Use of Pauli operator basis to reconstruct the quantum state

#### Validation
- Hermiticity checks of reconstructed density matrices
- Trace normalization checks (Tr(ρ) = 1)
- Positivity checks via eigenvalue computation
- Comparison against reference density matrices

#### Visualization
- Visualization of reconstructed density matrices
- Export of interactive HTML plots for inspection

---

## Data Artifacts

### qst_data/
- Contains `.npy` files storing synthetic measurement data
- Includes metadata JSON files describing the prepared quantum state

### data/
- Stores reconstructed density matrices and numerical results
- Includes fidelity or comparison metrics where applicable

### density_matrix_htmls/
- Interactive HTML visualizations of reconstructed density matrices

---

## Reference Assets

### reference_states.json
- Defines reference quantum states
- Stores ideal density matrices and preparation descriptions
- Used for validation and comparison against reconstructed states

---

## Scripts

All functionality is implemented inside the notebook for clarity and reproducibility.
The notebook logically separates dataset generation, tomography, and validation
through well-defined code cells.

---

## AI Usage Disclosure

AI assistance was used for conceptual clarification of quantum state tomography
and for improving code structure and documentation clarity.
All implementation logic was written, reviewed, and understood by the author.
