# Section 2: Quantum States

In this chapter, we will learn about quantum states: how to write them down, what they represent, and how they differ from classical states.
Then, we will learn how to operate on and extract information from quantum states using unitary operations and measurements.
Lastly, we will discuss multiple quantum states and how to describe them.
Most of this chapter will be familiar to those who have taken an introductory quantum computing course.

# Qubits

First, let's discuss quantum bits, also known as qubits.
We have seen in the previous chapter that information can be represented by classical bits.
In the classical world, a classical bit can only be in two states:
it can be in a state we label *zero*, or in a state we label *one*, nothing in between.
In contrast, a quantum bit can be anything in between.
It can be 100% zero or 100% one, but it can also be 50% zero and 50% one or 1% zero and 99% one.
Such a state is called a **superposition** of zero and one.
It's not that we don't know what the state is, it really is neither zero nor one but it's somewhere in between.
(This notion of "in between" is not a completely accurate description, but it will do for now.
As we do the mathematics over the next several sections, your understanding will grow.)

The most common notation for writing down the state of a qubit (or more than one qubit) is called the **Dirac notation**, and it's extremely useful.
A general superposition of a qubit can be written as:

$$\vert{}\psi\rangle = \alpha \vert{}0\rangle + \beta \vert{}1\rangle$$

The funny angle bracket notation is called a **ket**.
The Greek letter $\psi$ in a ket, which we will call "state psi" or "ket psi" interchangeably, is often used to describe a general state of a qubit.
$\ket{0}$ and $\ket{1}$ are called the **basis states**, and they determine what our state is.
The parameters $\alpha$ and $\beta$ are **probability amplitudes** that tell us how much of the state is in zero and how much of the state is in one.
These probability amplitudes can be any complex numbers, provided that they satisfy the following **normalization condition**:

$$\vert{}\alpha\vert{}^2 + \vert{}\beta\vert{}^2 = 1$$

This should be read as "mod alpha squared plus mod beta squared is equal to one".
This condition ensures that whatever measurements we do in the future on this state produce results with the correct probabilities.

Another very useful representation of quantum states is using the **Bloch sphere**. This visual representation gives us a very intuitive way of thinking about quantum states. All the pure states are given as points on the surface of the sphere, parameterized by the angle $\theta$ and the angle $\phi$. Then the state $\ket{\psi}$ can be written in the following form:

$$\vert{}\psi\rangle = \cos \frac{\theta}{2}\vert{}0\rangle + e^{i \phi} \sin \frac{\theta}{2}\vert{}1\rangle$$

where the probability amplitude for basis state 0 is given by $\cos(\theta/2)$ and the probability amplitude for basis state 1 is given by $\sin(\theta/2)$, multiplied by $e^{i \phi}$, known as the **complex phase** of the state. This phase does not affect the probability of finding a one when we measure the qubit, but it is critically important as part of the state and in quantum algorithms.

This $\ket{\psi}$ is a general state, but let's look at some examples. We have already encountered $\ket{0}$ and $\ket{1}$, and they sit at the north and the south pole of the Bloch sphere, respectively. We also said that we can have an arbitrary superposition of zero and one. For example, we can have a state known as the **plus state**, written $\ket{+}$, which is an equal superposition of zero and one. The plus state appears on the equator of the Bloch sphere, at the point where the sphere's positive $X$ axis intersects the surface. We can have its friend the **minus state**, written $\ket{-}$, on the other side of the Bloch sphere. It also is an equal superposition, but this time it's on the negative side of the $X$ axis. If you think about a rotation about the $Z$ along the equator, since $e^{i\pi} = -1$, it has the complex phase $\pi$. We can also have two states on the $Y$ axis. One is called the "plus i" state, written $\ket{i}$ or occasionally $\ket{+i}$, and the other is called "minus i", written $\ket{-i}$. You can see that again, both of these states are an equal superposition of zero and one, but this time the phase between zero and one is given by the complex number $i$ or the angle $\pi/2$ for $\ket{i}$ and $-i$ or the angle $3\pi/2$ for $\ket{-i}$. Summarizing, these states are:

