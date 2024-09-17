---
header-includes:
- \usepackage{braket}
---

# Coding part

Can be found in [notebook](./Quantum2024_MandatoryI_Coding.ipynb)

# Mandatory Tasks

## Quantum States and Quantum Gates 

### Task 1


Rewrite $\ket{\phi}$ in the standard basis:

$$
\begin{aligned} \\
\ket{\phi} &= \frac{1}{\sqrt{3}}(\ket{\phi^+} + \ket{\phi^-} -i \ket{\psi^-}) \\
            &= \frac{1}{\sqrt{3}}(\frac{1}{\sqrt{2}}(\ket{00} + \ket{11}) + \frac{1}{\sqrt{2}}(\ket{00} - \ket{11}) -\frac{i}{\sqrt{2}}(\ket{01} - \ket{10})) \\
            &= \frac{1}{\sqrt{3}}(\frac{2}{\sqrt{2}}\ket{00}-\frac{i}{\sqrt{2}}(\ket{01} - \ket{10})) \\
            &= \frac{1}{\sqrt{6}}(2\ket{00}-i(\ket{01} - \ket{10})) \\
\end{aligned} \\
$$

Show that it is entangled:

$$
\begin{aligned} \\
\ket{\phi} &= \alpha \gamma \ket{00} + \alpha \delta \ket{01} + \beta \gamma \ket{10} + \beta \delta \ket{11} \\
\frac{2}{\sqrt{6}} \ket{00} - \frac{i}{\sqrt{6}} \ket{01} + \frac{i}{\sqrt{6}} \ket{10} + 0 \ket{11} &\neq 
\alpha \gamma \ket{00} + \alpha \delta \ket{01} + \beta \gamma \ket{10} + \beta \delta \ket{11}
\end{aligned} \\
$$

Either $\beta$ or $\delta$ needs to be zero, but that contradicts the other terms. Thus $\ket{\phi}$ is entangeled.

### Task 2

### Task 3


## Measurment Operators

### Task 1

### Task 2

### Task 3

### Task 4

### Task 5

### Task 6

### Task 7
