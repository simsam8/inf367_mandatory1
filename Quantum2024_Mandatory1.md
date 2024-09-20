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

$\ket0 = \frac{1}{\sqrt{2}}(\ket++\ket-)$

$\ket1 = \frac{1}{\sqrt{2}}(\ket+-\ket-)$

$\ket{00} = \frac{1}{2}(\ket{++}+\ket{+-}+\ket{-+}+\ket{--})$

$\ket{01} = \frac{1}{2}(\ket{++}-\ket{+-}+\ket{-+}-\ket{--})$

$\ket{10} = \frac{1}{2}(\ket{++}+\ket{+-}-\ket{-+}-\ket{--})$

$\ket{11} = \frac{1}{2}(\ket{++}-\ket{+-}-\ket{-+}+\ket{--})$


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


$$
\begin{aligned}\\
U &= (CX \otimes Z) \cdot C(I\otimes X) \cdot (H \otimes X \otimes I)\\
U &= \qquad\left[\begin{array}{c c|c c|c c|c c}
    1&&&&&&&\\ 
    &-1&&&&&&\\ 
    \hline 
    &&1&&&&&\\ 
    &&&-1&&&&\\ 
    \hline 
    &&&&&&1&\\ 
    &&&&&&&-1\\ 
    \hline 
    &&&&1&&&\\ 
    &&&&&-1&&\\ 
\end{array}\right]\\
&\cdot\;\;\quad\quad
\left[\begin{array}{c c|c c|c c|c c} 
    1&&&&&&&\\ 
    &1&&&&&&\\ 
    \hline 
    &&1&&&&&\\ 
    &&&1&&&&\\ 
    \hline 
    &&&&&1&&\\ 
    &&&&1&&&\\ 
    \hline 
    &&&&&&&1\\ 
    &&&&&&1&\\ 
\end{array}\right]\\
&\cdot
\frac{1}{\sqrt2}\left[\begin{array}{c c|c c|c c|c c} 
    &&1&&&&1&\\ 
    &&&1&&&&1\\ 
    \hline 
    1&&&&1&&&\\ 
    &1&&&&1&&\\ 
    \hline 
    &&1&&&&-1&\\ 
    &&&1&&&&-1\\ 
    \hline 
    1&&&&-1&&&\\ 
    &1&&&&-1&&\\ 
\end{array}\right]\\
&=\frac{1}{\sqrt2}
\left[\begin{array}{c c|c c|c c|c c} 
    &&1&&&&1&\\ 
    &&&-1&&&&-1\\ 
    \hline 
    1&&&&1&&&\\ 
    &-1&&&&-1&&\\ 
    \hline 
    &1&&&&-1&&\\ 
    -1&&&&1&&&\\ 
    \hline 
    &&&1&&&&-1\\ 
    &&-1&&&&1&\\ 
\end{array}\right]\\
\end{aligned}\\
$$

### Task 2

$$
\begin{aligned}\\
U\ket{000} &= \frac{1}{\sqrt2}
\left[\begin{array}{c c|c c|c c|c c} 
    &&1&&&&1&\\ 
    &&&-1&&&&-1\\ 
    \hline 
    1&&&&1&&&\\ 
    &-1&&&&-1&&\\ 
    \hline 
    &1&&&&-1&&\\ 
    -1&&&&1&&&\\ 
    \hline 
    &&&1&&&&-1\\ 
    &&-1&&&&1&\\ 
\end{array}\right]
\cdot
\begin{bmatrix} 1\\\\\\\\\\\\\\\\ \end{bmatrix}\\
&=\frac{1}{\sqrt2}\begin{bmatrix} \\\\ 1\\\\\\ -1\\\\\\ \end{bmatrix}
=\frac{1}{\sqrt{2}}(\ket{010} - \ket{101})
\end{aligned}\\
$$

We can write a statevector with 3 qubits like this:

$\ket{\phi} = (a_1\ket0 + b_1\ket1) \otimes (a_2\ket0 + b_2\ket1) \otimes (a_3\ket0 + b_3\ket1)$

For the state $\ket{\phi}$ these are the coefficients.
The state is entangeled as none of the $a$'s and $b$'s 
can be $0$, but most products are $0$, thus there is a contradiction 
and the state is entangeled.

$$
\begin{cases}
    a_1 a_2 a_3 = 0 \\ 
    a_1 a_2 b_3 = 0 \\
    a_1 b_2 a_3 = \frac{1}{\sqrt{2}} \\
    a_1 b_2 b_3 = 0 \\
    b_1 a_2 a_3 = 0 \\
    b_1 a_2 b_3 = -\frac{1}{\sqrt{2}} \\
    b_1 b_2 a_3 = 0 \\
    b_1 b_2 b_3 = 0 \\
\end{cases}
$$


### Task 3

### Task 4

### Task 5

### Task 6

### Task 7