$$\vert{}\pm\rangle = \frac{1}{\sqrt{2}}(\vert{}0\rangle \pm \vert{}1\rangle), \qquad \vert{}\pm i\rangle = \frac{1}{\sqrt{2}}(\vert{}0\rangle \pm i\vert{}1\rangle)$$

---

## Unitary Operations

Let's see how we can manipulate quantum states, and therefore manipulate quantum information as well. We're going to do this with **unitary operations**. One thing that you have to realize is that **information is physical** (an aphorism coined by Rolf Landauer of IBM). This is because the information is represented by physical systems. Therefore, to change the information and process it, we have to interact with the physical systems that carry the information. In classical information, of course the primary processing technology is transistors manufactured using a photolithography process. Computational states are represented using electrical charge, and information processing is done by using charge to control whether a switch is on or off, allowing charge to move from place to place within a computer chip. Another very good example is HDDs (hard disk drives), where you read, write and manipulate information with very weak and precise magnetic fields. For an example of a younger technology, we can look at the solid-state drive where you achieve the same thing by manipulating very weak electric currents.

In quantum information, on the other hand, we have physical systems such as **ion traps**, from companies such as IonQ and Quantinuum. The atoms are suspended on magnetic fields and they represent individual quantum bits. To manipulate the states of these qubits, you apply laser pulses. One of the most prominent forms of qubits is **superconducting qubits** from companies such as IBM and Google, where microwave pulses manipulate the state of a quantum of electrical current.

But how do we actually describe these transformations? Before giving a more complete mathematical description, let me show you some simple examples:

| Operation | Notation | Quantum Transformation | Classical Transformation |
| --- | --- | --- | --- |
| **Identity** *(do nothing)* | $I$ | $\vert{}0\rangle \rightarrow \vert{}0\rangle$<br>

<br>$\vert{}1\rangle \rightarrow \vert{}1\rangle$ | $0 \rightarrow 0$<br>

<br>$1 \rightarrow 1$ |
| **Pauli $X$** *(bit flip)* | $X$ | $\vert{}0\rangle \rightarrow \vert{}1\rangle$<br>

<br>$\vert{}1\rangle \rightarrow \vert{}0\rangle$ | $0 \rightarrow 1$<br>

<br>$1 \rightarrow 0$ |
| **Hadamard** *(create superposition)* | $H$ | $\vert{}0\rangle \rightarrow \frac{\vert{}0\rangle + \vert{}1\rangle}{\sqrt{2}}$<br>

<br>$\vert{}1\rangle \rightarrow \frac{\vert{}0\rangle - \vert{}1\rangle}{\sqrt{2}}$ | N/A |

The simplest transformation that we can think of is actually to do nothing. We call this the **identity operation**, represented by $I$. Another basic operation is the **Pauli $X$ operation**, often called the "flip". It takes $\ket{0}$ to $\ket{1}$ and vice versa. The third operation in the table, the **Hadamard operation** ($H$), creates superpositions. This is the first example of a quantum operation that doesn't really have a classical analog.

All of these examples are **unitary operations**. Any unitary operation has the property of being **reversible**, meaning we can undo its effect on our data and return to the original input state. This is done by what's known as an **adjoint operator**, denoted as $U^\dagger$ (read "U dagger") where $U$ is the unitary.

Let's see how that works. We start with a ket $\ket{\psi}$ and we apply a unitary that transforms it into a completely new ket $\ket{\psi'}$. Then, if we apply the adjoint, we end up back again at the state $\ket{\psi}$:

$$\vert{}\psi'\rangle = U\vert{}\psi\rangle \implies \vert{}\psi\rangle = U^{\dagger}\vert{}\psi'\rangle = U^{\dagger}U\vert{}\psi\rangle$$

We can also perform similar operations starting from the other expression:

$$\vert{}\psi'\rangle = U\vert{}\psi\rangle = UU^{\dagger}\vert{}\psi'\rangle$$

From these equations, we can see that $UU^\dagger$ must be equal to the identity operator, and also $U^\dagger U$ must be equal to the identity. In fact, this becomes precisely our definition of a unitary operation:

$$UU^{\dagger} = U^{\dagger}U = I$$

### Matrix Representation

So far we have been talking about states as kets, but a ket is shorthand for a vector, and we transform vectors by multiplying them by matrices. Therefore, unitary operations can be represented by matrices.

First, let's see how kets for states become vectors:

$$\ket{0} \equiv \begin{pmatrix} 1 \\ 0 \end{pmatrix}, \qquad \ket{1} \equiv \begin{pmatrix} 0 \\ 1 \end{pmatrix}$$

Any general state $\ket{\psi}$ can be represented as:

$$\ket{\psi} = \alpha\begin{pmatrix} 1 \\ 0 \end{pmatrix} + \beta\begin{pmatrix} 0 \\ 1 \end{pmatrix} = \begin{pmatrix} \alpha \\ \beta \end{pmatrix}$$

Now let's look at examples of matrices representing unitary operations. The identity operator $I$ is:

$$I = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$$

An important set of operations we will use many times is known as the set of **Pauli operators**:

$$X = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}, \quad Y = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}, \quad Z = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}$$

We also have the Hadamard operator:

$$H = \frac{1}{\sqrt{2}}\begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}$$

Let's see an example of applying the Pauli $X$ operator to $\ket{0}$:

$$X\vert{}0\rangle = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}\begin{pmatrix} 1 \\ 0 \end{pmatrix} = \begin{pmatrix} 0 \\ 1 \end{pmatrix} = \vert{}1\rangle$$

To create a superposition, take the Hadamard operator and apply it to the state $\ket{0}$:

$$H\vert{}0\rangle = \frac{1}{\sqrt{2}}\begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}\begin{pmatrix} 1 \\ 0 \end{pmatrix} = \frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ 1 \end{pmatrix} = \frac{1}{\sqrt{2}}(\vert{}0\rangle + \vert{}1\rangle) = \vert{}+\rangle$$

Notice that the factor $1/\sqrt{2}$ in the Hadamard operator ensures that the output state is properly normalized, since $\vert{}1/\sqrt{2}\vert{}^2 + \vert{}1/\sqrt{2}\vert{}^2 = 1$.

### Calculating the Adjoint

How can we systematically find the adjoint $U^\dagger$ of an operator given its matrix $U$? It takes two simple steps:

1. **Complex Conjugate:** Replace every element with its complex conjugate (where $(x+iy)^* = x-iy$).
2. **Transpose:** Swap the rows and columns (exchange off-diagonal elements).

$$U = \begin{pmatrix} U_{00} & U_{01} \\ U_{10} & U_{11} \end{pmatrix} \longrightarrow \begin{pmatrix} U_{00}^{*} & U_{01}^{*} \\ U_{10}^{*} & U_{11}^{*} \end{pmatrix} \longrightarrow \begin{pmatrix} U_{00}^{*} & U_{10}^{*} \\ U_{01}^{*} & U_{11}^{*} \end{pmatrix} = U^{\dagger}$$

For example, for the Pauli $Y$ matrix:

$$Y = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix} \longrightarrow \begin{pmatrix} 0 & i \\ -i & 0 \end{pmatrix} \longrightarrow \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix} = Y$$

When the adjoint of a matrix is equal to the matrix itself ($U^\dagger = U$), we say that the operator is **self-adjoint** (or Hermitian).

### Rotations on the Bloch Sphere

Another very important class of unitary operations are **rotations**. The rotation operator around an arbitrary unit vector $\hat{n} = (n_x, n_y, n_z)$ by an angle $\theta$ is defined as:

$$R_{\hat{n}}(\theta) = e^{-i \theta \hat{n} \cdot \hat{\sigma} / 2}$$

where $\hat{\sigma} = (X, Y, Z)$ is the vector of Pauli matrices. Expanding the exponent gives:

$$R_{\hat{n}}(\theta) = \cos \frac{\theta}{2} I - i \sin \frac{\theta}{2}\left(n_{x} X + n_{y} Y + n_{z} Z\right)$$

In the Bloch sphere representation, this operation rotates the state vector around the $\hat{n}$ axis by angle $\theta$:

$$R_{\hat{n}}(\theta)\vert{}\psi\rangle = \vert{}\psi'\rangle$$

For example, a rotation around the $Y$-axis by an angle $\pi/2$ applied to $\ket{0}$ yields:

$$R_y(\pi / 2)\ket{0} = \ket{+}$$

*(Note: Although this rotation takes $\ket{0}$ to $\ket{+}$, the Hadamard gate $H$ is not a $\pi/2$ rotation around the $Y$-axis; instead, $H$ corresponds to a $\pi$ rotation about the axis $(X+Z)/\sqrt{2}$.)*

---

## Measurement

Now, let's consider measurements and how they extract information from qubits. A measurement asks the question: *is my qubit in the state $\ket{0}$ or is it in the state $\ket{1}$?*

When measuring a general state $\ket{\psi} = \alpha\ket{0} + \beta\ket{1}$ in the computational basis ($Z$-basis), there are two possible outcomes, usually assigned values $+1$ and $-1$:

$$\operatorname{Prob}\{+1\} = \vert{}\alpha\vert{}^2 \longrightarrow \textrm{state collapses to } \vert{}0\rangle$$

$$\operatorname{Prob}\{-1\} = \vert{}\beta\vert{}^2 \longrightarrow \textrm{state collapses to } \vert{}1\rangle$$

Immediately after measurement, the state **collapses** onto either $\ket{0}$ or $\ket{1}$.

### Measuring in Different Bases

We can also measure in another basis, such as the Pauli $X$ basis, asking whether the state is in $\ket{+}$ or $\ket{-}$. We express $\ket{\psi}$ using the identities:

$$\vert{}0\rangle = \frac{1}{\sqrt{2}}(\vert{}+\rangle + \vert{}-\rangle), \qquad \vert{}1\rangle = \frac{1}{\sqrt{2}}(\vert{}+\rangle - \vert{}-\rangle)$$

Substituting these into $\ket{\psi}$ gives:

$$\vert{}\psi\rangle = \frac{\alpha+\beta}{\sqrt{2}}\vert{}+\rangle + \frac{\alpha-\beta}{\sqrt{2}}\vert{}-\rangle$$

The probabilities for the outcomes in the $X$-basis are:

$$\operatorname{Prob}\{+1\} = \frac{\vert{}\alpha+\beta\vert{}^2}{2} \longrightarrow \textrm{state becomes } \vert{}+\rangle$$

$$\operatorname{Prob}\{-1\} = \frac{\vert{}\alpha-\beta\vert{}^2}{2} \longrightarrow \textrm{state becomes } \vert{}-\rangle$$

Similarly, in the Pauli $Y$ basis ($\ket{i}$ and $\ket{-i}$), where:

$$\vert{}i\rangle = \frac{1}{\sqrt{2}}\begin{pmatrix}1 \\ i\end{pmatrix}, \qquad \vert{}-i\rangle = \frac{1}{\sqrt{2}}\begin{pmatrix}1 \\ -i\end{pmatrix}$$

the state is rewritten as:

$$\vert{}\psi\rangle = \frac{\alpha - i \beta}{\sqrt{2}}\vert{}i\rangle + \frac{\alpha + i \beta}{\sqrt{2}}\vert{}-i\rangle$$

### Inner Product and Bras

The **inner product** measures the overlap (similarity) between two quantum states. Given a state $\ket{\psi}$, its corresponding **bra** $\bra{\psi}$ is defined as its adjoint:

$$\langle\psi\vert{} = (\vert{}\psi\rangle)^{\dagger} = \begin{pmatrix} \alpha \\ \beta \end{pmatrix}^{\dagger} = \begin{pmatrix} \alpha^{*} & \beta^{*} \end{pmatrix}$$

The inner product between $\vert{}\phi\rangle = \gamma\vert{}0\rangle + \delta\vert{}1\rangle$ and $\vert{}\psi\rangle = \alpha\vert{}0\rangle + \beta\vert{}1\rangle$ is:

$$\langle\phi \mid \psi\rangle = \begin{pmatrix} \gamma^{*} & \delta^{*} \end{pmatrix}\begin{pmatrix} \alpha \\ \beta \end{pmatrix} = \alpha \gamma^{*} + \beta \delta^{*}$$

Note that $\langle\psi\vert{}\phi\rangle = (\langle\phi\vert{}\psi\rangle)^*$. If $\langle\phi\vert{}\psi\rangle = 0$, the two states are **orthogonal**. For a normalized state, $\langle\psi\vert{}\psi\rangle = 1$.

Using inner products, the probability of obtaining an outcome corresponding to a basis state $\vert{}b_k\rangle$ when measuring $\vert{}\psi\rangle$ is given by:

$$\operatorname{Prob}\{k\} = \vert{}\langle b_k \mid \psi\rangle\vert{}^2$$

---

## Probabilities, Expectation, and Variance

A single measurement (**single-shot measurement**) yields only a single result ($+1$ or $-1$) and destroys the quantum superposition. To extract the underlying probabilities, we must measure many identical copies of state $\ket{\psi}$.

If we perform $N$ total measurements resulting in $N(+1)$ positive outcomes and $N(-1)$ negative outcomes:

$$\frac{N(+1)}{N(+1)+N(-1)} \approx \vert{}\alpha\vert{}^{2}, \qquad \frac{N(-1)}{N(+1)+N(-1)} \approx \vert{}\beta\vert{}^{2}$$

### Expectation Value

The **expectation value** of measuring in the Pauli $Z$ basis is:

$$\mathbb{E}[Z] = \operatorname{Prob}\{+1\} \cdot (+1) + \operatorname{Prob}\{-1\} \cdot (-1) = \vert{}\alpha\vert{}^{2} - \vert{}\beta\vert{}^{2}$$

In Dirac notation, we write the expectation value of an operator $M$ as:

$$\langle M \rangle = \langle\psi\vert{}M\vert{}\psi\rangle$$

For Pauli $Z$:

$$\langle Z \rangle = \begin{pmatrix} \alpha^* & \beta^* \end{pmatrix} \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix} \begin{pmatrix} \alpha \\ \beta \end{pmatrix} = \vert{}\alpha\vert{}^2 - \vert{}\beta\vert{}^2$$

### Variance and Fluctuations

The variance of a measurement operator $Z$ is defined as:

$$\operatorname{Var}[Z] = \mathbb{E}[Z^2] - \mathbb{E}[Z]^2 = \langle Z^2 \rangle - \langle Z \rangle^2$$

Since $Z^2 = I$, we have $\langle Z^2 \rangle = \langle\psi\vert{}I\vert{}\psi\rangle = 1$. Therefore:

$$(\Delta Z)^2 \equiv \operatorname{Var}[Z] = 1 - \langle Z \rangle^2$$

---

## Multiple Qubits

A two-qubit system has four basis states: $\ket{00}$, $\ket{01}$, $\ket{10}$, and $\ket{11}$. A general two-qubit quantum state is a superposition:

$$\vert{}\psi\rangle = \alpha\vert{}00\rangle + \beta\vert{}01\rangle + \gamma\vert{}10\rangle + \delta\vert{}11\rangle$$

with the normalization condition $\vert{}\alpha\vert{}^2 + \vert{}\beta\vert{}^2 + \vert{}\gamma\vert{}^2 + \vert{}\delta\vert{}^2 = 1$. In vector notation:

$$\ket{00} = \begin{pmatrix} 1 \\ 0 \\ 0 \\ 0 \end{pmatrix}, \quad \ket{01} = \begin{pmatrix} 0 \\ 1 \\ 0 \\ 0 \end{pmatrix}, \quad \ket{10} = \begin{pmatrix} 0 \\ 0 \\ 1 \\ 0 \end{pmatrix}, \quad \ket{11} = \begin{pmatrix} 0 \\ 0 \\ 0 \\ 1 \end{pmatrix} \implies \ket{\psi} = \begin{pmatrix} \alpha \\ \beta \\ \gamma \\ \delta \end{pmatrix}$$

### Tensor Product

