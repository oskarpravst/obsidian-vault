---
type: "[[Lectures]]"
course: "[[Introduction to Digital Circuits]]"
date: 2026-11-19
week: "7"
---

# 2026-11-19 - Separating and Testing Symmetric Functions, Structural Switching Circuits

## Main Idea

The lecture finished [[Symmetric Switching Function|symmetric functions]] and started a new chapter:

- **Separating symmetric functions** (*ločenje simetričnih funkcij*): we "factor out" one variable, $f_C = x_1 f_A \lor \bar{x}_1 f_B$; the remainders are again symmetric functions with shifted symmetry numbers.
- **Testing for symmetry** (*testiranje na simetričnost*): swap input pairs ($n - 1$ comparisons per input tuple, $2^n$ tuples), or use a [[Veitch Diagram|Veitch diagram]] with the number of 1s in each cell; the extended (4× larger) diagram finds the tuples in which the function is symmetric.
- **Structural switching circuits** (*strukturalna preklopna vezja*): matrix notation — joining matrices, the transpose, vector reduction and the Iverson–Liebig operations on matrices. With it, the [[Truth Table|truth table]], the vector of [[Minterm|minterms]] $\tilde{m} = \tilde{x} \mathbin{\&\equiv} W^T$ and the vector of [[Maxterm|maxterms]] $\tilde{M} = \tilde{x} \mathbin{\lor\nabla} W^T$ can be written compactly.

## Notes

### Symmetric functions (recap)

$$f(x_1, x_2, x_3) = f(x_2, x_1, x_3)$$

We can swap the inputs among themselves (*vhode lahko med sabo zamenjamo*).

$f(\bar{a}, b, \bar{c})$: the $i$-th permutation (input tuple) is symmetric (*i-ta permutacija je simetrična*).

### Separating symmetric functions (*ločenje simetričnih funkcij*)

$$f_C(x_1, x_2, x_3) = x_1 f_A(x_2, x_3) \lor \bar{x}_1 f_B(x_2, x_3)$$

We "factor out" one of the variables (*eno izmed spremenljivk "izpostavimo"*).

**Example:**

$$
\begin{aligned}
f_{\{2\}}(x_1, x_2, x_3) &= x_1 x_2 \bar{x}_3 \lor x_1 \bar{x}_2 x_3 \lor \bar{x}_1 x_2 x_3 \\
&= x_1 (x_2 \bar{x}_3 \lor \bar{x}_2 x_3) \lor \bar{x}_1 (x_2 x_3) \quad \text{(separated by } x_1\text{)} \\
&= x_1 f_{\{1\}}(x_2, x_3) \lor \bar{x}_1 f_{\{2\}}(x_2, x_3)
\end{aligned}
$$

If we separated by $x_3$, the notation would be the same (*če bi ločili po $x_3$, je enak zapis*).

**Example:** $f_{\{0,2,3\}}(x_1, x_2, x_3, x_4)$, separated by $x_1$ (truth table in [[2026-11-12 - Minimal Conjunctive Form, Incompletely Specified and Symmetric Functions - 6|lecture 6]]). The combinations where $f = 1$, grouped by the number of 1s, with $x_1$ split off from $x_2 x_3 x_4$:

| $m$ | $x_1$ | $x_2 x_3 x_4$ |
| :-: | :-: | :-: |
| {0} | 0 | 000 |
| {2} | 0 | 011, 101, 110 |
| | 1 | 001, 010, 100 |
| {3} | 0 | 111 |
| | 1 | 011, 101, 110 |

When $x_1 = 1$, the remaining variables have one or two 1s; when $x_1 = 0$, they have 0, 2 or 3:

$$f_{\{0,2,3\}}(x_1, x_2, x_3, x_4) = x_1 f_{\{1,2\}}(x_2, x_3, x_4) \lor \bar{x}_1 f_{\{0,2,3\}}(x_2, x_3, x_4)$$

### Testing for symmetry (*testiranje na simetričnost*)

![[Digital Circuits 7 symmetry testing.svg]]

