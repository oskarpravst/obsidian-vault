---
type: "[[Concepts]]"
status: developed
aliases:
  - DFT
  - Diskretna Fourierova transformacija
  - Spectral decomposition
  - Spektralna dekompozicija
---

# Discrete Fourier Transform

## Definition

A signal of $N$ samples $X = (x_0, x_1, \dots, x_{N-1})$ is written as a combination of "pure frequency" vectors

$$C_k = \left(e^{i2\pi\frac{k n}{N}}\right)_{n=0}^{N-1}, \qquad X = \sum_{k=0}^{N-1} y_k\,C_k, \qquad y_k = r_k\,e^{i\varphi_k} \in \mathbb{C}$$

This is the **spectral decomposition** (*spektralna dekompozicija*). The **DFT** computes the coefficients:

$$y_q = \frac{1}{N}\,X \cdot \overline{C_q} = \frac{1}{N}\sum_{n=0}^{N-1} x_n\,e^{-i2\pi\frac{q n}{N}}$$

- $k$ … frequency (*frekvenca*), $r_k = |y_k|$ … strength (*jakost*), $\varphi_k$ … shift (*zamik*).

## Explanation

- **Why it works:** the vectors $C_k$ are pairwise perpendicular in the complex [[Dot Product|scalar product]]:

$$C_p \cdot \overline{C_q} = \begin{cases} 0, & p \neq q \\ N, & p = q \end{cases}$$

  So multiplying $X$ by $\overline{C_q}$ kills every term except $k = q$ — $y_q$ is the projection of $X$ onto $C_q$.
- **Uniqueness:** every signal has exactly one such representation.
- The entries of $C_k$ are powers of an $N$-th root of unity, so they lie on a regular $N$-gon in the complex plane ([[Euler's Formula|Euler's formula]]).
- **Real signals:** $C_k = \overline{C_{N-k}}$ always, and for real signals the coefficients satisfy $y_k = \overline{y_{N-k}}$.
- **Convention:** many books define the DFT without $\frac{1}{N}$ (as $\sum_n x_n e^{-i2\pi qn/N}$) and put the $\frac{1}{N}$ in the inverse transform. The lecture's $y_q$ is that value divided by $N$.

## Examples

**Cosine and sine** (Calculus 3), from $\cos t = \frac{e^{it} + e^{-it}}{2}$ and $\sin t = \frac{e^{it} - e^{-it}}{2i}$:

$$\left(\cos\tfrac{2\pi kn}{N}\right)_n = \tfrac{1}{2}C_k + \tfrac{1}{2}C_{N-k}, \qquad \left(\sin\tfrac{2\pi kn}{N}\right)_n = -\tfrac{i}{2}C_k + \tfrac{i}{2}C_{N-k}$$

**$\cos t + \sin t$** (Calculus 3): the coefficients $\frac{1}{2} \mp \frac{i}{2} = \frac{1}{\sqrt{2}}e^{\mp i\pi/4}$ give

$$\cos t + \sin t = \sqrt{2}\,\cos\left(t - \frac{\pi}{4}\right)$$

**Noise cancelling:** $\cos t + \cos(t + \pi) = 0$ — adding a signal shifted by $\pi$ removes it.

## Connections

- [[2026-10-21 - Spectral Decomposition and Sequences - 3]] — $C_k$, spectral decomposition, the lemma, DFT (Calculus)
- [[2026-10-14 - Polar Form of Complex Numbers - 2]] — Euler's formula, $n$-th roots of unity (Calculus)
- [[Dot Product]] — the scalar product of complex vectors; also used for work in Physics
- [[Complex Number]], [[Euler's Formula]], [[De Moivre's Formula]]

## Sources

- Handwritten notes: [[Sources/calculus/photoNotes/lectures/lecture 3.pdf|Calculus lecture 3]]
- [Discrete Fourier transform — Wikipedia](https://en.wikipedia.org/wiki/Discrete_Fourier_transform)
