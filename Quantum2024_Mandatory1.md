---
header-includes:
- \usepackage{braket}
- \usepackage{graphicx}
---

# Coding part

Can be found in [notebook](./Quantum2024_MandatoryI_Coding.ipynb)

# Mandatory Tasks

## Quantum States and Quantum Gates 

### Express the state and show entanglement

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

### Apply a Hadamard layer and compute the new state in the standard basis

$$
\begin{aligned} \\
H \otimes H &= \frac{1}{\sqrt{2}}(\ket{0}\bra{0}+\ket{0}\bra{1}+\ket{1}\bra{0}-\ket{1}\bra{1}) \\
&\quad \otimes \frac{1}{\sqrt{2}}(\ket{0}\bra{0}+\ket{0}\bra{1}+\ket{1}\bra{0}-\ket{1}\bra{1}) \\
H \otimes H &= \frac{1}{2} \ket{00} \bra{00}+\ket{00} \bra{01}+\ket{00} \bra{10}+\ket{00} \bra{11} \\
&\quad +\ket{01}\bra{00}-\ket{01}\bra{01}+\ket{01}\bra{10}-\ket{01}\bra{11} \\
&\quad +\ket{10}\bra{00}+\ket{10}\bra{01}-\ket{10}\bra{10}-\ket{10}\bra{11} \\
&\quad +\ket{11}\bra{00}-\ket{11}\bra{01}-\ket{11}\bra{10}+\ket{11}\bra{11} \\
\end{aligned} \\
$$

$$
\begin{aligned}\\
\ket{\phi} &=\frac{1}{\sqrt{6}}(2\ket{00}-i(\ket{01} - \ket{10})) \\
(H \otimes H) \ket{\phi} &=\frac{1}{2} (\ket{00} \bra{00}\ket{\phi} \quad\to -i\ket{00}\\
&\quad + \ket{00}\bra{01}\ket{\phi}\quad \to i\ket{00}\\
&\quad + \ket{00}\bra{10}\ket{\phi}\quad \to i\ket{00}\\
&\quad + \ket{00}\bra{11}\ket{\phi}\quad \to 0\\
&\quad + \ket{01}\bra{00}\ket{\phi}\quad \to 2\ket{01}\\
&\quad - \ket{01}\bra{01}\ket{\phi}\quad \to i\ket{01}\\
&\quad + \ket{01}\bra{10}\ket{\phi}\quad \to i\ket{01}\\
&\quad - \ket{01}\bra{11}\ket{\phi}\quad \to 0\\
&\quad + \ket{10}\bra{00}\ket{\phi}\quad \to 2\ket{10}\\
&\quad + \ket{10}\bra{01}\ket{\phi}\quad \to -i\ket{10}\\
&\quad - \ket{10}\bra{10}\ket{\phi}\quad \to -i\ket{10}\\
&\quad - \ket{10}\bra{11}\ket{\phi}\quad \to 0\\
&\quad + \ket{11}\bra{00}\ket{\phi}\quad \to 2\ket{11}\\
&\quad - \ket{11}\bra{01}\ket{\phi}\quad \to i\ket{11}\\
&\quad - \ket{11}\bra{10}\ket{\phi}\quad \to -i\ket{11}\\
&\quad + \ket{11}\bra{11}\ket{\phi}\quad \to 0)\\
&= \frac{1}{2\sqrt{6}}(2\ket{00} + 2(1+i)\ket{01} + 2(1-i)\ket{10} + 2\ket{11}) \\
&= \frac{1}{\sqrt{6}}(\ket{00} + (1+i)\ket{01} + (1-i)\ket{10} + \ket{11})\\
\end{aligned}\\
$$

### CZ-gate, bottom qubit as control, compute new state in standard basis and X-basis

Let $CZ'$ be the $CZ$ gate with the bottom qubit as the control.


$$
\begin{aligned}\\
CZ' &= \ket0 \bra0 \otimes Z + \ket1 \bra1 \otimes I\\
&=\ket0\bra0 \otimes (\ket0\bra0 - \ket1\bra1) + \ket1\bra1 \otimes (\ket0\bra0 + \ket1\bra1)\\
&=\ket{00}\bra{00} - \ket{01}\bra{01} + \ket{10}\bra{10} + \ket{11}\bra{11}
\end{aligned}\\
$$

Computing in standard basis:

$$
\begin{aligned}\\
CZ' \ket{\phi} &= \ket{00}\bra{00}-\ket{01}\bra{01}+\ket{10}\bra{10}+\ket{11}\bra{11}\\
&\quad \cdot \frac{1}{\sqrt{6}}(\ket{00} + (1+i)\ket{01} + (1-i)\ket{10} + \ket{11})\\
&= \frac{1}{\sqrt{6}}(\ket{00} - (1+i)\ket{01} + (1-i)\ket{10} + \ket{11})
\end{aligned}\\
$$

Computing in X-basis:

$\ket0 = \frac{1}{\sqrt{2}}(\ket++\ket-)\\$
$\ket1 = \frac{1}{\sqrt{2}}(\ket+-\ket-)\\$


$\ket{00} = \frac{1}{2}(\ket{++}+\ket{+-}+\ket{-+}+\ket{--})\\$
$\ket{01} = \frac{1}{2}(\ket{++}-\ket{+-}+\ket{-+}-\ket{--})\\$
$\ket{10} = \frac{1}{2}(\ket{++}+\ket{+-}-\ket{-+}-\ket{--})\\$
$\ket{11} = \frac{1}{2}(\ket{++}-\ket{+-}-\ket{-+}+\ket{--})\\$


$$
\begin{aligned}\\
CZ' \ket{\phi} &= \frac{1}{2\sqrt{6}}(\ket{++}+\ket{+-}+\ket{-+}+\ket{--}\\
&\quad -(1+i) (\ket{++}-\ket{+-}+\ket{-+}-\ket{--})\\
&\quad +(1-i) (\ket{++}+\ket{+-}-\ket{-+}-\ket{--})\\
&\quad + \ket{++}-\ket{+-}-\ket{-+}+\ket{--})\\
&=\frac{1}{\sqrt{6}}((1-i)\ket{++} + \ket{+-} -\ket{-+} + (1+i)\ket{--})\\
\end{aligned}\\
$$



## Measurment Operators

### Task 1

### Task 2

### Task 3

### Task 4

### Task 5

### Task 6

### Task 7
