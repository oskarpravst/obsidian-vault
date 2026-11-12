---
type: "[[Lectures]]"
course: "[[Introduction to Digital Circuits]]"
date: 2026-11-12
week: "6"
---

# 2026-11-12 - Minimal Conjunctive Form, Incompletely Specified and Symmetric Functions

## Main Idea

The lecture continued [[Veitch Diagram|Veitch]] minimisation with a 5-variable example and then introduced three new topics:

- **MKNO** (minimal conjunctive normal form, *minimalna konjunktivna normalna oblika*): minimise the **negated** function as an MDNO, negate it again and apply [[De Morgan's Laws|De Morgan's laws]]. Comparing operators and inputs then shows which of MDNO and MKNO gives the cheaper circuit.
- **Minimisation of incompletely specified functions** (*minimizacija nepopolnih funkcij*): input combinations that can never occur are **don't cares** (X, *vseeno nam je*). In the Veitch diagram each X may be taken as 0 or 1, whichever gives larger groups. Example: a 7-segment display for an elevator.
- **Other important switching functions** (*ostale pomembne preklopne funkcije*): **invariance** to swapping two variables (*variantnost*), **symmetric functions** (*simetrične funkcije*), **symmetry numbers** (*simetrijska števila*), and how negation, disjunction and conjunction preserve symmetry.

## Notes

### Veitch minimisation with 5 variables

$$f(x_1, x_2, x_3, x_4, x_5) = \lor(4, 6, 7, 12, 14, 15, 16, 17, 22, 23, 27, 30, 31)$$

![[Digital Circuits 6 Veitch 5 variables example.svg]]

$$f(x_1, x_2, x_3, x_4, x_5) = x_3 x_4 \lor \bar{x}_1 x_3 \bar{x}_5 \lor x_1 x_2 x_4 x_5 \lor x_1 \bar{x}_2 \bar{x}_3 \bar{x}_4$$

(the term $x_1 x_2 x_4$ is crossed out in the notebook)

### Minimal conjunctive normal form (*minimalna konjunktivna normalna oblika*, MKNO)

We minimise the **negated** function (*negirana*): in the Veitch diagram we group the cells where $f = 0$. The negated function and the function itself:

![[Digital Circuits 6 MKNO Veitch.svg]]

$$\overline{f(x_1, x_2, x_3, x_4)} = \bar{x}_1 x_2 \lor x_2 \bar{x}_3 \lor x_1 \bar{x}_3 x_4 \lor \bar{x}_1 x_3 x_4$$

We negate once more and get the original function (*negiramo še enkrat → dobimo osnovno funkcijo*):

$$f(x_1, x_2, x_3, x_4) = \overline{\bar{x}_1 x_2 \lor x_2 \bar{x}_3 \lor x_1 \bar{x}_3 x_4 \lor \bar{x}_1 x_3 x_4} = (\overline{\bar{x}_1 x_2})(\overline{x_2 \bar{x}_3})(\overline{x_1 \bar{x}_3 x_4})(\overline{\bar{x}_1 x_3 x_4})$$

with [[De Morgan's Laws|De Morgan's laws]]:

$$\overline{a \lor b} = \bar{a}\bar{b} \qquad \overline{ab} = \bar{a} \lor \bar{b}$$

$$\Rightarrow f(x_1, x_2, x_3, x_4) = (x_1 \lor \bar{x}_2)(\bar{x}_2 \lor x_3)(\bar{x}_1 \lor x_3 \lor \bar{x}_4)(x_1 \lor \bar{x}_3 \lor \bar{x}_4) \quad \text{(MKNO)}$$

The same function as an MDNO (the first example of [[2026-11-05 - Minimisation of Switching Functions - 5|lecture 5]]):

$$f(x_1, x_2, x_3, x_4) = \bar{x}_1 \bar{x}_2 \bar{x}_3 \lor \bar{x}_2 \bar{x}_4 \lor x_1 x_3 \quad \text{(MDNO)}$$

#### Which is more efficient? (*katera je bolj učinkovita*)

![[Digital Circuits 6 MKNO and MDNO circuits.svg]]