We swap the inputs (*menjava*): if $f(b, a, c)$ and $f(c, b, a)$ are equal to $f(a, b, c)$, the function is already symmetric in this input tuple (*je že simetrična pri tem vhodnem naboru*). We need $(n - 1)$ comparisons (*primerjav*).

This has to be done for every input tuple:

$$f(\bar{a}, \bar{b}, \bar{c}),\ f(\bar{a}, \bar{b}, c),\ f(\bar{a}, b, \bar{c}),\ \dots,\ f(a, b, c)$$

$2^n$ input tuples (*vhodnih naborov*), so

$$\frac{2^n (n - 1)}{2} \text{ comparisons}$$

The tuples are paired ($f(\bar{a}, \bar{b}, \bar{c})$ with $f(a, b, c)$): if we negate the input variables, it is the same (*če negiram vhodne spremenljivke, je ista*), so half of the tests are enough.

#### With a Veitch diagram

In each cell we write the number of 1s in the input (left); next to it the function (right):

![[Digital Circuits 7 symmetry Veitch.svg]]

If all cells with the same number are all 1s or all 0s (*vse ista številka ima vse enke ali vse po vrednosti 0*), the function is symmetric.

For the other input tuples we use the extended Veitch diagram (*razširjeni Veitchev diagram*), 4× larger, and shift the function over it (*in premikamo*). We get 2 solutions (because of symmetry — *zaradi simetričnosti*):

$$f_{\{1,4\}}(\bar{x}_1, x_2, \bar{x}_3, x_4) \qquad f_{\{0,3\}}(x_1, \bar{x}_2, x_3, \bar{x}_4)$$

$$f_{\{1,4\}}(\bar{\bar{x}}_1, \bar{x}_2, \bar{\bar{x}}_3, \bar{x}_4) = f_{\{0,3\}}(x_1, \bar{x}_2, x_3, \bar{x}_4)$$

#### Kinds of symmetry

- completely non-symmetric (*popolnoma nesimetrične*)
- partially symmetric (*delno simetrične*)
- completely symmetric (*popolnoma simetrične*)

### Structural switching circuits (*strukturalna preklopna vezja*)

A matrix with its dimensions: the upper index is the number of rows (*št. vrstic*), the lower index the number of columns (*št. stolpcev*):

$$A^{1:3}_{1:3} = \begin{bmatrix} 1 & 1 & 1 \\ 1 & 1 & 1 \\ 1 & 1 & 1 \end{bmatrix}$$

#### Horizontal join (*vodoravna združitev*)

The number of rows must be equal (*št. vrstic enako*):

$$A = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix} \qquad B = \begin{bmatrix} 0 & 1 & 0 \\ 1 & 0 & 1 \end{bmatrix} \qquad C = A\,B = \begin{bmatrix} 1 & 0 & 0 & 1 & 0 \\ 0 & 1 & 1 & 0 & 1 \end{bmatrix}$$

#### Vertical join (*navpična združitev*)

The number of columns must be equal (*št. stolpcev enako*):

$$A = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix} \qquad B = \begin{bmatrix} 0 & 1 \\ 1 & 0 \\ 1 & 1 \end{bmatrix} \qquad C = \begin{matrix} A \\ B \end{matrix} = \begin{bmatrix} 1 & 0 \\ 0 & 1 \\ 0 & 1 \\ 1 & 0 \\ 1 & 1 \end{bmatrix}$$

#### Transposed matrix (*transponirana matrika*)

$$B^{1:m}_{1:n} = {A^T}^{1:m}_{1:n}$$

Rows and columns are swapped (*vrstice, stolpci se zamenja*). For an element of the matrix (*element matrike*):

$$b^i_j = a^j_i$$

The elements of a $2 \times 2$ matrix, written with two indices and with an upper (row) and a lower (column) index:

$$\begin{bmatrix} x_{11} & x_{12} \\ x_{21} & x_{22} \end{bmatrix} \qquad \begin{bmatrix} x^1_1 & x^1_2 \\ x^2_1 & x^2_2 \end{bmatrix}$$

$$A = \begin{bmatrix} 1 & 0 \\ 0 & 1 \\ 1 & 1 \end{bmatrix} \qquad A^T = \begin{bmatrix} 1 & 0 & 1 \\ 0 & 1 & 1 \end{bmatrix}$$

