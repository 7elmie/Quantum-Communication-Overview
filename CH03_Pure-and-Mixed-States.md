# Section 3: Pure and Mixed States

This chapter will expand on what we learned in the previous chapter.
It will deal with pure and mixed states, and finally we will get to the description of real noisy quantum states.
The notation and mathematical tools that we develop in this chapter will be extremely useful in the rest of these lecture notes. If you have taken an introductory course in quantum computation, your course may or may not have covered these topics already, depending on whether hardware or algorithmic concepts were emphasized.

---

## Noisy World

Up until now, we have only discussed quantum states which were noiseless, meaning they were always in the exact state that we wanted them to be.
There was no uncertainty in our knowledge of the description of the state.
The operations that we used to transform them were perfect too, resulting in perfect outputs.
The world, however, is a noisy place and this description is not quite sufficient for real-world applications.
Let's consider three examples demonstrating why this is the case.

1. **State Preparation:** You may go to your friend who works in a quantum laboratory and ask him or her to prepare a state $\ket{\psi}$. In a real lab, the prepared state is not the desired state $\ket{\psi}$. If you are lucky it might be some other pure state $|\psi'\rangle$ which is close to the desired state $|\psi\rangle$. You would still obtain a pure state, albeit not exactly the one you asked for, but at least you would have full knowledge of this state $|\psi'\rangle$. A much more likely scenario is that your friend in the lab can only produce a distribution of pure states. This means that we obtain some pure state $|\psi_1\rangle$ with probability $p_1$, or a different pure state $|\psi_2\rangle$ with probability $p_2$, and so on. This distribution is often written as $\{p_i, |\psi_i\rangle\}$.

2. **Processing of Information:** In this case, we wish to perform a quantum computation represented by some unitary operator $U$. Even if the input to the computation is an ideal pure state $|\psi\rangle$, the output will not be the desired $U|\psi\rangle$. The output might contain coherent errors, meaning that the applied operation was some other unitary $U'$, giving us the output $U'|\psi\rangle$. The output might be affected by incoherent errors, such as probabilistic Pauli errors, or even relaxation errors.

3. **Quantum Communication:** Consider the case where you prepare a state $|\psi\rangle$, which you would like to send to a friend through a long optical fiber. Even though we do not process the prepared state in any way, optical fibers themselves are sources of noise. The state received by your friend will be affected by coherent and incoherent errors. On top of these, the state may even get lost and never arrive due to various processes such as absorption or scattering in the fiber. Photon loss is a huge headache in quantum communication and we will discuss it in great detail in later chapters.

---

## Outer Product

We have seen in the previous chapter that the inner product of two vector states $|a\rangle$ and $|b\rangle$ is formed by transforming the first ket into a bra and then multiplying them together:

$$\langle a | b\rangle = \begin{pmatrix} a_0^* & a_1^* \end{pmatrix} \begin{pmatrix} b_0 \\ b_1 \end{pmatrix} = a_0^* b_0 + a_1^* b_1$$

What happens when we change the order of multiplication? Let's multiply the ket $|b\rangle$ from the right by the bra $\langle a|$:

$$| b\rangle \langle a | = \begin{pmatrix} b_0 \\ b_1 \end{pmatrix} \begin{pmatrix} a_0^* & a_1^* \end{pmatrix} = \begin{pmatrix} a_0^*b_0 & a_1^*b_0 \\ a_0^*b_1 & a_1^*b_1 \end{pmatrix}$$

By changing the order of multiplication, we obtained a complex matrix. The above product of a ket with a bra, $|b\rangle\langle a|$, is called an **outer product**. It is necessary in order to describe measurements as well as noisy quantum states.

In order to see what the action of an outer product on a state vector is, we will begin with a few simple examples. Let me show you the following outer product, $|0\rangle\langle0|$. The matrix representation of $|0\rangle\langle0|$ is:

$$|0\rangle\langle0| = \begin{pmatrix} 1 \\ 0 \end{pmatrix} \begin{pmatrix} 1 & 0 \end{pmatrix} = \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix}$$

We also know from basic vector algebra that matrices transform vectors into other vectors. Let's apply our example outer product to a general qubit state vector $|\psi\rangle = \alpha|0\rangle + \beta|1\rangle$, where $|\alpha|^2+|\beta|^2=1$:

$$|0\rangle\langle0|\psi\rangle = |0\rangle\langle0| \left( \alpha|0\rangle + \beta|1\rangle \right) = \alpha |0\rangle\underbrace{\langle0|0\rangle}_{=1} + \beta |0\rangle\underbrace{\langle0|1\rangle}_{=0} = \alpha|0\rangle$$

