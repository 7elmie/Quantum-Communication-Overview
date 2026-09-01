# Section 6: Interference

In this chapter, we will discuss the fundamental phenomenon of interference.
Most of you have very likely encountered interference of waves in either water, light or even sound.
We begin this chapter with a mathematical description of what happens when two waves of different frequencies interfere together.
After that, we will move to interference at the quantum level, using single photons.
Finally, we will conclude this chapter by learning that interference can occur at the level of individual qubits as well.

---

## Constructive and Destructive Interference

A good starting point is to settle on the notation that will be used in this chapter.
Let's consider a wave oscillating at a single frequency, and which is propagating in time along a single dimension denoted by coordinate $x$,

$$\Psi(x,t) = A \sin [\omega t-(k x+\phi_0)].$$

We denote the wave with $\Psi(x,t)$.
The ***amplitude***, denoted by $A$, is the maximum value that $\Psi(x,t)$ takes.
It signifies how much the wave is displaced from its rest state.
The symbol $\omega$ (small Greek letter "omega") is the ***angular frequency***, and it determines how quickly the wave propagates in time.
Time is denoted by $t$.
The symbol $k$ is known as the ***wave number***.
It tells us how quickly the wave oscillates in space, and therefore is related to the wavelength of the oscillations.
The wave number also tells us about the direction in which the wave propagates.
Finally, $\phi_0$ (small Greek letter "phi") is called the initial phase of oscillations.
The angular frequency $\omega$, and the wave number $k$, are related to the period of oscillations $T$ and the wavelength $\lambda$, respectively:

$$\omega=\frac{2 \pi}{T}, \qquad k=\frac{2 \pi}{\lambda}.$$

Now is a good time to have a look at some simple examples of the simple wave described above.
Let's freeze the wave at time $t=0$, and for convenience we also set $\phi_0 = 0$, and only vary the wave number $k$.
The blue wave in Fig. 6.1 represents the case when $k=1$, whereas the orange one represents the case when $k=0.5$.
The wavelength is the shortest distance between two points of the wave where it begins to repeat itself.
We can see that halving the wave number $k$ doubles the wavelength.
In other words, increasing the wave number "compresses the oscillations", while decreasing the wave number "stretches" them.

![Same frequency, different wave numbers.](Figures/Chapter06/BW/6-1_wave_number_BW.pdf)

Let's consider what happens when we fix the wave number but we vary the initial phase.
In this case, we have shifted the second wave by an initial phase of $\phi_0=\pi/2$.
Varying the initial phase has the effect of shifting the wave along the $x$ coordinate.
The wavelength of the wave remains unaffected.

![Same wavelength, different initial phase.](Figures/Chapter06/BW/6-1_phase_BW.pdf)

Finally, let's add time dependence into the picture, where we have set the wave number $k=1$, and the initial phase $\phi_0=0$.
The angular frequency of the blue wave is set to $\omega=0.1$.
The figure plots the wave at three different times $t_1$, $t_2$, $t_3$, where $t_1<t_2<t_3$.
The angular frequency of the orange wave is set to $\omega=0.2$.
We observe that the wave is propagating faster as it covers longer distance in the same amount of time.
The wave number $k$ controls the "shape" of the wave, stretching or contracting the oscillations by determining their wavelength.
On the other hand, the angular frequency $\omega$ controls how much the whole wave shifts in time.

![Propagation of waves in time.](Figures/Chapter06/BW/6-1_frequency_BW.pdf)

Having gained some intuition how the various parameters affect the behavior of the wave, it is time to discuss what happens when two waves meet.
Let's consider a special case of two waves, $\Psi_1(x,t)$ and $\Psi_2(x,t)$, each with a different amplitude and initial phase, but both having the same frequency:

$$
\begin{aligned}
\Psi_1(x,t) & = A_1 \sin \left(\omega t+\alpha_1\right), \quad\text{where } \alpha_1=-\left(k x+\phi_1\right), \\
\Psi_2(x,t) & = A_2 \sin \left(\omega t+\alpha_2\right), \quad\text{where } \alpha_2=-\left(k x+\phi_2\right).
\end{aligned}
$$

These two waves produce a new wave given by their sum:

$$\Psi(x,t) = \Psi_1(x,t) + \Psi_2(x,t).$$

This is known as the ***principle of superposition***.
We have in fact encountered this principle in Chapter 2, where we talked about superposition of two quantum state vectors.

The superposition will have the same form as its constituent waves:

$$\Psi(x,t) = A \sin (\omega t-\alpha).$$

The question that we would like to answer is to determine how the amplitudes and initial phases of $\Psi_1(x,t)$ and $\Psi_2(x,t)$ affect the amplitude and the phase of the superposition.
Using the trigonometric identity $\sin (a + b)=\sin a \cos b +\cos a \sin b$, we can rewrite the superposition as:

$$
\begin{aligned}
\Psi(x,t) & = A_1 \left( \sin\omega t \cos\alpha_1 + \cos\omega t \sin \alpha_1 \right) \\
& + A_2 \left( \sin\omega t \cos\alpha_2 + \cos\omega t \sin\alpha_2 \right).
\end{aligned}
$$