The columns of $A$ become the rows of $A^T$:

$$A = \underbrace{\begin{bmatrix} 1 & 0 & 1 & 0 \\ 0 & 1 & 1 & 0 \end{bmatrix}}_{4} \Big\}\, 2 \qquad A^T = \underbrace{\begin{bmatrix} 1 & 0 \\ 0 & 1 \\ 1 & 1 \\ 0 & 0 \end{bmatrix}}_{2} \Big\}\, 4$$

#### Operations on vectors (*operacije nad vektorji*)

**Vector reduction (row)** (*vektorska redukcija (vrstica)*):

$$c = {*}/\tilde{a}_{1:n} \qquad c = a_1 * a_2 * \dots * a_n$$

$$\tilde{a} = [1\ 0\ 1] \qquad c = \nabla/\tilde{a} = 1 \nabla 0 \nabla 1 = 0 \qquad d = \&/\tilde{a} = 1 \cdot 0 \cdot 1 = 0$$

**Vector reduction (column)** (*vektorska redukcija (stolpca)*):

$$c = {*}/\tilde{a}^{1:m} \qquad \tilde{b} = \begin{bmatrix} 0 \\ 1 \\ 1 \end{bmatrix} \qquad c = \lor/\tilde{b} = 0 \lor 1 \lor 1 = 1$$

#### Operations on matrices (*operacije nad matrikami*)

Introduced by Iverson and Liebig; the operation requires 2 operators (*2 operatorja zahteva*):

$$A \mathbin{\lor\&} B = \begin{bmatrix} a_{11} & a_{12} \\ a_{21} & a_{22} \\ a_{31} & a_{32} \end{bmatrix} \mathbin{\lor\&} \begin{bmatrix} b_{11} & b_{12} \\ b_{21} & b_{22} \end{bmatrix} = \begin{bmatrix} a_{11} b_{11} \lor a_{12} b_{21} & a_{11} b_{12} \lor a_{12} b_{22} \\ a_{21} b_{11} \lor a_{22} b_{21} & a_{21} b_{12} \lor a_{22} b_{22} \\ a_{31} b_{11} \lor a_{32} b_{21} & a_{31} b_{12} \lor a_{32} b_{22} \end{bmatrix}$$

The inner operator ($\&$) combines a row of the first matrix (*ret. vr.*) with a column of the second (*ret. st.*), the outer one ($\lor$) reduces the results.

- The number of columns of the 1st matrix must equal the number of rows of the 2nd matrix (*št. stolpcev 1. matrike mora biti enako št. vrstic 2. matrike*).
- The result has the number of rows of the 1st matrix and the number of columns of the 2nd (here $3 \times 2$).

**Example** with $\lor\nabla$:

$$A = \begin{bmatrix} 1 & 0 & 1 \\ 0 & 1 & 1 \end{bmatrix} \qquad B = \begin{bmatrix} 0 & 1 & 1 \\ 1 & 0 & 0 \\ 1 & 1 & 1 \end{bmatrix}$$

$$
\begin{aligned}
A \mathbin{\lor\nabla} B &= \begin{bmatrix} 1\nabla0 \lor 0\nabla1 \lor 1\nabla1 & 1\nabla1 \lor 0\nabla0 \lor 1\nabla1 & 1\nabla1 \lor 0\nabla0 \lor 1\nabla1 \\ 0\nabla0 \lor 1\nabla1 \lor 1\nabla1 & 0\nabla1 \lor 1\nabla0 \lor 1\nabla1 & 0\nabla1 \lor 1\nabla0 \lor 1\nabla1 \end{bmatrix} \\
&= \begin{bmatrix} 1 \lor 1 \lor 0 & 0 \lor 0 \lor 0 & 0 \lor 0 \lor 0 \\ 0 \lor 0 \lor 0 & 1 \lor 1 \lor 0 & 1 \lor 1 \lor 0 \end{bmatrix} = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 1 \end{bmatrix}
\end{aligned}
$$

**Negation of a matrix** (*negacija matrike*):

