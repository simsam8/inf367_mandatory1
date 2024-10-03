---
numbersections: true
header-includes:
- \usepackage{braket}
- \usepackage{graphicx}
- \usepackage{qcircuit}
---

# Coding part

Can be found in __[notebook](./Quantum2024_MandatoryI_Coding.ipynb)__

# Manual Tasks

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



\newpage

## Measurement Operators

### Express the first part of the circuit as one unitary operator U


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

\newpage

### Compute the quantum state at the barrier and check for entanglement

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
&=\frac{1}{\sqrt2}\begin{bmatrix} 0\\0\\1\\0\\0\\-1\\0\\0\\ \end{bmatrix}
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


\newpage

### Define a measurement operator M. List eigenspaces, dimensionalities and measurement probabilities

Defining the measurement operator $M$:

$$
\newcommand{\f}[1]{\textbf{#1}}
\begin{aligned}
\ket{\psi} &= \frac{1}{\sqrt{2}}(\ket{\f{2}} - \ket{\f{5}})\\
U^\dag &=  (H \otimes Y \otimes I) \cdot (I \otimes (Swap \cdot CX \cdot Swap))\\
 &= \frac{i}{\sqrt{2}} (\ket{\f{2}}\bra{\f{0}} + \ket{\f{6}}\bra{\f{0}} - \ket{\f{1}}\bra{\f{1}} - \ket{\f{5}}\bra{\f{1}}\\
 &-\ket{\f{0}}\bra{\f{2}} - \ket{\f{4}}\bra{\f{2}} + \ket{\f{3}}\bra{\f{3}} + \ket{\f{7}}\bra{\f{3}}\\
 &+ \ket{\f{2}}\bra{\f{4}} - \ket{\f{6}}\bra{\f{4}} - \ket{\f{1}}\bra{\f{5}} + \ket{\f{5}}\bra{\f{5}}\\
 &-\ket{\f{0}}\bra{\f{6}} + \ket{\f{4}}\bra{\f{6}} + \ket{\f{3}}\bra{\f{7}} - \ket{\f{7}}\bra{\f{7}})\\
\end{aligned}
$$

Map the standard basis with $U^\dag$:

$$
\newcommand{\f}[1]{\textbf{#1}}
\begin{aligned}
U^\dag \ket{\f0} &= \frac{i}{\sqrt{2}}(\ket{\f2} + \ket{\f6}) = \frac{i}{\sqrt{2}}\ket{+10} = \ket{+10}\\
U^\dag \ket{\f1} &= \frac{i}{\sqrt{2}}(-\ket{\f1} - \ket{\f5}) = -\frac{i}{\sqrt{2}}\ket{+01} = \ket{+01}\\
U^\dag \ket{\f2} &= \frac{i}{\sqrt{2}}(-\ket{\f0} - \ket{\f4}) = -\frac{i}{\sqrt{2}}\ket{+00} = \ket{+00}\\
U^\dag \ket{\f3} &= \frac{i}{\sqrt{2}}(\ket{\f3} + \ket{\f7}) = \frac{i}{\sqrt{2}}\ket{+11} = \ket{+11}\\
U^\dag \ket{\f4} &= \frac{i}{\sqrt{2}}(\ket{\f2} - \ket{\f6}) = \frac{i}{\sqrt{2}}\ket{-10} = \ket{-10}\\
U^\dag \ket{\f5} &= \frac{i}{\sqrt{2}}(-\ket{\f1} + \ket{\f5}) = -\frac{i}{\sqrt{2}}\ket{-01} = \ket{-01}\\
U^\dag \ket{\f6} &= \frac{i}{\sqrt{2}}(-\ket{\f0} + \ket{\f4}) = -\frac{i}{\sqrt{2}}\ket{-00} = \ket{-00}\\
U^\dag \ket{\f7} &= \frac{i}{\sqrt{2}}(\ket{\f3} - \ket{\f7}) = \frac{i}{\sqrt{2}}\ket{-11} = \ket{-11}\\
M &= 1 \cdot \ket{+00}\bra{+00}\\
 &+1 \cdot \ket{+01}\bra{+01}\\
 &+2 \cdot \ket{+10}\bra{+10}\\
 &+2 \cdot \ket{+11}\bra{+11}\\
 &+3 \cdot \ket{-00}\bra{-00}\\
 &+3 \cdot \ket{-01}\bra{-01}\\
 &+4 \cdot \ket{-10}\bra{-10}\\
 &+4 \cdot \ket{-11}\bra{-11}\\
\end{aligned}
$$


Eigenspaces:

$$
\newcommand{\f}[1]{\textbf{#1}}
\begin{array}{rrr}
Eigenvalue & Eigenspace & Dim \\
\hline \lambda_1 = 1 & \{\ket{+00}, \ket{+01}\} & 2 \\
 \lambda_2 = 2 & \{\ket{+10}, \ket{+11}\} & 2 \\
 \lambda_3 = 3 & \{\ket{-00}, \ket{-01}\} & 2 \\
 \lambda_4 = 4 & \{\ket{-10}, \ket{-11}\} & 2 \\
\end{array}
$$

Measurement probabilities:

$$
\newcommand{\f}[1]{\textbf{#1}}
\begin{aligned}
\ket{\psi} &= \frac{1}{\sqrt{2}}(\ket{\f{2}} - \ket{\f{5}})\\
\ket{\psi} &= \frac{1}{\sqrt{2}}(\ket{010} - \ket{101}) = \frac{1}{2}(\ket{+10}+\ket{-10} + \ket{-01}-\ket{+01})\\
P_m[\ket{\psi} \to 1] &= | \braket{+00|{\psi}} |^2 + | \braket{+01|{\psi}} |^2= |-\frac{1}{2}\braket{+01|+01}|^2 = \frac{1}{4}\\
P_m[\ket{\psi} \to 2] &= | \braket{+10|{\psi}} |^2 + | \braket{+11|{\psi}} |^2= |\frac{1}{2}\braket{+10|+10}|^2 = \frac{1}{4} \\
P_m[\ket{\psi} \to 3] &= | \braket{-00|{\psi}} |^2 + | \braket{-01|{\psi}} |^2= |\frac{1}{2}\braket{-01|-01})|^2 = \frac{1}{4}\\
P_m[\ket{\psi} \to 4] &= | \braket{-10|{\psi}} |^2 + | \braket{-11|{\psi}} |^2= |\frac{1}{2}\braket{-10|-10})|^2 = \frac{1}{4}\\
\end{aligned}
$$


\newpage

### Compute the expectation value and the posterior states

Expectation value:

$$
\newcommand{\f}[1]{\textbf{#1}}
\begin{aligned}
\braket{M_{\psi}} &= 1\cdot\frac{1}{4}+2\cdot\frac{1}{4}+3\cdot\frac{1}{4}+4\cdot\frac{1}{4}\\
&=\frac{10}{4}=2.5
\end{aligned}
$$

Posterior states:

$\ket{\psi} = \frac{1}{2}(\ket{+10}+\ket{-10} + \ket{-01}-\ket{+01})$

for $\lambda_1$:

$$
\begin{aligned}
\pi_{1} &= \ket{+00}\bra{+00} + \ket{+01}\bra{+01}\\ 
\ket{\phi}_{\lambda_1} &= \frac{\pi_1\ket{\psi}}{||\pi_1 \ket{\psi}||}\\
&=\frac{-\frac{1}{2}\ket{+01}}{||-\frac{1}{2}\ket{+01}||} = \frac{-\frac{1}{2}\ket{+01}}{\frac{1}{2}}\\
&=\ket{+01}\\
\end{aligned}
$$

for $\lambda_2$:

$$
\begin{aligned}
\pi_{2} &= \ket{+10}\bra{+10} + \ket{+11}\bra{+11}\\ 
\ket{\phi}_{\lambda_2} &= \frac{\pi_2\ket{\psi}}{||\pi_2 \ket{\psi}||}\\
&=\frac{\frac{1}{2}\ket{+10}}{||\frac{1}{2}\ket{+10}||} = \frac{\frac{1}{2}\ket{+10}}{\frac{1}{2}}\\
&=\ket{+10}\\
\end{aligned}
$$

for $\lambda_3$:

$$
\begin{aligned}
\pi_{3} &= \ket{-00}\bra{-00} + \ket{-01}\bra{-01}\\ 
\ket{\phi}_{\lambda_3} &= \frac{\pi_3\ket{\psi}}{||\pi_3 \ket{\psi}||}\\
&=\frac{\frac{1}{2}\ket{-01}}{||\frac{1}{2}\ket{-01}||} = \frac{\frac{1}{2}\ket{-01}}{\frac{1}{2}}\\
&=\ket{-01}\\
\end{aligned}
$$

for $\lambda_4$:

$$
\begin{aligned}
\pi_{4} &= \ket{-10}\bra{-10} + \ket{-11}\bra{-11}\\ 
\ket{\phi}_{\lambda_4} &= \frac{\pi_4\ket{\psi}}{||\pi_4 \ket{\psi}||}\\
&=\frac{\frac{1}{2}\ket{-10}}{||\frac{1}{2}\ket{-10}||} = \frac{\frac{1}{2}\ket{-10}}{\frac{1}{2}}\\
&=\ket{-10}\\
\end{aligned}
$$

\newpage

### Use the measurement operator $\hat{M}$. List eigenspaces, dimensionalities and measurement probabilities

Eigenstate:

$$
\begin{array}{rrr}
Eigenvalue & Eigenspace & Dimension \\
\hline \lambda_1 = 1 & \{(\ket{L\Phi^+} , \ket{R\Phi^+})  \} & 2 \\
 \lambda_2 = 2 &  \{(\ket{L\Phi^-} , \ket{R\Phi^-})  \} & 2 \\
 \lambda_3 = 3 &  \{(\ket{L\Psi^+} , \ket{R\Psi^+})  \} & 2 \\
 \lambda_4 = 4 &  \{(\ket{L\Psi^-} , \ket{R\Psi^-})  \} & 2 \\
\end{array}
$$

$$
\begin{aligned}
\ket{\psi} &=\frac{1}{\sqrt{2}}(\ket{010} - \ket{101})=\ket{\textbf2}-\ket{\textbf5}\\
\ket{L\Phi^+} &= \frac{1}{2}\begin{bmatrix} 1\\\\\\1\\-i\\\\\\-i \end{bmatrix},
\ket{R\Phi^+} =\frac{1}{{2}}\begin{bmatrix} 1\\\\\\1\\i\\\\\\i \end{bmatrix},
\ket{L\Phi^-} =\frac{1}{{2}}\begin{bmatrix} 1\\\\\\-1\\-i\\\\\\i \end{bmatrix},
\ket{R\Phi^-} =\frac{1}{{2}}\begin{bmatrix} 1\\\\\\-1\\i\\\\\\-i \end{bmatrix},\\
\ket{L\Psi^+} &=\frac{1}{{2}}\begin{bmatrix} \\1\\1\\\\\\-i\\-i\\\\ \end{bmatrix},
\ket{R\Psi^-} =\frac{1}{{2}}\begin{bmatrix} \\1\\1\\\\\\i\\i\\\\ \end{bmatrix},
\ket{L\Psi^-} =\frac{1}{{2}}\begin{bmatrix} \\1\\-1\\\\\\-i\\i\\\\ \end{bmatrix},
\ket{R\Psi^-} =\frac{1}{2}\begin{bmatrix} \\1\\-1\\\\\\i\\-i\\\\ \end{bmatrix}
\end{aligned}
$$


$$
\newcommand{\f}[1]{\textbf{#1}}
\begin{aligned}
M &= 1\cdot(\ket{\f{0}}\bra{\f{0}}+\ket{\f{3}}\bra{\f{0}}+\ket{\f{0}}\bra{\f{3}}+\ket{\f{3}}\bra{\f{3}}+\ket{\f{4}}\bra{\f{4}}+\ket{\f{4}}\bra{\f{7}}+\ket{\f{7}}\bra{\f{4}}+\ket{\f{7}}\bra{\f{7}})\\
&+ 2\cdot(\ket{\f{0}}\bra{\f{0}}-\ket{\f{3}}\bra{\f{0}}-\ket{\f{0}}\bra{\f{3}}+\ket{\f{3}}\bra{\f{3}}+\ket{\f{4}}\bra{\f{4}}-\ket{\f{4}}\bra{\f{7}}-\ket{\f{7}}\bra{\f{4}}+\ket{\f{7}}\bra{\f{7}})\\
&+ 3\cdot(\ket{\f{1}}\bra{\f{1}}+\ket{\f{1}}\bra{\f{2}}+\ket{\f{2}}\bra{\f{1}}+\ket{\f{2}}\bra{\f{2}}+\ket{\f{5}}\bra{\f{5}}+\ket{\f{5}}\bra{\f{6}}+\ket{\f{6}}\bra{\f{5}}+\ket{\f{6}}\bra{\f{6}})\\
&+ 4\cdot(\ket{\f{1}}\bra{\f{1}}-\ket{\f{1}}\bra{\f{2}}-\ket{\f{2}}\bra{\f{1}}+\ket{\f{2}}\bra{\f{2}}+\ket{\f{5}}\bra{\f{5}}-\ket{\f{5}}\bra{\f{6}}-\ket{\f{6}}\bra{\f{5}}+\ket{\f{6}}\bra{\f{6}})
\end{aligned}
$$

Measurement probabilities:

$$
\begin{aligned}
P_m[\ket{\psi} \to 1] &= | \braket{\textbf0|{\psi}} |^2 + | \braket{\textbf3|{\psi}} |^2 + | -i \braket{\textbf4|{\psi}} |^2 + |-i \braket{\textbf7|{\psi}} |^2\\
&+ | \braket{\textbf0|{\psi}} |^2 + | \braket{\textbf3|{\psi}} |^2 + | i \braket{\textbf4|{\psi}} |^2 + | i \braket{\textbf7|{\psi}} |^2\\
&= 0 + 0 + 0 + 0 + 0 + 0 + 0 + 0\\
&= 0\\
P_m[\ket{\psi} \to 2] &= | \braket{\textbf0|{\psi}} |^2 + |- \braket{\textbf3|{\psi}} |^2 + |-i \braket{\textbf4|{\psi}} |^2 + |i \braket{\textbf7|{\psi}} |^2\\
&+ | \braket{\textbf0|{\psi}} |^2 + |- \braket{\textbf3|{\psi}} |^2 + |i \braket{\textbf4|{\psi}} |^2 + |-i \braket{\textbf7|{\psi}} |^2\\
&= 0 + 0 + 0 + 0 + 0 + 0 + 0 + 0\\
&= 0\\
P_m[\ket{\psi} \to 3] &= | \braket{\textbf1|{\psi}} |^2 + | \braket{\textbf2|{\psi}} |^2 + |-i \braket{\textbf5|{\psi}} |^2 + |-i \braket{\textbf6|{\psi}} |^2\\
&+ | \braket{\textbf1|{\psi}} |^2 + | \braket{\textbf2|{\psi}} |^2 + |i \braket{\textbf5|{\psi}} |^2 + |i \braket{\textbf6|{\psi}} |^2\\
&=  0 + | \frac{1}{\sqrt{2}\sqrt{2}\sqrt{2}} (\braket{\textbf2|\textbf2} - \braket{\textbf2|\textbf5}) |^2 + | \frac{-i}{\sqrt{2}\sqrt{2}\sqrt{2}} (\braket{\textbf5|\textbf2} - \braket{\textbf5|\textbf5}) |^2 + 0\\
&+  0 + | \frac{1}{\sqrt{2}\sqrt{2}\sqrt{2}} (\braket{\textbf2|\textbf2} - \braket{\textbf2|\textbf5}) |^2 + | \frac{i}{\sqrt{2}\sqrt{2}\sqrt{2}} (\braket{\textbf5|\textbf2} - \braket{\textbf5|\textbf5}) |^2 + 0\\
&= \frac{1}{8} + \frac{1}{8} + \frac{1}{8} + \frac{1}{8}\\
&= \frac{1}{2}\\
P_m[\ket{\psi} \to 4] &= | \braket{\textbf1|{\psi}} |^2 + |- \braket{\textbf2|{\psi}} |^2 + |-i \braket{\textbf5|{\psi}} |^2 + | \braket{\textbf6|{\psi}} |^2\\
&+ | \braket{\textbf1|{\psi}} |^2 + |- \braket{\textbf2|{\psi}} |^2 +  |i \braket{\textbf5|{\psi}} |^2 + |-i \braket{\textbf6|{\psi}} |^2\\
&=  0 + | \frac{-1}{\sqrt{2}\sqrt{2}\sqrt{2}} (\braket{\textbf2|\textbf2} - \braket{\textbf2|\textbf5}) |^2 + | \frac{-i}{\sqrt{2}\sqrt{2}\sqrt{2}} (\braket{\textbf5|\textbf2} - \braket{\textbf5|\textbf5}) |^2 + 0\\
&+  0 + | \frac{-1}{\sqrt{2}\sqrt{2}\sqrt{2}} (\braket{\textbf2|\textbf2} - \braket{\textbf2|\textbf5}) |^2 + | \frac{i}{\sqrt{2}\sqrt{2}\sqrt{2}} (\braket{\textbf5|\textbf2} - \braket{\textbf5|\textbf5}) |^2 + 0\\
&= \frac{1}{8} + \frac{1}{8} + \frac{1}{8} + \frac{1}{8}\\
&= \frac{1}{2}\\
\end{aligned}
$$

\newpage

### Compute the expectation value and the posterior states

Expectation value:
$\braket{M}_\psi=0\cdot1+0\cdot2+\frac{1}{2}\cdot3+\frac{1}{2}\cdot4=7/2=3.5$

Posterior states:
$$
\begin{aligned}
\pi_3  &= \ket{\textbf1} \bra{\textbf1}+\ket{\textbf2} \bra{\textbf2}+i\ket{\textbf5} \bra{\textbf5}+i\ket{\textbf6} \bra{\textbf6}+\ket{\textbf1} \bra{\textbf1}+\ket{\textbf2} \bra{\textbf2}-i\ket{\textbf5} \bra{\textbf5}-i\ket{\textbf6} \bra{\textbf6}\\
\pi_4 &= \ket{\textbf1} \bra{\textbf1}-\ket{\textbf2} \bra{\textbf2}-i\ket{\textbf5} \bra{\textbf5}+i\ket{\textbf6} \bra{\textbf6}+\ket{\textbf1} \bra{\textbf1}-\ket{\textbf2} \bra{\textbf2}+i\ket{\textbf5} \bra{\textbf5}-i\ket{\textbf6} \bra{\textbf6}\\
\pi_3 &: \ket{\psi}= \frac{1}{{\sqrt{8}}} (\ket{\textbf2}+ \ket{\textbf2} +i\ket{\textbf5}-i\ket{\textbf5})\\
\pi_4 &:\ket{\psi} = \frac{1}{{\sqrt{8}}} (-\ket{\textbf2}-\ket{\textbf2} +i\ket{\textbf5}-i\ket{\textbf5})\\
\ket{\psi} &\to \frac{\pi_3\ket{\psi}}{||\pi_3\ket{\psi}||}=\frac{\frac{1}{{\sqrt{8}}} (\ket{\textbf2} + \ket{\textbf2} +i\ket{\textbf5}-i\ket{\textbf5})}{\frac{\sqrt{4}}{\sqrt{8}}}=\frac{(\ket{\textbf2} + \ket{\textbf2} +i\ket{\textbf5}-i\ket{\textbf5})}{\sqrt{4}}=\frac{(2\cdot\ket{\textbf2})}{\sqrt{4}}=\ket{0}\otimes\ket{1}\otimes\ket{0}\\
\ket{\psi} &\to \frac{\pi_4\ket{\psi}}{||\pi_4\ket{\psi}||}=\frac{\frac{1}{{\sqrt{8}}} (-\ket{\textbf2}-\ket{\textbf2}+i\ket{\textbf5}-i\ket{\textbf5})}{\frac{\sqrt{4}}{\sqrt{8}}}\\
&=\frac{(-\ket{\textbf2} - \ket{\textbf2} +i\ket{\textbf5}-i\ket{\textbf5})}{\sqrt{4}}=\frac{(-2\cdot\ket{\textbf2})}{\sqrt{4}}=-(\ket{0}\otimes\ket{1}\otimes\ket{0})\\
\end{aligned}
$$

### Realization of $\hat{M}$ on a quantum computer with only (partial) standard measurements

To realize $\hat{M}$ on a quantum computer with only (partial) standard measurements,
we need a unitary operator $U$ that maps the eigenspaces of $\hat{M}$ onto 
the standard basis.

$Eig(\hat{M}, \lambda_k) \overset{U}{\mapsto} Eig(M_{std}, \lambda_k)$

After measuring and calculating the posterior states in $M_{std}$, 
we then revert back by $U^{\dagger}$.

$$
\Qcircuit @C=1em @R=.7em {
    & \multigate{1}{U} & \meter & \multigate{1}{U^\dag} & \qwa\\
    & \ghost{U} & \qw & \ghost{U^\dag} & \qwa
}
$$
