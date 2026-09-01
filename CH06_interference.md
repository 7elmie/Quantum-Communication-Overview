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


