---
type: "[[Lectures]]"
course: "[[Introduction to Digital Circuits]]"
date: 2026-11-26
week: "8"
---

# 2026-11-26 - Matrix Normal Forms, Encoder, Decoder and Multiplexer

## Main Idea

The lecture continued with **structural switching circuits** (*strukturalna preklopna vezja*) in matrix notation:

- The **PDNO** and **PKNO** ([[Disjunctive Normal Form|complete disjunctive]] and [[Conjunctive Normal Form|conjunctive normal form]]) written with matrices: $y = (\tilde{x} \mathbin{\&\equiv} W^T) \mathbin{\lor\&} \tilde{f}$ and $y = (\tilde{x} \mathbin{\lor\nabla} W^T) \mathbin{\&\lor} \tilde{f}$. The vector of [[Minterm|minterms]] (or [[Maxterm|maxterms]]) is combined with the column of function values.
- **Functions with several outputs** (*funkcije z več izhodi*): the columns $\tilde{f}_1, \tilde{f}_2, \dots$ are joined into the matrix $D$, and the output vector is $\tilde{y} = (\tilde{x} \mathbin{\&\equiv} W^T) \mathbin{\lor\&} D$.
- Three building blocks:
  - **encoder** (*kodirnik*), $\tilde{y} = \tilde{m} \mathbin{\lor\&} K$: only one input is active at a time, and it is encoded into an output word;
  - **decoder** (*dekodirnik*), $\tilde{m} = \tilde{x} \mathbin{\&\equiv} D^T$: it maps the inputs to minterm outputs, with any matrix $D$;
  - **multiplexer** (*multiplekser*), $y = \tilde{m} \mathbin{\lor\&} \tilde{k}^T$: the address vector chooses which data input appears on the output. With a decoder in front, fewer connections are needed; parallel multiplexers give several outputs.

## Notes

### Recap: minterm and maxterm vectors

$$\tilde{m} = \tilde{x} \mathbin{\&\equiv} W^T \qquad \tilde{M} = \tilde{x} \mathbin{\lor\nabla} W^T$$

### PDNO in matrix form

$$f(x_1, x_2, \dots, x_n) = \bigvee_{i=0}^{2^n - 1} m_i f_i$$

$$y = \tilde{m} \mathbin{\lor\&} \tilde{f} = [m_0, m_1, m_2, m_3] \mathbin{\lor\&} \begin{bmatrix} f_0 \\ f_1 \\ f_2 \\ f_3 \end{bmatrix} \qquad \tilde{m} = [m_0, m_1, m_2, m_3] \qquad \tilde{f} = \begin{bmatrix} f_0 \\ f_1 \\ f_2 \\ f_3 \end{bmatrix}$$

$$y = m_0 f_0 \lor m_1 f_1 \lor m_2 f_2 \lor m_3 f_3$$

| $x_1$ | $x_2$ | $f(x_1, x_2)$ |
| :-: | :-: | :-: |
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

$$W = \underbrace{\begin{bmatrix} 0 & 0 \\ 0 & 1 \\ 1 & 0 \\ 1 & 1 \end{bmatrix}}_{n} \Big\}\, 2^n$$

$$y = f(\tilde{x}) = \underbrace{(\tilde{x} \mathbin{\&\equiv} W^T)}_{\tilde{m}} \mathbin{\lor\&} \tilde{f}$$

**Example** with $\tilde{x} = [x_1, x_2]$ and $\tilde{f} = [0, 1, 1, 0]^T$ (the function from the table):

