# Measurement Theory Notes

## Born Rule

In quantum mechanics, the **Born rule** provides the link between the mathematical
description of a quantum state and the probabilities of measurement outcomes.

For a quantum state described by a density matrix $\rho$ and a measurement
operator $E_i$, the probability of obtaining outcome $i$ is given by:

$$
p(i) = \mathrm{Tr}(\rho E_i)
$$

where:  
- $\rho$ is the density matrix representing the quantum state  
- $E_i$ is the positive operator corresponding to measurement outcome $i$  
- $\mathrm{Tr}(\cdot)$ denotes the trace operation  

This rule forms the statistical foundation of quantum measurement theory.

---

## Pauli Measurement Operators

For **single-qubit quantum state tomography**, measurements are performed in the
Pauli bases $X$, $Y$, and $Z$. The Pauli matrices are defined as:

$$
X =
\begin{pmatrix}
0 & 1 \\
1 & 0
\end{pmatrix}, \quad
Y =
\begin{pmatrix}
0 & -i \\
i & 0
\end{pmatrix}, \quad
Z =
\begin{pmatrix}
1 & 0 \\
0 & -1
\end{pmatrix}
$$

Measurements in these bases are sufficient for reconstructing any single-qubit
density matrix because the Pauli operators form a complete basis for the space
of $2 \times 2$ Hermitian operators.

---

## SIC-POVM vs. Pauli Measurements

A **SIC-POVM (Symmetric Informationally Complete Positive Operator-Valued Measure)**
consists of four measurement operators that are symmetrically distributed on the
Bloch sphere. These operators satisfy the condition:

$$
\mathrm{Tr}(E_i E_j) = \frac{1}{3}, \quad i \neq j
$$

### Comparison

| Property | SIC-POVM | Pauli Measurements |
|--------|----------|-------------------|
| Number of outcomes | 4 | 3 measurement bases |
| Informational completeness | Yes | Yes |
| Measurement efficiency | High (minimal redundancy) | Lower |
| Experimental simplicity | Complex | Simple |


SIC-POVMs are often favored in theoretical studies due to their efficiency,
while Pauli measurements are easier to implement and interpret, making them
suitable for this project.

---

## Operator Definitions

- **Measurement operator $E_i$:** A positive semi-definite operator
  associated with a measurement outcome  
- **POVM:** A set of operators $\{E_i\}$ satisfying
  $\sum_i E_i = I$, where $I$ is the identity operator  
- **Projective measurement:** A special case of POVM where each operator is an
  orthogonal projector satisfying $E_i^2 = E_i$

---

## Validation Checks

After reconstructing a density matrix $\rho$, the following physical
consistency checks are applied:

- **Hermiticity:** $\rho = \rho^\dagger$  
  Ensures observable quantities are real-valued  
- **Trace normalization:** $\mathrm{Tr}(\rho) = 1$  
  Ensures total probability is conserved  
- **Positivity:** All eigenvalues of $\rho \ge 0$  
  Confirms the state is physically realizable  

If all conditions are satisfied, the reconstructed density matrix represents a
valid quantum state.