We used the fact that the inner product of a normalized vector with itself is unity, and the orthogonality property of kets $|0\rangle$ and $|1\rangle$. We see that our example outer product induces an interesting transformation of the initial general single-qubit state vector $|\psi\rangle$. It changes the initial state vector into $|0\rangle$, up to a complex constant $\alpha$. We say that $|0\rangle\langle0|$ **projects** onto the state $|0\rangle$, and that the outer product is an example of a **projector**.

Let's have a quick look at the action of $|1\rangle\langle1|$:

$$|1\rangle\langle1| = \begin{pmatrix} 0 \\ 1 \end{pmatrix} \begin{pmatrix} 0 & 1 \end{pmatrix} = \begin{pmatrix} 0 & 0 \\ 0 & 1 \end{pmatrix}$$

Acting with $|1\rangle\langle1|$ on $|\psi\rangle$:

$$|1\rangle\langle1|\psi\rangle = |1\rangle\langle1| \left( \alpha|0\rangle + \beta|1\rangle \right) = \alpha |1\rangle\underbrace{\langle1|0\rangle}_{=0} + \beta |1\rangle\underbrace{\langle1|1\rangle}_{=1} = \beta|1\rangle$$

The outer products $|0\rangle\langle0|$ and $|1\rangle\langle1|$ capture the effect of **projective measurements**. The probabilities of the measurement outcomes can also be readily calculated as the expectation values of the projectors:

$$\langle \psi | 0 \rangle \langle 0 | \psi \rangle = \left( \alpha^*\langle0| + \beta^*\langle1| \right) |0\rangle\langle0| \left( \alpha |0\rangle + \beta |1\rangle \right) = |\alpha|^2$$

$$\langle \psi | 1 \rangle \langle 1 | \psi \rangle = \left( \alpha^*\langle0| + \beta^*\langle1| \right) |1\rangle\langle1| \left( \alpha |0\rangle + \beta |1\rangle \right) = |\beta|^2$$

Projectors corresponding to measurement in the Pauli $X$ basis ($|\pm\rangle$ outcomes) are:

$$|+\rangle\langle+| = \frac{1}{2} \begin{pmatrix} 1 & 1 \\ 1 & 1 \end{pmatrix}, \qquad |-\rangle\langle-| = \frac{1}{2} \begin{pmatrix} 1 & -1 \\ -1 & 1 \end{pmatrix}$$

And for the Pauli $Y$ basis ($|\pm i\rangle$ outcomes):

$$|i\rangle\langle i| = \frac{1}{2} \begin{pmatrix} 1 & -i \\ i & 1 \end{pmatrix}, \qquad |-i\rangle\langle-i| = \frac{1}{2} \begin{pmatrix} 1 & i \\ -i & 1 \end{pmatrix}$$

Sometimes, rather than writing projectors as outer products, we denote them by $\Pi$:

$$\Pi_{\pm}^B \equiv |b_{\pm}\rangle\langle b_{\pm}|$$

| Basis | $+1$ Outcome Projector | $-1$ Outcome Projector |
|---|---|---|
| **Pauli $X$ basis** | $\Pi^X_+ = |+\rangle\langle+|$ | $\Pi^X_- = |-\rangle\langle-|$ |
| **Pauli $Y$ basis** | $\Pi^Y_+ = |i\rangle\langle i|$ | $\Pi^Y_- = |-i\rangle\langle-i|$ |
| **Pauli $Z$ basis** | $\Pi^Z_+ = |0\rangle\langle0|$ | $\Pi^Z_- = |1\rangle\langle1|$ |

We can also **represent quantum states as matrices** written in the form of outer products:

$$|0\rangle\langle0| = \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix}, \quad |+\rangle\langle+| = \frac{1}{2} \begin{pmatrix} 1 & 1 \\ 1 & 1 \end{pmatrix}, \quad |\psi\rangle\langle\psi| = \begin{pmatrix} |\alpha|^2 & \alpha\beta^* \\ \alpha^*\beta & |\beta|^2 \end{pmatrix}$$

States represented purely by vectors or single projectors are called **pure states**.

---

## Density Matrices

When an ideal state travels through noise, the output becomes a probabilistic distribution of states $\{p_i, |\psi_i\rangle\}$. The whole output state can be described as a sum of outer products:

$$\rho = p_1 |\psi_1\rangle\langle\psi_1| + p_2 |\psi_2\rangle\langle\psi_2| + \ldots + p_n |\psi_n\rangle\langle\psi_n| = \sum_i p_i |\psi_i\rangle\langle\psi_i|$$

where $\sum_i p_i = 1$. The state $\rho$ is called a **mixed state**, and this representation is called a **density matrix**.