- **MKNO:** 5 operators, 14 inputs (*vhodov*).
- **MDNO:** 4 operators, 10 inputs. This one is more favourable (*ta je bolj ugodna*).

#### Complexity on one more example (*kompleksnost še na enem primeru*)

$$f(x_1, x_2, x_3, x_4) = (\bar{x}_1 \lor \bar{x}_2 \lor x_4)(\bar{x}_2 \lor x_3 \lor \bar{x}_4)(x_1 \lor x_2 \lor \bar{x}_3)(x_1 \lor x_2 \lor x_4) \quad \text{(MKNO)}$$

$$f(x_1, x_2, x_3, x_4) = (x_1 \bar{x}_2) \lor (\bar{x}_2 \bar{x}_3 x_4) \lor (x_2 x_3 x_4) \lor (\bar{x}_1 x_2 \bar{x}_4) \quad \text{(MDNO)}$$

| | gates | inputs | total |
| --- | --- | --- | --- |
| **MKNO** ($3 + 3 + 3 + 3 + 4$) | 4 disjunctions (*DIS*) | 3 inputs each | 5 operators, **16 inputs** |
| | 1 conjunction (*KON*) | 4 inputs | |
| **MDNO** | 1 conjunction | 2 inputs | 5 operators, **15 inputs** |
| | 3 conjunctions | 3 inputs each | |
| | 1 disjunction | 4 inputs | |

### Minimisation of incompletely specified functions (*minimizacija nepopolnih funkcij*)

Example: a keypad with the digits 1–9 and 0, coded with $x_1 x_2 x_3 x_4$:

| $x_1$ | $x_2$ | $x_3$ | $x_4$ | |
| :-: | :-: | :-: | :-: | :-: |
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 0 | 1 | 1 |
| 0 | 0 | 1 | 0 | 2 |
| | | ⋮ | | |
| 1 | 0 | 0 | 0 | 8 |
| 1 | 0 | 0 | 1 | 9 |

These are **legal** combinations (*legalne*, the function is defined — *definirana funkcija*). The remaining ones ($1010$, $1011$, $1100$, …) we cannot realise (*ne moremo realizirati*): there the function is **undefined** (*nedefinirana funkcija*).

#### Example

![[Digital Circuits 6 incomplete function Veitch.svg]]

$$d(x_1, x_2, x_3, x_4) = \lor(0, 2, 5) \;\rightarrow\; \text{undefined (*nedefinirana*)}$$

| $x_1$ | $x_2$ | $x_3$ | $x_4$ | $f$ |
| :-: | :-: | :-: | :-: | :-: |
| 0 | 0 | 0 | 0 | X → we don't care (*vseeno nam je*) |
| 0 | 0 | 0 | 1 | 1 |
| 0 | 0 | 1 | 0 | X → we don't care |
| 0 | 0 | 1 | 1 | 1 |
| 0 | 1 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 | X → we don't care |
| 0 | 1 | 1 | 0 | 0 |
| 0 | 1 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 | 0 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 0 |
| 1 | 0 | 1 | 1 | 1 |
| 1 | 1 | 0 | 0 | 0 |
| 1 | 1 | 0 | 1 | 0 |
| 1 | 1 | 1 | 0 | 0 |
| 1 | 1 | 1 | 1 | 1 |

Two minimisations, depending on which X we take as 1:

$$f_1(x_1, x_2, x_3, x_4) = x_3 x_4 \lor \bar{x}_1 x_4 \qquad f_2(x_1, x_2, x_3, x_4) = x_3 x_4 \lor \bar{x}_1 \bar{x}_2$$

$f_1$ and $f_2$ are different functions, but both satisfy the conditions of undefinedness (*obe ustrezata pogojem nedefiniranosti*).

#### Example: elevator display (*dvigalo*)

The floor (ground floor *P* = *pritličje*, 1–4) is coded with $x_1 x_2 x_3$ and shown on a 7-segment display with segments $a$–$g$:

![[Digital Circuits 6 elevator display.svg]]