$$
\begin{aligned}
y &= \left([x_1, x_2] \mathbin{\&\equiv} \begin{bmatrix} 0 & 0 \\ 0 & 1 \\ 1 & 0 \\ 1 & 1 \end{bmatrix}^T\right) \mathbin{\lor\&} \begin{bmatrix} 0 \\ 1 \\ 1 \\ 0 \end{bmatrix} = \left([x_1, x_2] \mathbin{\&\equiv} \begin{bmatrix} 0 & 0 & 1 & 1 \\ 0 & 1 & 0 & 1 \end{bmatrix}\right) \mathbin{\lor\&} \begin{bmatrix} 0 \\ 1 \\ 1 \\ 0 \end{bmatrix} \\
&= [(x_1 \equiv 0)(x_2 \equiv 0),\ (x_1 \equiv 0)(x_2 \equiv 1),\ (x_1 \equiv 1)(x_2 \equiv 0),\ (x_1 \equiv 1)(x_2 \equiv 1)] \mathbin{\lor\&} \begin{bmatrix} 0 \\ 1 \\ 1 \\ 0 \end{bmatrix} \\
&= [\bar{x}_1 \bar{x}_2,\ \bar{x}_1 x_2,\ x_1 \bar{x}_2,\ x_1 x_2] \mathbin{\lor\&} \begin{bmatrix} 0 \\ 1 \\ 1 \\ 0 \end{bmatrix} \\
&= \bar{x}_1 \bar{x}_2\, 0 \lor \bar{x}_1 x_2\, 1 \lor x_1 \bar{x}_2\, 1 \lor x_1 x_2\, 0 \\
&= \bar{x}_1 x_2 \lor x_1 \bar{x}_2
\end{aligned}
$$

### PKNO in matrix form

$$y = (\tilde{x} \mathbin{\&\equiv} W^T) \mathbin{\lor\&} \tilde{f} \quad \text{(PDNO)} \qquad\qquad y = (\tilde{x} \mathbin{\lor\nabla} W^T) \mathbin{\&\lor} \tilde{f} \quad \text{(PKNO)}$$

The same function:

$$
\begin{aligned}
y &= \left([x_1, x_2] \mathbin{\lor\nabla} \begin{bmatrix} 0 & 0 & 1 & 1 \\ 0 & 1 & 0 & 1 \end{bmatrix}\right) \mathbin{\&\lor} \begin{bmatrix} 0 \\ 1 \\ 1 \\ 0 \end{bmatrix} \\
&= [(x_1 \nabla 0) \lor (x_2 \nabla 0),\ (x_1 \nabla 0) \lor (x_2 \nabla 1),\ (x_1 \nabla 1) \lor (x_2 \nabla 0),\ (x_1 \nabla 1) \lor (x_2 \nabla 1)] \mathbin{\&\lor} \begin{bmatrix} 0 \\ 1 \\ 1 \\ 0 \end{bmatrix} \\
&= [x_1 \lor x_2,\ x_1 \lor \bar{x}_2,\ \bar{x}_1 \lor x_2,\ \bar{x}_1 \lor \bar{x}_2] \mathbin{\&\lor} \begin{bmatrix} 0 \\ 1 \\ 1 \\ 0 \end{bmatrix} \\
&= (x_1 \lor x_2 \lor 0)\underbrace{(x_1 \lor \bar{x}_2 \lor 1)}_{1}\underbrace{(\bar{x}_1 \lor x_2 \lor 1)}_{1}(\bar{x}_1 \lor \bar{x}_2 \lor 0) \\
&= (x_1 \lor x_2)(\bar{x}_1 \lor \bar{x}_2)
\end{aligned}
$$

A maxterm that is joined with $f_i = 1$ becomes $1$ and drops out of the product.

### Functions with several outputs (*funkcije z več izhodi*)

| $x_1$ | $x_2$ | $f_1(x_1, x_2)$ ($y_1$) | $f_2(x_1, x_2)$ ($y_2$) | $f_3(x_1, x_2)$ ($y_3$) | $f_4(x_1, x_2)$ ($y_4$) |
| :-: | :-: | :-: | :-: | :-: | :-: |
| 0 | 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 1 | 0 | 1 | 1 |
| 1 | 0 | 1 | 1 | 1 | 1 |
| 1 | 1 | 1 | 0 | 0 | 0 |

The right side of the table (the function values) is the matrix $D$:

$$\tilde{x} = [x_1, x_2] \qquad \tilde{y} = [y_1, y_2, y_3, y_4] \qquad W = \begin{bmatrix} 0 & 0 \\ 0 & 1 \\ 1 & 0 \\ 1 & 1 \end{bmatrix} \qquad D = \tilde{f}_1\, \tilde{f}_2\, \tilde{f}_3\, \tilde{f}_4 = \begin{bmatrix} 0 & 1 & 1 & 0 \\ 1 & 0 & 1 & 1 \\ 1 & 1 & 1 & 1 \\ 1 & 0 & 0 & 0 \end{bmatrix}$$

$$\tilde{y} = (\tilde{x} \mathbin{\&\equiv} W^T) \mathbin{\lor\&} D \qquad\qquad \tilde{y} = (\tilde{x} \mathbin{\lor\nabla} W^T) \mathbin{\&\lor} D$$

$$
\begin{aligned}
\tilde{y} &= \left([x_1, x_2] \mathbin{\&\equiv} \begin{bmatrix} 0 & 0 \\ 0 & 1 \\ 1 & 0 \\ 1 & 1 \end{bmatrix}^T\right) \mathbin{\lor\&} \begin{bmatrix} 0 & 1 & 1 & 0 \\ 1 & 0 & 1 & 1 \\ 1 & 1 & 1 & 1 \\ 1 & 0 & 0 & 0 \end{bmatrix} = [\bar{x}_1 \bar{x}_2,\ \bar{x}_1 x_2,\ x_1 \bar{x}_2,\ x_1 x_2] \mathbin{\lor\&} \begin{bmatrix} 0 & 1 & 1 & 0 \\ 1 & 0 & 1 & 1 \\ 1 & 1 & 1 & 1 \\ 1 & 0 & 0 & 0 \end{bmatrix} \\
&= [\bar{x}_1 \bar{x}_2\, 0 \lor \bar{x}_1 x_2\, 1 \lor x_1 \bar{x}_2\, 1 \lor x_1 x_2\, 1,\ \ \bar{x}_1 \bar{x}_2\, 1 \lor \bar{x}_1 x_2\, 0 \lor x_1 \bar{x}_2\, 1 \lor x_1 x_2\, 0, \\
&\qquad \bar{x}_1 \bar{x}_2\, 1 \lor \bar{x}_1 x_2\, 1 \lor x_1 \bar{x}_2\, 1 \lor x_1 x_2\, 0,\ \ \bar{x}_1 \bar{x}_2\, 0 \lor \bar{x}_1 x_2\, 1 \lor x_1 \bar{x}_2\, 1 \lor x_1 x_2\, 0] \\
&= [\underbrace{\bar{x}_1 x_2 \lor x_1 \bar{x}_2 \lor x_1 x_2}_{y_1},\ \underbrace{\bar{x}_1 \bar{x}_2 \lor x_1 \bar{x}_2}_{y_2},\ \underbrace{\bar{x}_1 \bar{x}_2 \lor \bar{x}_1 x_2 \lor x_1 \bar{x}_2}_{y_3},\ \underbrace{\bar{x}_1 x_2 \lor x_1 \bar{x}_2}_{y_4}]
\end{aligned}
$$

### Encoder (*kodirnik*)

The encoder encodes (*kodira*). Its inputs have the minterm property (*mintermsko značilnost*): only one input is active at a time. They are not minterms, though (*niso mintermi*). With 4 inputs there are 4 possibilities: $0001$, $0010$, $0100$, $1000$.

![[Digital Circuits 8 encoder.svg]]

Through the encoding matrix $K$ (*kodirna matrika*) it encodes the inputs into the outputs:

| inputs | outputs |
| :-: | :-: |
| 4 | 2 |
| 8 | 3 |
| 16 | 4 |
| 10 | 4 (not all combinations are used) |

$$\tilde{m} = [m_0, m_1, m_2, m_3] \qquad \tilde{y} = [y_1, y_2]$$

The equation of the encoder:

$$\tilde{y} = \tilde{m} \mathbin{\lor\&} K$$