### Example: Bit-Flip Channel
In a bit-flip channel, Pauli $X$ is applied with probability $p$, and the state is unaffected with probability $1-p$:

$$\rho = (1-p) |\psi\rangle\langle\psi| + p X|\psi\rangle\langle\psi|X$$

* If $|\psi\rangle = |0\rangle$, then $\rho = (1-p)|0\rangle\langle0| + p|1\rangle\langle1| = \begin{pmatrix} 1-p & 0 \\ 0 & p \end{pmatrix}$
* If $|\psi\rangle = |1\rangle$, then $\rho = (1-p)|1\rangle\langle1| + p|0\rangle\langle0| = \begin{pmatrix} p & 0 \\ 0 & 1-p \end{pmatrix}$

### Properties of Density Matrices
1. **Trace Normalization:** The trace of a matrix is the sum of its diagonal elements: $\text{Tr}\{A\} = \sum_i A_{ii}$. A density matrix is normalized when $\text{Tr}\{\rho\} = 1$.
2. **Trace on Outer Products:** $\text{Tr}\{|b\rangle\langle a|\} = \langle a|b\rangle$.
3. **Bloch Sphere Representation:** Pure states lie on the surface of the Bloch sphere, while mixed states lie **inside the Bloch sphere**.
4. **Maximally Mixed State:** The center of the sphere represents the maximally mixed state:

$$\frac{I}{2} = \frac{1}{2} |0\rangle\langle0| + \frac{1}{2} |1\rangle\langle1| = \frac{1}{2} |+\rangle\langle+| + \frac{1}{2} |-\rangle\langle-| = \frac{1}{2} \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$$

---

## Pure vs Mixed States

Consider an equal superposition state $|\psi\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle) = |+\rangle$ and an equal mixture state $\rho = \frac{1}{2}(|0\rangle\langle0| + |1\rangle\langle1|)$:

* **$Z$-basis Measurement:** Both yield $\text{Prob}\{+1\} = \text{Prob}\{-1\} = 1/2$.
* **$X$-basis Measurement:** 
  * Superposition $|\psi\rangle$: $\text{Prob}\{+1\} = 1, \text{Prob}\{-1\} = 0$ (Deterministic).
  * Mixture $\rho$: $\text{Prob}\{+1\} = 1/2, \text{Prob}\{-1\} = 1/2$ (Probabilistic).

### Purity ($\gamma$)
A mathematical criterion to check if a state is pure or mixed is **purity**:

$$\gamma = \text{Tr}\{\rho^2\} \longrightarrow \begin{cases} = 1, & \text{when } \rho \text{ is pure} \\ < 1, & \text{when } \rho \text{ is mixed} \end{cases}$$

| Property | Pure States | Mixed States |
|---|---|---|
| **Notation** | $|\psi\rangle$ | $\rho$ |
| **Represented by** | Vectors or Matrices | Matrices only |
| **Normalization** | $\langle\psi|\psi\rangle = 1$ | $\text{Tr}\{\rho\} = 1$ |
| **Knowledge of the State** | Perfect | Imperfect |
| **Purity ($\gamma$)** | $1$ | $< 1$ |

---

## Fidelity

**Fidelity** quantifies how close a real state $\rho$ is to a target pure state $|\psi\rangle$:

$$F(\rho, |\psi\rangle) = \langle\psi|\rho|\psi\rangle$$

* If $\rho = |\psi\rangle\langle\psi|$ (ideal case), $F = 1$.
* If $\rho$ is pure and orthogonal to $|\psi\rangle$, $F = 0$.
* Generally, $0 \le F(\rho, |\psi\rangle) \le 1$.

### Examples:
1. **Single-Qubit Maximally Mixed State:** $F\left(\frac{I}{2}, |0\rangle\right) = \frac{1}{2}$.
2. **$N$-Qubit Maximally Mixed State:** $F\left(\frac{I}{2^N}, |0\rangle^{\otimes N}\right) = \frac{1}{2^N}$.
3. **Bit-Flip Channel Output ($|\psi\rangle = |0\rangle$):** $F(\rho, |0\rangle) = 1 - p$.

---

## Exercises

**Exercise 1: Single-qubit measurements**  
Consider a general pure state $|\psi\rangle=\alpha|+\rangle+\beta|-\rangle$. Calculate the probabilities $\text{Pr}\{+1\}$ and $\text{Pr}\{-1\}$ when measured in the $X$, $Y$, and $Z$ bases.

*Solution:*
* **$X$-basis:** $\text{Pr}\{+1\} = |\alpha|^2, \text{Pr}\{-1\} = |\beta|^2$.
* **$Y$-basis:** $\text{Pr}\{\pm1\} = \frac{1}{2}[1 \mp 2\text{Im}(\alpha^*\beta)]$.
* **$Z$-basis:** $\text{Pr}\{\pm1\} = \frac{1}{2}[1 \pm 2\text{Re}(\alpha^*\beta)]$.