We can group the time dependent terms together to obtain:

$$\Psi(x,t) = ( \underbrace{A_1 \cos\alpha_1 + A_2 \cos\alpha_2}_{\equiv A\cos\alpha} ) \sin \omega t + ( \underbrace{A_1 \sin\alpha_1 + A_2 \sin\alpha_2}_{\equiv A\sin\alpha} ) \cos \omega t.$$

We observe that the resulting wave $\Psi(x,t)$ does indeed oscillate with angular frequency $\omega$.
Using the trigonometric identity $\cos^2\theta + \sin^2\theta=1$, and after some rearranging, we obtain the following expression for the square of the amplitude $A$:

$$A^2 = A_1^2 + A_2^2 + 2 A_1 A_2 \cos(\alpha_2-\alpha_1).$$

The phase $\alpha$ can be obtained in the following way:

$$\tan \alpha = \frac{A\sin\alpha}{A\cos\alpha} = \frac{A_1\sin\alpha_1 + A_2\sin\alpha_2}{A_1\cos\alpha_1 + A_2\cos\alpha_2}.$$

The last term in the amplitude equation is known as the ***interference term***.
It oscillates as a function of the phase difference $\delta\equiv\alpha_2 - \alpha_1$, resulting in either positive or negative contribution to the amplitude of $\Psi(x,t)$.
When the phase difference is such that $\cos\delta>1$, the interference term contributes by increasing the amplitude $A$, which is known as ***constructive interference***.
On the other hand, when $\cos\delta<1$, the interference term contributes negatively, a situation known as ***destructive interference***.

Let's look at the example where the amplitudes of the initial two waves are equal, $A_1=A_2$, but their wave numbers are different.
The interference of these two waves with $k_1=1.0$ (blue) and $k_2=0.8$ (orange) is plotted in Fig. 6.5.
The resulting wave $\Psi(x,t)$ is shown in green.
We observe that when the phase difference $\delta$ is small (small $x$), the two waves interfere constructively, reaching almost $2A$.
Where $x$ is large, the interference becomes destructive as the waves go "out of phase".

![Superposition of two waves.](Figures/Chapter06/BW/6-1_interference_wave_numbers_BW.pdf)

---

## Phase and Group Velocities

In this section, we will investigate the speed at which a wave propagates.

***Phase velocity:***
First, let's consider a single wave of a single frequency $\omega$ propagating through space:

$$\Psi(x,t) = A \sin(\omega t - kx - \phi_0),$$

where the phase at a particular point in time $t$ and space $x$ is $\theta(x,t)=\omega t-k x-\phi_0$.
Differentiating the expression for phase with respect to time and setting it equal to zero:

$$\frac{d\theta(x,t)}{d t} = \omega - k\frac{dx}{dt} = 0.$$

The rate of change of the position, $dx/dt$, is called the ***phase velocity***:

$$v_p \equiv \frac{dx}{dt}, \longrightarrow v_p = \frac{\omega}{k}.$$

![Phase velocity.](Figures/Chapter06/BW/6-2_phase_velocity_BW.pdf)

***Group velocity:***
How is the speed of the wave affected when the wave itself is a superposition of multiple single-frequency waves?
Let's consider two interfering waves:

$$\Psi_1(x,t) = A \sin (\omega_1 t - k_1 x), \qquad \Psi_2(x,t) = A \sin (\omega_2 t - k_2 x).$$

Interference of these two waves results in the following superposition:

$$\Psi(x,t) = 2 A \underbrace{\sin \left( \frac{\omega_{1}+\omega_{2}}{2} t-\frac{k_{1}+k_{2}}{2} x \right)}_{\text{fast oscillations}} \underbrace{ \cos \left( \frac{\omega_{1}-\omega_{2}}{2} t-\frac{k_{1}-k_{2}}{2} x \right)}_{\text{slow oscillations}}.$$

![Group velocity.](Figures/Chapter06/BW/6-2_group_velocity_BW.pdf)

The first term captures the fast oscillations at frequency $(\omega_1+\omega_2)/2$, giving the phase velocity:

$$v_p = \frac{\omega_1 + \omega_2}{k_1 + k_2}.$$

The second term captures the slowly-varying envelope with frequency $(\omega_1-\omega_2)/2$, giving rise to ***group velocity***:

$$v_g = \frac{\omega_1 - \omega_2}{k_1 - k_2}.$$

The phase and group velocities of a superposition can be related as:

$$v_p > v_g, \quad v_p = v_g, \quad v_p < v_g.$$

It is the group velocity that tells us how quickly a signal carries information.

![Superposition of more than two waves.](Figures/Chapter06/BW/6-2_superposition_many_BW.pdf)

When we have a superposition of more than two single-frequency components, as pictured in Fig. 6.8, we observe long regions of destructive interference and short ***pulses*** where constructive interference kicks in.
It is these pulses that carry information at the group velocity.

---

## Interference with Single Photons

![Double-slit experiment.](Figures/Chapter06/BW/6-3_double_slit_waves_BW.pdf)