For an input $[x_1, x_2]$ the minterm vector is $\tilde{m}([x_1, x_2])$, e.g. $\tilde{m}([0, 1]) = [0, 1, 0, 0]$.

**Encoder with 8 inputs and 3 outputs:**

$$\tilde{y} = [m_0, m_1, m_2, m_3, m_4, m_5, m_6, m_7] \mathbin{\lor\&} \begin{bmatrix} 0 & 0 & 0 \\ 0 & 0 & 1 \\ 0 & 1 & 0 \\ 0 & 1 & 1 \\ 1 & 0 & 0 \\ 1 & 0 & 1 \\ 1 & 1 & 0 \\ 1 & 1 & 1 \end{bmatrix} = [m_4 \lor m_5 \lor m_6 \lor m_7,\ m_2 \lor m_3 \lor m_6 \lor m_7,\ m_1 \lor m_3 \lor m_5 \lor m_7]$$

$$\tilde{y} = [y_1, y_2, y_3]$$

Row $i$ of $K$ is the binary code of $i$: the active input $m_i$ is encoded into the number $i$.

### Decoder (*dekodirnik*)

![[Digital Circuits 8 decoder.svg]]

| inputs | outputs |
| :-: | :-: |
| 2 | 4 |
| 3 | 8 |
| 4 | 16 |
| 4 | 10 (decimal system) |

$$\tilde{x} = [x_1, x_2, x_3] \qquad \tilde{m} = [m_0, m_1, \dots, m_7]$$

The equation of the decoder (DK):

$$\tilde{m} = \tilde{x} \mathbin{\&\equiv} D^T$$

We can put any matrix in place of $D$; the difference from the minterm vector is only in the matrix (*razlika v matriki*). For minterms:

$$\tilde{m} = \tilde{x} \mathbin{\&\equiv} W^T$$

Use: encoder — an elevator (*dvigalo*); decoder — addresses (*naslovi*).

$$\tilde{m} = [x_1, x_2, x_3] \mathbin{\&\equiv} \begin{bmatrix} 0 & 0 & 0 & 0 & 1 & 1 & 1 & 1 \\ 0 & 0 & 1 & 1 & 0 & 0 & 1 & 1 \\ 0 & 1 & 0 & 1 & 0 & 1 & 0 & 1 \end{bmatrix} = [(x_1 \equiv 0)(x_2 \equiv 0)(x_3 \equiv 0),\ (x_1 \equiv 0)(x_2 \equiv 0)(x_3 \equiv 1),\ \dots]$$

**Example — a different matrix $D$:** for $i = 0, \dots, 7$ the input $i$ activates the output $m_{(i + 3) \bmod 8}$: $i = 0 \to m_3$, $i = 1 \to m_4$, …

| $x_1$ | $x_2$ | $x_3$ | $m_0$ | $m_1$ | $m_2$ | $m_3$ | $m_4$ | $m_5$ | $m_6$ | $m_7$ |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| 1 | 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 |
| 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 |
| 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |

$$D = \begin{bmatrix} 1 & 0 & 1 \\ 1 & 1 & 0 \\ 1 & 1 & 1 \\ 0 & 0 & 0 \\ 0 & 0 & 1 \\ 0 & 1 & 0 \\ 0 & 1 & 1 \\ 1 & 0 & 0 \end{bmatrix}$$

Row $j$ of $D$ is the input that activates $m_j$. Compared with the ordinary decoder ($D = W$), the outputs are shifted by 3:

![[Digital Circuits 8 decoder permutation.svg]]

### Multiplexer (*multiplekser*)

Task: a switch that I turn left or right (*stikalo obrnem levo ali desno*). If $m_0$ is active, the output is $k_0$; if $m_1$ is active, the output is $k_1$.

![[Digital Circuits 8 multiplexer.svg]]