$$B = \begin{bmatrix} 0 & 1 & 1 \\ 1 & 0 & 0 \\ 1 & 1 & 1 \end{bmatrix} \qquad \bar{B} = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 1 \\ 0 & 0 & 0 \end{bmatrix}$$

**One binary operator** (*en binarni operator*), element by element: $A * B = C$; the dimensions of the matrices must be equal (*dimenzije matrik morajo biti enake*).

$$A = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix} \qquad B = \begin{bmatrix} 1 & 1 \\ 1 & 0 \end{bmatrix} \qquad A \mathbin{\&} B = \begin{bmatrix} 1\&1 & 0\&1 \\ 0\&1 & 1\&0 \end{bmatrix} = \begin{bmatrix} 1 & 0 \\ 0 & 0 \end{bmatrix}$$

### Truth table in matrix form (*pravilnostna tabela*)

$$\begin{array}{c|c} \tilde{x} & y \\ \hline W & \tilde{f} \end{array}$$

| $x_1$ | $x_2$ | $x_3$ | $f(x_1, x_2, x_3) = y$ |
| :-: | :-: | :-: | :-: |
| 0 | 0 | 0 | 1 |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 1 |
| 1 | 1 | 1 | 0 |

$$\tilde{x} = [x_1, x_2, x_3] \qquad \tilde{f} = \begin{bmatrix} 1 \\ 0 \\ 1 \\ 1 \\ 0 \\ 1 \\ 1 \\ 0 \end{bmatrix} \qquad \tilde{f}^T = [1\ 0\ 1\ 1\ 0\ 1\ 1\ 0] \qquad W = \begin{bmatrix} 0 & 0 & 0 \\ 0 & 0 & 1 \\ 0 & 1 & 0 \\ 0 & 1 & 1 \\ 1 & 0 & 0 \\ 1 & 0 & 1 \\ 1 & 1 & 0 \\ 1 & 1 & 1 \end{bmatrix}$$

$W$ is the left side of the truth table (all input combinations), $\tilde{f}$ the column of function values.

### Minterm notation (*zapis minterma*)

$$m_i = x_1^{w_{1,i}} x_2^{w_{2,i}} \dots x_n^{w_{n,i}} \qquad x^1 = x, \quad x^0 = \bar{x}$$

$$x \equiv 1 = x \qquad x \equiv 0 = \bar{x}$$

(in the notebook first written with a general operator $*$: $x * 1 = x$, $x * 0 = \bar{x}$)

The vector of minterms:

$$\tilde{m} = [m_0, m_1, \dots, m_{2^n - 1}] \qquad \tilde{m} = \tilde{x} \mathbin{\&\equiv} W^T$$

($\tilde{x}$ has $n$ elements, $W^T$ is $n \times 2^n$, $\tilde{m}$ has $2^n$ elements.)

For $n = 3$:

$$\tilde{m} = [m_0, m_1, m_2, \dots, m_7] = [x_1, x_2, x_3] \mathbin{\&\equiv} \begin{bmatrix} 0 & 0 & 0 & 0 & 1 & 1 & 1 & 1 \\ 0 & 0 & 1 & 1 & 0 & 0 & 1 & 1 \\ 0 & 1 & 0 & 1 & 0 & 1 & 0 & 1 \end{bmatrix} \quad (= W^T)$$

$$
\begin{aligned}
\tilde{m} &= [(x_1 \equiv 0)(x_2 \equiv 0)(x_3 \equiv 0),\ (x_1 \equiv 0)(x_2 \equiv 0)(x_3 \equiv 1),\ \dots,\ (x_1 \equiv 1)(x_2 \equiv 1)(x_3 \equiv 1)] \\
&= [\bar{x}_1 \bar{x}_2 \bar{x}_3,\ \bar{x}_1 \bar{x}_2 x_3,\ \dots,\ x_1 x_2 x_3] = [m_0, m_1, \dots, m_7]
\end{aligned}
$$

**Minterm vector for a constant input** (*konstanten vhod*):