Multi-qubit states are constructed using the **tensor product** ($\otimes$). Given two single-qubit states $\vert{}a\rangle = (a_1, a_2)^T$ and $\vert{}b\rangle = (b_1, b_2)^T$:

$$\vert{}a\rangle \otimes \vert{}b\rangle = \begin{pmatrix} a_1 \\ a_2 \end{pmatrix} \otimes \begin{pmatrix} b_1 \\ b_2 \end{pmatrix} = \begin{pmatrix} a_1 \begin{pmatrix} b_1 \\ b_2 \end{pmatrix} \\ a_2 \begin{pmatrix} b_1 \\ b_2 \end{pmatrix} \end{pmatrix} = \begin{pmatrix} a_1 b_1 \\ a_1 b_2 \\ a_2 b_1 \\ a_2 b_2 \end{pmatrix}$$

The tensor product symbol is often omitted: $\vert{}a\rangle \otimes \vert{}b\rangle = \vert{}a\rangle\vert{}b\rangle = \vert{}ab\rangle$.

### Multi-Qubit Operators

For operators $A$ and $B$ acting on the first and second qubits respectively:

$$A \otimes B = \begin{pmatrix} A_{11} & A_{12} \\ A_{21} & A_{22} \end{pmatrix} \otimes \begin{pmatrix} B_{11} & B_{12} \\ B_{21} & B_{22} \end{pmatrix} = \begin{pmatrix} A_{11}B & A_{12}B \\ A_{21}B & A_{22}B \end{pmatrix}$$

When applying $A \otimes B$ to a joint state $\vert{}a\rangle \otimes \vert{}b\rangle$:

$$(A \otimes B)(\vert{}a\rangle \otimes \vert{}b\rangle) = (A\vert{}a\rangle) \otimes (B\vert{}b\rangle)$$

For example, applying Pauli $X$ to the first qubit and doing nothing ($I$) to the second qubit of a general state $\ket{\psi}$:

$$(X \otimes I)(\alpha\vert{}00\rangle + \beta\vert{}01\rangle + \gamma\vert{}10\rangle + \delta\vert{}11\rangle) = \alpha\vert{}10\rangle + \beta\vert{}11\rangle + \gamma\vert{}00\rangle + \delta\vert{}01\rangle$$

---

## Exercises

**Exercise 1**

Consider the state $\ket{\psi} = \frac{\sqrt{3}}{2}\ket{0} + \frac{1}{2}\ket{1}$.

1. Find the probability of measuring $\ket{0}$.
2. Find the probability of measuring $\ket{1}$.

*Solution:*

1. $P(0) = \vert{}\langle 0\vert{}\psi \rangle\vert{}^2 = \left\vert{}\frac{\sqrt{3}}{2}\right\vert{}^2 = \frac{3}{4}$
2. $P(1) = \vert{}\langle 1\vert{}\psi \rangle\vert{}^2 = \left\vert{}\frac{1}{2}\right\vert{}^2 = \frac{1}{4}$

---

**Exercise 2**

Write out the column vectors for the following tensor products:

1. $\ket{+}\ket{1}$
2. $\ket{1}\ket{+}$
3. $\ket{-}\ket{+}$

*Solution:*

1. $\frac{1}{\sqrt{2}} \begin{pmatrix} 0 & 1 & 0 & 1 \end{pmatrix}^T$
2. $\frac{1}{\sqrt{2}} \begin{pmatrix} 0 & 0 & 1 & 1 \end{pmatrix}^T$
3. $\frac{1}{2} \begin{pmatrix} 1 & 1 & -1 & -1 \end{pmatrix}^T$

---

**Exercise 3**

Find the expectation value $\langle Z \rangle$ for the state $\ket{\psi} = \frac{\sqrt{3}}{2}\ket{0} + \frac{1}{2}\ket{1}$.

*Solution:*

$$\langle Z \rangle = \vert{}\alpha\vert{}^2 - \vert{}\beta\vert{}^2 = \left(\frac{\sqrt{3}}{2}\right)^2 - \left(\frac{1}{2}\right)^2 = \frac{3}{4} - \frac{1}{4} = \frac{1}{2}$$