| | $x_1$ | $x_2$ | $x_3$ | $f_a$ | $f_b$ | $f_c$ | $f_d$ | $f_e$ | $f_f$ | $f_g$ |
| --- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| P | 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | 0 |
| 2 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 1 |
| 3 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 1 |
| 4 | 1 | 0 | 0 | 0 | 1 | 1 | 0 | 0 | 1 | 1 |
| — | 1 | 0 | 1 | X₀ | X₁ | X₁ | X₀ | X₀ | X₀ | X₀ |
| — | 1 | 1 | 0 | X₁ | X₁ | X₁ | X₁ | X₀ | X₀ | X₁ |
| — | 1 | 1 | 1 | X₁ | X₁ | X₁ | X₁ | X₀ | X₀ | X₁ |

The last three rows: the elevator cannot go higher than the 4th floor (*dvigalo ne more iti višje kot v 4. nadstropje*). We don't care about them, because such an input must never arrive (*ker tak vhod nikoli ne sme priti*). The subscript is the value chosen for the X during minimisation.

![[Digital Circuits 6 seven-segment Veitch.svg]]

$$
\begin{aligned}
f_a(x_1, x_2, x_3) &= x_2 \lor \bar{x}_1 \bar{x}_3 \\
f_b(x_1, x_2, x_3) &= 1 \quad \text{(because it is always on — *ker vedno gori*)} \\
f_c(x_1, x_2, x_3) &= x_1 \lor x_3 \\
f_d(x_1, x_2, x_3) &= x_2 \\
f_e(x_1, x_2, x_3) &= \bar{x}_1 \bar{x}_3 \\
f_f(x_1, x_2, x_3) &= \bar{x}_2 \bar{x}_3 \\
f_g(x_1, x_2, x_3) &= x_2 \lor \bar{x}_3
\end{aligned}
$$

With these choices the codes $101$, $110$ and $111$ show "1", "3" and "3" (the elevator display at the top). In our case the digits make sense (*so smiselne številke*), but we could also get rubbish (*lahko pa bi dobili krneki*).

### Other important switching functions (*ostale pomembne preklopne funkcije*)

#### Invariance (*variantnost*)

![[Digital Circuits 6 swapping variables.svg]]

$$f(a, b, c) = f(b, a, c)$$

(so it is invariant to the general notation — *torej je invariantna na splošen zapis*)

$f(x_1, x_2, \dots, x_i, \dots, x_j, \dots, x_n)$ is independent of swapping the variables (*neodvisna na zamenjavo spremenljivk*) if

$$f(x_1, x_2, \dots, x_i, \dots, x_j, \dots, x_n) = f(x_1, x_2, \dots, x_j, \dots, x_i, \dots, x_n) = (i, j)\, f(x_1, x_2, \dots, x_n)$$

$(i, j)$ means that we can swap $i$ and $j$ (*da lahko i, j zamenjamo*).

#### Symmetric functions (*simetrične funkcije*)

- **symmetric** (*simetrična*) if we can swap all variables,
- **partially symmetric** (*delno simetrična*) if we can swap some,
- **non-symmetric** (*nesimetrična*) if we may swap none.

Symmetry is also checked with negated variables. A tuple (*nabor*) of variables:

$$\tilde{x}^{\tilde{w}_i} = \{x_1^{w_{1i}}, x_2^{w_{2i}}, \dots, x_n^{w_{ni}}\} \quad \rightarrow \; 2^n \text{ tuples (*naborov*)}$$

**Symmetry** (*simetričnost*): we have to check every tuple separately (a lot of work — *veliko dela*).

#### Symmetry numbers (*simetrijska števila*)

![[Digital Circuits 6 switching function box.svg]]

The input combinations are grouped by the number of 1s $m$; a symmetric function has the same value for all inputs of one group (*pri vseh vhodih enaka vrednost*).

For 3 variables:

| $m$ | combinations $abc$ |
| :-: | --- |
| 0 | 000 |
| 1 | 100, 010, 001 |
| 2 | 110, 101, 011 |
| 3 | 111 |

For 4 variables:

| $m$ | combinations |
| :-: | --- |
| 0 | 0000 |
| 1 | 0001, 0010, 0100, 1000 |
| 2 | 0011, 0101, 1001, 0110, 1010, 1100 |
| 3 | 0111, 1011, 1101, 1110 |
| 4 | 1111 |