$$\tilde{m}([0, 1, 0]) = [0, 1, 0] \mathbin{\&\equiv} \dots = [(0 \equiv 0)(1 \equiv 0)(0 \equiv 0),\ (0 \equiv 0)(1 \equiv 0)(0 \equiv 1),\ (0 \equiv 0)(1 \equiv 1)(0 \equiv 0),\ (0 \equiv 0)(1 \equiv 1)(0 \equiv 1),\ \dots]$$

$$\tilde{m}([0, 1, 0]) = [0, 0, 1, 0, 0, 0, 0, 0]$$

Only the minterm whose number this is equals 1 (*samo ko je to št. minterma, kjer je 1*).

### Maxterm (*maksterm*)

$$M_{2^n - i - 1} = x_1^{\overline{w_{1i}}} \lor x_2^{\overline{w_{2i}}} \lor \dots \lor x_n^{\overline{w_{ni}}}$$

$$\tilde{M} = [M_{2^n - 1}, M_{2^n - 2}, \dots, M_0] \qquad \tilde{M} = \tilde{x} \mathbin{\lor\nabla} W^T$$

$$x \equiv 1 = x \qquad x \equiv 0 = \bar{x} \qquad\qquad x \nabla 1 = \bar{x} \qquad x \nabla 0 = x$$

**Example** for $n = 2$:

$$\tilde{M} = [x_1, x_2] \mathbin{\lor\nabla} \begin{bmatrix} 0 & 0 & 1 & 1 \\ 0 & 1 & 0 & 1 \end{bmatrix} \qquad W = \begin{bmatrix} 0 & 0 \\ 0 & 1 \\ 1 & 0 \\ 1 & 1 \end{bmatrix}$$

$$
\begin{aligned}
\tilde{M} = [M_3, M_2, M_1, M_0] &= [(x_1 \nabla 0) \lor (x_2 \nabla 0),\ (x_1 \nabla 0) \lor (x_2 \nabla 1),\ (x_1 \nabla 1) \lor (x_2 \nabla 0),\ (x_1 \nabla 1) \lor (x_2 \nabla 1)] \\
&= [x_1 \lor x_2,\ x_1 \lor \bar{x}_2,\ \bar{x}_1 \lor x_2,\ \bar{x}_1 \lor \bar{x}_2] = [M_3, M_2, M_1, M_0]
\end{aligned}
$$

$$\tilde{M}([0, 0]) = [0, 1, 1, 1]$$

## Questions

- [ ] Why can the number of symmetry tests be halved — why does negating all input variables keep a function symmetric?
- [ ] How exactly do we shift the function over the extended Veitch diagram to read off the input tuple in which it is symmetric?

## Connections

- Course: [[Introduction to Digital Circuits]]
- Previous lecture: [[2026-11-12 - Minimal Conjunctive Form, Incompletely Specified and Symmetric Functions - 6]] (symmetric functions, symmetry numbers, the function $f_{\{0,2,3\}}$)
- [[2026-10-15 - Complete Normal Forms and Logic Functions - 2]]: minterms, maxterms and $\nabla$ (sum modulo 2)
- [[2026-10-22 - Veitch Diagrams, Shannon Expansion and Decomposition - 3]]: separation is the [[Shannon Expansion|Shannon expansion]] by one variable
- [[Symmetric Switching Function]], [[Veitch Diagram]], [[Minterm]], [[Maxterm]], [[Truth Table]], [[Exclusive Or]], [[Matrix Transpose]]

## Sources

- Handwritten notes: [[Sources/introduction_to_digital_circuits/photoNotes/lectures/lecture 7.pdf|lecture 7]]
- Slides: [[Sources/introduction_to_digital_circuits/ODV.pdf#page=73|ODV]] (N. Zimic), separating symmetric functions and testing for symmetry, extended Veitch diagram (PDF pp. 73–75); chapter 7 *Strukturalna preklopna vezja*: joining matrices, transpose, vector reduction, Iverson–Liebig operations, truth table, minterm and maxterm vectors (PDF pp. 76–83)
- Script: [[Sources/introduction_to_digital_circuits/ODV_skripta.pdf#page=45|ODV skripta]], 7.1 *Ločenje preklopnih funkcij* (PDF p. 45)
