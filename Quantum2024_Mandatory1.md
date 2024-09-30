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



## Measurement Operators

\newpage

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

\newpage

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

### Task 3

Defining the measurement operator $M$:

$$
\newcommand{\f}[1]{\textbf{#1}}
\begin{aligned}
\ket{\psi} &= \frac{1}{\sqrt{2}}(\ket{\f{2}} - \ket{\f{5}})\\
U &= I \otimes (Swap \cdot CX \cdot Swap) \cdot (H \otimes Y \otimes I)\\
 &= \frac{1}{\sqrt{2}} (\ket{\f{2}}\bra{\f{0}} + \ket{\f{6}}\bra{\f{0}} + \ket{\f{1}}\bra{\f{1}} + \ket{\f{5}}\bra{\f{1}}\\
 &= -\ket{\f{0}}\bra{\f{2}} - \ket{\f{4}}\bra{\f{2}} - \ket{\f{3}}\bra{\f{3}} - \ket{\f{7}}\bra{\f{3}}\\
 &= \ket{\f{2}}\bra{\f{4}} - \ket{\f{6}}\bra{\f{4}} + \ket{\f{1}}\bra{\f{5}} - \ket{\f{5}}\bra{\f{5}}\\
 &= -\ket{\f{0}}\bra{\f{6}} + \ket{\f{4}}\bra{\f{6}} - \ket{\f{3}}\bra{\f{7}} + \ket{\f{7}}\bra{\f{7}})\\
U\ket{\psi} &= \frac{1}{2}(-\ket{\f0}+\ket{\f1}-\ket{\f4}-\ket{\f5})\\
M &= 1 \cdot \ket{\f0}\bra{\f0}\\
 &+2 \cdot \ket{\f1}\bra{\f1}\\
 &+3 \cdot \ket{\f2}\bra{\f2}\\
 &+4 \cdot \ket{\f3}\bra{\f3}\\
 &+5 \cdot \ket{\f4}\bra{\f4}\\
 &+6 \cdot \ket{\f5}\bra{\f5}\\
 &+7 \cdot \ket{\f6}\bra{\f6}\\
 &+8 \cdot \ket{\f7}\bra{\f7}\\
\end{aligned}
$$


Eigenspaces:

$$
\newcommand{\f}[1]{\textbf{#1}}
\begin{array}{rrr}
Eigenvalue & Eigenspace & Dim \\
\hline \lambda_1 = 1 & \{\ket{\f0}\} & 1 \\
\lambda_2= 2 & \{\ket{\f1}\} & 1 \\
\lambda_3 = 3 & \{\ket{\f2}\} & 1 \\
\lambda_4 = 4 & \{\ket{\f3}\} & 1 \\
\lambda_5 = 5 & \{\ket{\f4}\} & 1 \\
\lambda_6 = 6 & \{\ket{\f5}\} & 1 \\
\lambda_7 = 7 & \{\ket{\f6}\} & 1 \\
\lambda_8 = 8 & \{\ket{\f7}\} & 1 \\
\end{array}
$$

Measurement probabilities:

$$
\newcommand{\f}[1]{\textbf{#1}}
\begin{aligned}
P_m[\ket{\psi} \to 1] &= | \braket{\f0|{\psi}} |^2 = | \frac{1}{\sqrt{2}} (\braket{\f0|\f2} - \braket{\f0|\f5})|^2 = 0\\
P_m[\ket{\psi} \to 2] &= | \braket{\f1|{\psi}} |^2 = | \frac{1}{\sqrt{2}} (\braket{\f1|\f2} - \braket{\f1|\f5})|^2 = 0\\
P_m[\ket{\psi} \to 3] &= | \braket{\f2|{\psi}} |^2 = | \frac{1}{\sqrt{2}} (\braket{\f2|\f2} - \braket{\f2|\f5})|^2 = \frac{1}{2}\\
P_m[\ket{\psi} \to 4] &= | \braket{\f3|{\psi}} |^2 = | \frac{1}{\sqrt{2}} (\braket{\f3|\f2} - \braket{\f3|\f5})|^2 = 0\\
P_m[\ket{\psi} \to 5] &= | \braket{\f4|{\psi}} |^2 = | \frac{1}{\sqrt{2}} (\braket{\f4|\f2} - \braket{\f4|\f5})|^2 = 0\\
P_m[\ket{\psi} \to 6] &= | \braket{\f5|{\psi}} |^2 = | \frac{1}{\sqrt{2}} (\braket{\f5|\f2} - \braket{\f5|\f5})|^2 = \frac{1}{2}\\
P_m[\ket{\psi} \to 7] &= | \braket{\f6|{\psi}} |^2 = | \frac{1}{\sqrt{2}} (\braket{\f6|\f2} - \braket{\f6|\f5})|^2 = 0\\
P_m[\ket{\psi} \to 8] &= | \braket{\f7|{\psi}} |^2 = | \frac{1}{\sqrt{2}} (\braket{\f7|\f2} - \braket{\f7|\f5})|^2 = 0\\
\end{aligned}
$$


\newpage

### Task 4

Expectation value:

$$
\newcommand{\f}[1]{\textbf{#1}}
\begin{aligned}
\braket{M_{\psi}} &= \braket{\psi|M|\psi}\\
&= \frac{1}{\sqrt{2}}(\bra{\f2} - \bra{\f5}
)\\
&\cdot (1 \cdot \ket{\f0}\bra{\f0} +2 \cdot \ket{\f1}\bra{\f1} +3 \cdot \ket{\f2}\bra{\f2} +4 \cdot \ket{\f3}\bra{\f3}\\
 &+5 \cdot \ket{\f4}\bra{\f4} +6 \cdot \ket{\f5}\bra{\f5} +7 \cdot \ket{\f6}\bra{\f6} +8 \cdot \ket{\f7}\bra{\f7})\\
&\cdot \frac{1}{\sqrt{2}}(\ket{\f2} - \ket{\f5})\\
&=\frac{1}{2}(3\bra{\f2}-6\bra{\f5}) \cdot (\ket{\f2}-\ket{\f5})\\
&=\frac{1}{2}(3+6) = 9/2 = 4.5
\end{aligned}
$$


Posterior states

for $\lambda_3$:

$$
\newcommand{\f}[1]{\textbf{#1}}
\begin{aligned}
\frac{\ket{\f2}\braket{\f{2}|\psi}}{||\ket{\f2}\braket{\f{2}|\psi}||} &= 
\frac{\frac{1}{\sqrt{2}}(\ket{\f2}\braket{\f{2}|\f2}-\ket{\f2}\braket{\f{2}|\f5})}
{||\frac{1}{\sqrt{2}}(\ket{\f2}\braket{\f{2}|\f2}-\ket{\f2}\braket{\f{2}|\f5})||}\\
&= \frac{\frac{1}{\sqrt{2}}\ket{\f2}}{||\frac{1}{\sqrt{2}}\ket{\f2}||} =
\frac{\frac{1}{\sqrt{2}}\ket{\f2}}{\frac{1}{\sqrt{2}}} = \ket{\f2}
\end{aligned}
$$

for $\lambda_6$:

$$
\newcommand{\f}[1]{\textbf{#1}}
\begin{aligned}
\frac{\ket{\f5}\braket{\f{5}|\psi}}{||\ket{\f5}\braket{\f{5}|\psi}||} &= 
\frac{\frac{1}{\sqrt{2}}(\ket{\f5}\braket{\f{5}|\f2}-\ket{\f5}\braket{\f{5}|\f5})}
{||\frac{1}{\sqrt{2}}(\ket{\f5}\braket{\f{5}|\f2}-\ket{\f5}\braket{\f{5}|\f5})||}\\
&= \frac{-\frac{1}{\sqrt{2}}\ket{\f5}}{||-\frac{1}{\sqrt{2}}\ket{\f5}||} =
\frac{-\frac{1}{\sqrt{2}}\ket{\f5}}{\frac{1}{\sqrt{2}}} = -\ket{\f5} = \ket{\f5}
\end{aligned}
$$

### Task 5

### Task 6

### Task 7
