# Section 4: Entanglement

In this chapter, we will finally learn about **entanglement**: a special and unique feature of quantum mechanics.
We will begin by demonstrating how strange and counter-intuitive entanglement can be.
Then, we will move on to the definition of entangled states.
Following that, we will discuss a particular class of entangled states called "Bell states", which play an important role in quantum communication.
Finally, we will finish by framing entanglement as a resource for computational and communication tasks.

---

## CHSH Game

We begin with a game that will demonstrate just how wonderful and strange entangled states are.
The game is related to a proposal of four scientists named Clauser, Horn, Shimony, and Holt, normally referred to as the **CHSH game**.
It consists of two players, labelled $A$ and $B$, and a referee denoted by $R$.
The rules of the game are the following:

* Referee $R$ generates two random bits, $x, y \in \{0, 1\}$. Bit $x$ is sent to player $A$, and bit $y$ is sent to player $B$.
* Upon receiving the referee's bits, players $A$ and $B$ reply with their own bits. Player $A$ sends back a bit $a$, and player $B$ sends back bit $b$.
* Referee $R$ checks whether the players' bits satisfy the winning condition:

$$x \cdot y = a \oplus b$$

where $\oplus$ represents binary addition (XOR). This concludes a single round of the game.
* The game continues to see what percentage of the rounds the players can win.
* **IMPORTANT:** The players are **not allowed to communicate** once the game has started.

The players cannot communicate in order to make the game interesting, otherwise they would win every single round. Before the game starts, however, they can agree on a common strategy to maximize their winning chances.

| Round | $x$ | $y$ | $a$ | $b$ | $x \cdot y$ | $a \oplus b$ | Result |
|---|---|---|---|---|---|---|---|
| **Round 1** | 0 | 1 | 0 | 1 | 0 | 1 | **Loss** |
| **Round 2** | 0 | 1 | 1 | 1 | 0 | 0 | **Win** |
| **Round 3** | 1 | 1 | 1 | 0 | 1 | 1 | **Win** |

Let's look at the optimal classical strategy. There are four possible input bit pairs: $(0,0)$, $(0,1)$, $(1,0)$, and $(1,1)$.

| $x$ | $y$ | $x \cdot y$ | $a = b$ | $a \oplus b$ | Result |
|---|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 | **Win** |
| 0 | 1 | 0 | 0 | 0 | **Win** |
| 1 | 0 | 0 | 0 | 0 | **Win** |
| 1 | 1 | 1 | 0 | 0 | **Loss** |

If the players always output $a = b = 0$, they win in 3 out of 4 cases. Therefore, the optimal classical strategy yields a **75% winning chance**.

### Quantum Strategy
The players can do better if they share an **entangled state** before the game begins:

$$|\Phi^+\rangle = \frac{1}{\sqrt{2}} (|00\rangle + |11\rangle)$$

* **Player $A$:** If $x = 0$, measure in the $Z$ basis. If $x = 1$, measure in the $X$ basis. Send $a = 0$ for outcome $+1$, and $a = 1$ for outcome $-1$.
* **Player $B$:** If $y = 0$, measure in the $(Z+X)/\sqrt{2}$ basis. If $y = 1$, measure in the $(Z-X)/\sqrt{2}$ basis. Send $b = 0$ for outcome $+1$, and $b = 1$ for outcome $-1$.

By following this quantum strategy, the players achieve a winning probability of **85%** ($\frac{1+\sqrt{2}}{2\sqrt{2}}$), an increase of 10% over any classical strategy.

---

## Entangled States

Let's consider a system of two qubits. We use **local state** to refer to the state of either qubit alone, and **global state** to refer to both qubits together.

For a system where $A$ is in state $|0\rangle$ and $B$ is in state $|+\rangle$, the global state is simply a product state:

$$|\psi\rangle_{AB} = |0\rangle|+\rangle = |0\rangle \left( \frac{|0\rangle + |1\rangle}{\sqrt{2}} \right) = \frac{|00\rangle + |01\rangle}{\sqrt{2}}$$

Now consider the global state $|\Phi^+\rangle_{AB} = \frac{1}{\sqrt{2}}(|00\rangle + |11\rangle)$. Can we express this as a tensor product of general single-qubit states $|\psi\rangle_A = a_0|0\rangle + a_1|1\rangle$ and $|\psi\rangle_B = b_0|0\rangle + b_1|1\rangle$?

$$|\psi\rangle_A \otimes |\psi\rangle_B = a_0 b_0 |00\rangle + a_0 b_1 |01\rangle + a_1 b_0 |10\rangle + a_1 b_1 |11\rangle$$

Comparing coefficients with $|\Phi^+\rangle_{AB}$:

$$a_0 b_0 = a_1 b_1 = \frac{1}{\sqrt{2}}, \qquad a_0 b_1 = a_1 b_0 = 0$$

If $a_0 b_1 = 0$, then either $a_0 = 0$ or $b_1 = 0$. But setting either to 0 makes $a_0 b_0 = 0$ or $a_1 b_1 = 0$, which contradicts the first condition. Thus, **not all global states can be written as a tensor product of local states**.

* **Product States:** Can be written as a tensor product of local states ($|\psi\rangle_A \otimes |\psi\rangle_B$). We have perfect knowledge of both local and global states.
* **Entangled States:** Cannot be written as a tensor product of local states. We have perfect knowledge of the global state, but imperfect knowledge of local states.

---

## Bell States

The four **Bell states** form an orthonormal basis for two-qubit systems:

$$|\Phi^+\rangle = \frac{1}{\sqrt{2}} (|00\rangle + |11\rangle), \qquad |\Phi^-\rangle = \frac{1}{\sqrt{2}} (|00\rangle - |11\rangle)$$

$$|\Psi^+\rangle = \frac{1}{\sqrt{2}} (|01\rangle + |10\rangle), \qquad |\Psi^-\rangle = \frac{1}{\sqrt{2}} (|01\rangle - |10\rangle)$$

Computational basis states expressed in the Bell basis:

$$|00\rangle = \frac{1}{\sqrt{2}}(|\Phi^+\rangle + |\Phi^-\rangle), \qquad |01\rangle = \frac{1}{\sqrt{2}}(|\Psi^+\rangle + |\Psi^-\rangle)$$

$$|10\rangle = \frac{1}{\sqrt{2}}(|\Psi^+\rangle - |\Psi^-\rangle), \qquad |11\rangle = \frac{1}{\sqrt{2}}(|\Phi^+\rangle - |\Phi^-\rangle)$$

A general two-qubit pure state $|\psi\rangle = \alpha|00\rangle + \beta|01\rangle + \gamma|10\rangle + \delta|11\rangle$ in the Bell basis is:

$$|\psi\rangle = \frac{\alpha+\delta}{\sqrt{2}}|\Phi^+\rangle + \frac{\alpha-\delta}{\sqrt{2}}|\Phi^-\rangle + \frac{\beta+\gamma}{\sqrt{2}}|\Psi^+\rangle + \frac{\beta-\gamma}{\sqrt{2}}|\Psi^-\rangle$$

### Bell-Basis Measurement
Measuring a general state $|\psi\rangle$ in the Bell basis yields four outcomes with probabilities:

$$\text{Prob}\{|\Phi^+\rangle\} = \frac{|\alpha+\delta|^2}{2}, \qquad \text{Prob}\{|\Phi^-\rangle\} = \frac{|\alpha-\delta|^2}{2}$$

$$\text{Prob}\{|\Psi^+\rangle\} = \frac{|\beta+\gamma|^2}{2}, \qquad \text{Prob}\{|\Psi^-\rangle\} = \frac{|\beta-\gamma|^2}{2}$$

### Local Reduced States
If we hold only one qubit of an entangled pair $|\Phi^+\rangle$ and measure it locally in *any* basis ($X$, $Y$, or $Z$), outcomes are strictly 50/50 random. The local state of each qubit is a **maximally mixed state**:

$$\rho_A = \frac{1}{2}(|0\rangle\langle 0| + |1\rangle\langle 1|) = \frac{I}{2}, \qquad \rho_B = \frac{1}{2}(|0\rangle\langle 0| + |1\rangle\langle 1|) = \frac{I}{2}$$

---

## Spontaneous Parametric Down-Conversion (SPDC)

**Spontaneous Parametric Down-Conversion (SPDC)** is a nonlinear optical process used to generate entangled photon pairs in laboratories.

1. A high-energy **pump photon** interacts with a nonlinear crystal (e.g., **Beta Barium Borate** / BBO).
2. The pump photon is converted into two lower-energy photons: the **signal** and the **idler**.
3. Conservation of energy requires:

$$E_p = E_s + E_i$$

| System State | Basis States | Equal Superposition | General State |
|---|---|---|---|
| **Qubits** | $\{|0\rangle, |1\rangle\}$ | $|+\rangle$ | $\alpha|0\rangle + \beta|1\rangle$ |
| **Polarized Photons** | $\{|H\rangle, |V\rangle\}$ | $|D\rangle$ | $\alpha|H\rangle + \beta|V\rangle$ |

### Generating Entanglement via SPDC
By placing two thin BBO crystals back-to-back (the second rotated by 90°) and pumping with diagonally polarized light $|D\rangle_p = \frac{1}{\sqrt{2}}(|H\rangle_p + |V\rangle_p)$:

* $|H\rangle_p$ down-converts in the first crystal to $|V\rangle_s |V\rangle_i$.
* $|V\rangle_p$ down-converts in the second crystal to $|H\rangle_s |H\rangle_i$.

When the crystals are thin enough to satisfy the **indistinguishability condition** (path information is erased), an entangled photon pair is generated:

$$|D\rangle_p \longrightarrow \frac{|H\rangle_s |H\rangle_i + |V\rangle_s |V\rangle_i}{\sqrt{2}}$$

---

## Entanglement as a Resource

Entanglement acts as the "fuel" that drives quantum communication and computation protocols:

* **Consumption:** In protocols such as the CHSH game, quantum teleportation, and superdense coding, entangled pairs are **consumed** (destroyed) during measurement.
* **Distribution:** Quantum networks must continuously distribute Bell pairs across nodes to keep protocols running.

---

## Exercises

**Exercise 1: Classical strategies for the CHSH game**  
1. *Random replies:* Players win with probability $1/2 = 50\%$.
2. *Echo replies ($a=x, b=y$):* Players win only 1 out of 4 cases $\rightarrow 25\%$.

---

**Exercise 2: Local measurements on two qubits**  
1. For $|\Phi^+\rangle$, if both players measure in $Z$: possible outcomes are $(+1, +1)$ and $(-1, -1)$ with equal probability $1/2$.
2. For $|\Phi^+\rangle$, if $A$ measures in $Z$ and $B$ measures in $X$: all four outcomes $(+1,+1), (+1,-1), (-1,+1), (-1,-1)$ are equally likely ($1/4$).

---

**Exercise 3: Quantum strategy for CHSH game ($x=0, y=0$)**  
1. Winning condition ($x \cdot y = 0$): $a \oplus b = 0 \implies a = b$.
2. Probability of winning:
   $$p_{\text{win}} = p_{+1,+1} + p_{-1,-1} = \frac{1+\sqrt{2}}{4\sqrt{2}} + \frac{1+\sqrt{2}}{4\sqrt{2}} = \frac{1+\sqrt{2}}{2\sqrt{2}} \approx 0.85$$

---

**Exercise 4: Bell basis properties**  
1. Bell states are mutually orthogonal: $\langle\Phi^+|\Phi^-\rangle = \langle\Phi^+|\Psi^+\rangle = \dots = 0$.
2. $|\psi\rangle = \frac{\alpha+\delta}{\sqrt{2}}|\Phi^+\rangle + \frac{\beta+\gamma}{\sqrt{2}}|\Psi^+\rangle + \frac{\alpha-\delta}{\sqrt{2}}|\Phi^-\rangle + \frac{\beta-\gamma}{\sqrt{2}}|\Psi^-\rangle$.
3. Maximally mixed state:
   $$\frac{1}{4}(I \otimes I) = \frac{1}{4}|\Phi^+\rangle\langle\Phi^+| + \frac{1}{4}|\Psi^+\rangle\langle\Psi^+| + \frac{1}{4}|\Phi^-\rangle\langle\Phi^-| + \frac{1}{4}|\Psi^-\rangle\langle\Psi^-|$$

---

**Exercise 5: Single-qubit vs. Two-qubit measurement statistics**  
1. Measuring $|+\rangle$: $X$-basis gives $\text{Pr}\{+1\}=1$; $Y$ and $Z$ give $1/2$.
2. Measuring qubit $A$ of $|\Phi^+\rangle$: $X$, $Y$, and $Z$ bases all yield $\text{Pr}\{\pm 1\} = 1/2$ (behaves as a maximally mixed state).

---

**Exercise 6: Rate of production of down-converted photons**  
Pump laser power $P = 15\text{ mW}$, $\lambda = 405\text{ nm}$, efficiency = $1\text{ pair per } 10^8\text{ photons}$.

1. Single photon energy: $E_{\text{photon}} = \frac{hc}{\lambda} \approx 4.9 \times 10^{-19}\text{ J}$.
   $$\text{Photons per second} = \frac{P}{E_{\text{photon}}} = \frac{15 \times 10^{-3} \times 405 \times 10^{-9}}{6.626 \times 10^{-34} \times 3 \times 10^8} \approx 3.07 \times 10^{14}\text{ photons/s}$$
2. Entangled pair production rate:
   $$R_{\text{ent}} = 3.07 \times 10^{14} \times 10^{-8} = 3.07 \times 10^6\text{ pairs/s } (3.07\text{ MHz})$$
3. Down-converted photon wavelength (equal energy split): $\lambda = 2 \times 405\text{ nm} = 810\text{ nm}$.