In a double-slit experiment with coherent light, diffraction and interference create an alternating pattern of bright and dark fringes on a screen.
Bright fringes correspond to constructive interference ($\delta = \pm 2\pi n$), while dark fringes correspond to destructive interference ($\delta = \pm \pi n$).

When we attenuate the laser light to single photons:
* If one slit is covered, we observe a diffraction distribution with a broad peak centered behind the open slit.
* If both slits are open, our naive expectation would be the simple sum of distributions from each slit without interference fringes. However, real laboratory experiments show that a clear interference pattern of bright and dark fringes still emerges.

![Single-slit experiment with single photons.](Figures/Chapter06/BW/6-3_double_slit_covered_BW.pdf)

![Naive expectation of double-slit experiment.](Figures/Chapter06/BW/6-3_double_slit_naive_BW.pdf)

Even if we attenuate the incident light further so that only a single photon travels between the screens at any given time, the interference pattern still emerges eventually.
This demonstrates that a single photon interferes with itself, with its multiple possible routes through the slits resulting in certain locations having zero probability of detection.

![Double-slit experiment with single photons.](Figures/Chapter06/BW/6-3_double_slit_photons_BW.pdf)

---

## Interference with Qubits

Consider the action of a Hadamard operation on initial states $\ket{0}$ and $\ket{1}$:

$$|0\rangle = \begin{pmatrix} 1 \\ 0 \end{pmatrix}, \quad |1\rangle = \begin{pmatrix} 0 \\ 1 \end{pmatrix}, \quad H = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}.$$

Applying a Hadamard twice to $\ket{0}$:

$$H\left[\frac{1}{\sqrt{2}}(|0\rangle+|1\rangle)\right] = \frac{1}{2}(|0\rangle+|1\rangle+|0\rangle-|1\rangle) = |0\rangle.$$

Here, both $\ket{0}$ terms have amplitude $+1$ (constructive interference), while $\ket{1}$ terms have amplitudes $+1$ and $-1$ (destructive interference).
It is the ***interference of probability amplitudes*** that determines the state of the qubit.

Consider two transformations (beam splitters BS1 and BS2):

$$\text{BS}1 = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}, \quad \text{BS}2 = \frac{1}{\sqrt{2}}\begin{pmatrix} -1 & 1 \\ 1 & 1 \end{pmatrix}, \quad \text{BS}2 \cdot \text{BS1} \neq I.$$

Applying BS1 followed by BS2 to state $\ket{1}$:

$$\text{BS}2 \cdot \text{BS}1 |1\rangle = -|0\rangle = |0\rangle.$$

This abstract calculation connects directly to the ***Mach-Zehnder interferometer***.

![Mach-Zehnder interferometer.](Figures/Chapter06/BW/6-4_MZ_BW.pdf)

An incident photon has two paths in the interferometer, representing a ***spatially encoded*** qubit:
* Upper path: state $\ket{0}$
* Lower path: state $\ket{1}$

![State |0\rangle in the MI interferometer.](Figures/Chapter06/BW/6-4_MZ_ket_0_BW.pdf)

![State |1\rangle in the MI interferometer.](Figures/Chapter06/BW/6-4_MZ_ket_1_BW.pdf)

A photon entering the bottom port of BS1 passes through BS1 and BS2, resulting in constructive and destructive interference such that it is always detected by detector D0 and never by D1.
If we block the lower path with an absorbing material, interference is prevented, and a photon has a 50/50 chance of being detected by either D0 or D1.

![Lower path blocked.](Figures/Chapter06/BW/6-4_MZ_blocked_BW.pdf)

---

## Exercises

### Exercise 1: Visualization of wave propagation
Significant portions of this Chapter discuss propagation of waves in time. This exercise gives you the opportunity to write basic code to create an animation depicting interference of two waves in time.
* (a) Begin by replicating Fig. 6.4. Choose any two sinusoidal waves to clearly see fast and slow oscillations.
* (b) Create an animation showing how interference propagates in time.
* (c) Mark a point of constant phase and a point on the envelope. Which point has higher velocity?
* (d) Demonstrate cases clearly: $v_p>v_g$, $v_p=v_g$, $v_p<v_g$.
* (e) Find parameters such that the phase velocity is negative, $v_p<0$.

### Exercise 2: Single-qubit interference
Consider the Mach-Zehnder interferometer.
* (a) Show that BS1 and BS2 are not hermitian conjugates, $\text{BS}1\cdot\text{BS}2\neq I$.
* (b) What are the detection probabilities for D0 and D1 if input state is $(|0\rangle + |1\rangle)/\sqrt{2}$?
* (c) How can you physically implement such an input state?

### Exercise 3: Destroying the interference
Interference at BS2 can be destroyed by placing an obstacle (or another detector D2) in one arm of the Mach-Zehnder interferometer.
* (a) What is the state of the qubit immediately after BS1?
* (b) What is the probability of detector D2 detecting a photon?
* (c) What is the state of the qubit given that detector D2 did not click?
* (d) What are the individual click probabilities for the three detectors?
* (e) If we input a photon in the top port of BS1, where is it most likely going to be detected?