| $m_0$ | $m_1$ | $k_0$ | $k_1$ | $y$ |
| :-: | :-: | :-: | :-: | :-: |
| 1 | 0 | 0 | 0 | 0 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 0 | 1 | 1 | 1 |
| 0 | 1 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 | 1 |
| 0 | 1 | 1 | 0 | 0 |
| 0 | 1 | 1 | 1 | 1 |

Simplified (*poenostavljeno*):

| $m_0$ | $m_1$ | $y$ |
| :-: | :-: | :-: |
| 1 | 0 | $k_0$ |
| 0 | 1 | $k_1$ |

The inputs ($k_0$, $k_1$) appeared on the output side. The address vector (*naslovni vektor*) has the minterm property.

$$y = \tilde{m} \mathbin{\lor\&} \tilde{k}^T \qquad y = [m_0, m_1] \mathbin{\lor\&} \begin{bmatrix} k_0 \\ k_1 \end{bmatrix} = m_0 k_0 \lor m_1 k_1$$

**With a decoder in front:** to reduce the number of connections, I add a decoder (*da zmanjšam število povezav, dodam DK*). With 3 address inputs, 3 wires replace 8.

![[Digital Circuits 8 multiplexer with decoder.svg]]

**Parallel multiplexers** (*paralelni multiplekserji*): with larger multiplexers we achieve parallelism (more outputs).

![[Digital Circuits 8 parallel multiplexers.svg]]

$$\tilde{y} = [y_1, y_2, \dots] \qquad \tilde{y} = \tilde{m} \mathbin{\lor\&} K$$

### Multiplexer equations

$$y = (\tilde{x} \mathbin{\&\equiv} D^T) \mathbin{\lor\&} \tilde{k}^T \quad \text{(one output)} \qquad\qquad \tilde{y} = (\tilde{x} \mathbin{\&\equiv} D^T) \mathbin{\lor\&} K \quad \text{(several outputs)}$$

$K$ joins the input vectors of the individual multiplexers (*združitev vhodnih vektorjev za posamezen multiplekser*).

$$y = \tilde{m} \mathbin{\lor\&} \tilde{k}^T = [m_0, m_1, m_2, m_3] \mathbin{\lor\&} \begin{bmatrix} k_0 \\ k_1 \\ k_2 \\ k_3 \end{bmatrix} = m_0 k_0 \lor m_1 k_1 \lor m_2 k_2 \lor m_3 k_3$$

If $\tilde{m} = [0, 1, 0, 0]$, the output is $k_1$.

If we add a decoder, $\tilde{m}$ is replaced by $\tilde{x} \mathbin{\&\equiv} D^T$:

$$y = (\tilde{x} \mathbin{\&\equiv} D^T) \mathbin{\lor\&} \tilde{k}^T$$

## Questions

- [ ] 

## Connections

- Course: [[Introduction to Digital Circuits]]
- Previous lecture: [[2026-11-19 - Separating and Testing Symmetric Functions, Structural Switching Circuits - 7]] (matrix operations, the truth table in matrix form, minterm and maxterm vectors)
- [[2026-10-15 - Complete Normal Forms and Logic Functions - 2]]: PDNO and PKNO
- [[2026-11-12 - Minimal Conjunctive Form, Incompletely Specified and Symmetric Functions - 6]]: the elevator display, an example of encoding
- [[Minterm]], [[Maxterm]], [[Disjunctive Normal Form]], [[Conjunctive Normal Form]], [[Truth Table]], [[Encoder]], [[Decoder]], [[Multiplexer]]

## Sources

- Handwritten notes: [[Sources/introduction_to_digital_circuits/photoNotes/lectures/lecture 8.pdf|lecture 8]]
- Slides: [[Sources/introduction_to_digital_circuits/ODV.pdf#page=83|ODV]] (N. Zimic), chapter 7: PDNO and PKNO in matrix form, functions with several outputs (PDF pp. 83–85); encoder (pp. 86–88), decoder (pp. 89–91), multiplexer (pp. 91–94)
- Script: [[Sources/introduction_to_digital_circuits/ODV_skripta.pdf#page=46|ODV skripta]], *Multiplekser* (PDF p. 46)