**Example:** $f_{\{0,2\}}(x_1, x_2, x_3)$ is 1 when there are no 1s or when there are two 1s (*ko ni 0 enic, ko sta 2 enici*):

| $x_1$ | $x_2$ | $x_3$ | $f_{\{0,2\}}(x_1, x_2, x_3)$ |
| :-: | :-: | :-: | :-: |
| 0 | 0 | 0 | 1 |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 1 |
| 1 | 1 | 1 | 0 |

$$f_{\{0,2\}}(x_1, x_2, x_3) = \bar{x}_1 \bar{x}_2 \bar{x}_3 \lor \bar{x}_1 x_2 x_3 \lor x_1 \bar{x}_2 x_3 \lor x_1 x_2 \bar{x}_3$$

Symmetric functions are hard to minimise (*simetrične funkcije se težko minimizira*).

**Symmetry with a negated variable.** The number above each term is the number of 1s:

$$f(x_1, x_2, x_3) = \overset{1}{\bar{x}_1 \bar{x}_2 x_3} \lor \overset{1}{\bar{x}_1 x_2 \bar{x}_3} \lor \overset{2}{\bar{x}_1 x_2 x_3} \lor \overset{3}{x_1 x_2 x_3}$$

$$f(\bar{x}_1, x_2, x_3) = \overset{2}{x_1 \bar{x}_2 x_3} \lor \overset{2}{x_1 x_2 \bar{x}_3} \lor \overset{3}{x_1 x_2 x_3} \lor \overset{2}{\bar{x}_1 x_2 x_3} = f_{\{2,3\}}(\bar{x}_1, x_2, x_3)$$

$$f_{\{0,1,2,3\}}(x_1, x_2, x_3) = 1 \quad \text{(all combinations — *vse kombinacije*)}$$

#### Negation of symmetric functions

If we negate a symmetric function (*če negiramo simetrično funkcijo*):

$$\overline{f_{\{0,2\}}(x_1, x_2, x_3)} = f_{\{1,3\}}(x_1, x_2, x_3)$$

In general, for $f_A(x_1^{w_{1i}}, x_2^{w_{2i}}, \dots, x_n^{w_{ni}})$ and $f_B(x_1^{w_{1i}}, x_2^{w_{2i}}, \dots, x_n^{w_{ni}})$: the set $B$ contains all elements that are not in $A$ (*v množici B so vsi elementi, ki jih ni v A*):

$$B = \bar{A} = \{a \mid a \in U,\ a \notin A\}$$

$$\overline{f_{\{2,3\}}(\bar{x}_1, x_2, x_3)} = f_{\{0,1\}}(\bar{x}_1, x_2, x_3)$$

The negation of a symmetric function is again symmetric (*negacija sim. funkcije je spet simetrična*).

**Negating the input variables.** $f_{\{0,2\}}(\bar{x}_1, \bar{x}_2, \bar{x}_3)$: negating every combination turns $m$ ones into $3 - m$ ones:

| $m$ | combinations | negated (*neg.*) | $m$ |
| :-: | --- | --- | :-: |
| 0 | 000 | 111 | 3 |
| 2 | 011, 101, 110 | 100, 010, 001 | 1 |

$f_{\{2,3\}}(x_1, \bar{x}_2, \bar{x}_3)$: $\{2,3\} \rightarrow \{0,1\}$, the set changes (*nabor se spremeni*).

The negation of the input variables is again symmetric (*negacija vhodnih spremenljivk je spet simetrična*).

**Example with 4 variables**, $U = \{0, 1, 2, 3, 4\}$:

| $x_1$ | $x_2$ | $x_3$ | $x_4$ | $f_{\{0,2,3\}}(x_1, x_2, x_3, x_4)$ |
| :-: | :-: | :-: | :-: | :-: |
| 0 | 0 | 0 | 0 | 1 |
| 0 | 0 | 0 | 1 | 0 |
| 0 | 0 | 1 | 0 | 0 |
| 0 | 0 | 1 | 1 | 1 |
| 0 | 1 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 | 1 |
| 0 | 1 | 1 | 0 | 1 |
| 0 | 1 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 | 0 |
| 1 | 0 | 0 | 1 | 1 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 0 | 1 | 1 | 1 |
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 0 | 1 | 1 |
| 1 | 1 | 1 | 0 | 1 |
| 1 | 1 | 1 | 1 | 0 |