---

**Exercise 2: Post-measurement state**  
The normalized post-measurement state is $|\psi'\rangle = \frac{\Pi^B_i|\psi\rangle}{\sqrt{\langle\psi|\Pi^B_i|\psi\rangle}}$.
1. Initial state $|\psi\rangle = \alpha|0\rangle + \beta|1\rangle$, measured in $Z$-basis with $+1$ outcome. $\rightarrow |\psi'\rangle = |0\rangle$.
2. Initial state $|\psi\rangle = |0\rangle$, measured in $Y$-basis with $-1$ outcome. $\rightarrow |\psi'\rangle = |-i\rangle$.
3. Initial state $|\psi\rangle = |+\rangle$, measured in $X$-basis. Can we get $-1$? $\rightarrow$ No, probability is zero.

---

**Exercise 3: Projectors in rotated basis**  
Projectors can be written as $\Pi^B_{\pm} = \frac{1}{2}(I \pm B)$.
1. Verify for Pauli matrices: $\frac{1}{2}(I \pm X) = |\pm\rangle\langle\pm|$, $\frac{1}{2}(I \pm Y) = |\pm i\rangle\langle\pm i|$, $\frac{1}{2}(I \pm Z) = |0/1\rangle\langle 0/1|$.
2. For $B = (Z+X)/\sqrt{2}$:
   $$\Pi^B_+ = \frac{1}{2}\left[ I + \frac{Z+X}{\sqrt{2}} \right] = |\lambda_+\rangle\langle\lambda_+|, \quad |\lambda_+\rangle = \cos\frac{\pi}{8}|0\rangle + \sin\frac{\pi}{8}|1\rangle$$
   $$\Pi^B_- = \frac{1}{2}\left[ I - \frac{Z+X}{\sqrt{2}} \right] = |\lambda_-\rangle\langle\lambda_-|, \quad |\lambda_-\rangle = -\sin\frac{\pi}{8}|0\rangle + \cos\frac{\pi}{8}|1\rangle$$
3. For $B = r_x X + r_y Y + r_z Z$:
   $$\Pi^B_+ = \frac{1}{2} \begin{pmatrix} 1 + r_z & r_x - i r_y \\ r_x + i r_y & 1 - r_z \end{pmatrix}, \qquad \Pi^B_- = \frac{1}{2} \begin{pmatrix} 1 - r_z & -(r_x - i r_y) \\ -(r_x + i r_y) & 1 + r_z \end{pmatrix}$$

---

**Exercise 4: Mixed states preparation**  
A machine prepares $|0\rangle$ with 60% probability, $|1\rangle$ with 20%, and $|+\rangle$ with 20%.
1. **Dirac notation:** $\rho = \frac{3}{5}|0\rangle\langle0| + \frac{1}{5}|1\rangle\langle1| + \frac{1}{5}|+\rangle\langle+|$
2. **Matrix form:**
   $$\rho = \begin{pmatrix} \frac{7}{10} & \frac{1}{10} \\ \frac{1}{10} & \frac{3}{10} \end{pmatrix}$$

---

**Exercise 5: Bit-flip channel purity**  
For $\rho = (1-p)|\psi\rangle\langle\psi| + p X|\psi\rangle\langle\psi|X$:
1. **Normalization:** $\text{Tr}\{\rho\} = (1-p)\langle\psi|\psi\rangle + p\langle\psi|X^2|\psi\rangle = 1 - p + p = 1$.
2. **Purity expression:** $\text{Tr}\{\rho^2\} = (1-p)^2 + p^2 + 2p(1-p)\langle X \rangle^2$.
3. **If $|\psi\rangle = |0\rangle$:** $\langle X \rangle = 0 \implies \text{Tr}\{\rho^2\} = (1-p)^2 + p^2 < 1$.
4. **If $|\psi\rangle = |+\rangle$:** $\langle X \rangle = 1 \implies \text{Tr}\{\rho^2\} = 1$ (State remains pure because $|+\rangle$ is an eigenstate of $X$).

---

**Exercise 6: Phase-flip channel**  
For a phase-flip channel $\rho = (1-p)|\psi\rangle\langle\psi| + p Z|\psi\rangle\langle\psi|Z$:
1. States unaffected are eigenstates of $Z$, namely $|0\rangle$ and $|1\rangle$.
2. **Purity:** $\text{Tr}\{\rho^2\} = (1-p)^2 + p^2 + 2p(1-p)\langle Z \rangle^2$.

```