$$\overline{f_{\{0,2,3\}}(x_1, x_2, x_3, x_4)} = f_{\{1,4\}}(x_1, x_2, x_3, x_4)$$

$$f_{\{0,2,3\}}(\bar{x}_1, \bar{x}_2, \bar{x}_3, \bar{x}_4) = f_{\{1,2,4\}}(x_1, x_2, x_3, x_4)$$

$$\overline{f_{\{0,2,3\}}(\bar{x}_1, \bar{x}_2, \bar{x}_3, \bar{x}_4)} = f_{\{1,4\}}(\bar{x}_1, \bar{x}_2, \bar{x}_3, \bar{x}_4) = f_{\{0,3\}}(x_1, x_2, x_3, x_4)$$

#### Disjunction and conjunction of symmetric functions

Disjunction and conjunction of symmetric functions preserve symmetry (*disjunkcija, konjunkcija simetričnih funkcij ohranja simetričnost*), if both functions are symmetric in the same tuple $i$:

$$f_C(x_1^{w_{1i}}, \dots, x_n^{w_{ni}}) = f_A(x_1^{w_{1i}}, \dots, x_n^{w_{ni}}) \lor f_B(x_1^{w_{1i}}, \dots, x_n^{w_{ni}}), \qquad C = A \cup B$$

$$f_C(x_1^{w_{1i}}, \dots, x_n^{w_{ni}}) = f_A(x_1^{w_{1i}}, \dots, x_n^{w_{ni}})\, f_B(x_1^{w_{1i}}, \dots, x_n^{w_{ni}}), \qquad C = A \cap B$$

## Questions

- [ ] When is the MKNO cheaper than the MDNO, and can we tell before computing both?
- [ ] How do we choose the values of the don't cares (X) so that the display never shows "rubbish" for an illegal code?
- [ ] How do we find the tuple $\tilde{x}^{\tilde{w}_i}$ in which a function is symmetric without checking all $2^n$ tuples?

## Connections

- Course: [[Introduction to Digital Circuits]]
- Previous lecture: [[2026-11-05 - Minimisation of Switching Functions - 5]] (MDNO, Veitch minimisation; the two MDNOs used here)
- [[2026-10-22 - Veitch Diagrams, Shannon Expansion and Decomposition - 3]]: layout of the 5-variable Veitch diagram
- [[2026-11-02 - Prenex Normal Form, Sets and Russell's Paradox - 5]] (Discrete structures): the complement $\bar{A}$ of a set, used for symmetry numbers
- [[Conjunctive Normal Form]], [[Disjunctive Normal Form]], [[De Morgan's Laws]], [[Veitch Diagram]], [[Switching Function]], [[Maxterm]]
- [[Don't-care Condition]], [[Symmetric Switching Function]], [[Seven-segment Display]]

## Sources

- Handwritten notes: [[Sources/introduction_to_digital_circuits/photoNotes/lectures/lecture 6.pdf|lecture 6]]
- Slides: [[Sources/introduction_to_digital_circuits/ODV.pdf#page=61|ODV]] (N. Zimic), MKNO (PDF pp. 61–62), minimisation of incompletely specified functions (PDF pp. 63–64), chapter 6 *Ostale pomembne preklopne funkcije*: invariance, symmetric functions, negations (PDF pp. 65–70)
- Script: [[Sources/introduction_to_digital_circuits/ODV_skripta.pdf#page=36|ODV skripta]], MDNO/MKNO and number of operators/operands (PDF pp. 36–38), Zgled 16 incompletely specified function ([[Sources/introduction_to_digital_circuits/ODV_skripta.pdf#page=39|PDF p. 39]]), 6.1 symmetric switching functions, Zgled 17 $f_{\{0,2\}}$ ([[Sources/introduction_to_digital_circuits/ODV_skripta.pdf#page=41|PDF p. 41]])
