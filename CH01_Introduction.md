# Section 1: Introduction

## Introduction

In this chapter, we will give you an overview of how communication has evolved over the many thousands of years of human culture and civilization, then we will tell you about sending signals between parties of a network.
We will tell you the differences and similarities between digital and analog signals.
We will introduce the fundamental building block of modern communication, the **bit**.
We will move on to quantum communication and explain why you should care about it, what new capabilities that it brings to the table, and what the new challenges are that face us in designing quantum communication systems.
We will move on to the disruptive nature of quantum technologies and quantum communication in particular.
We will conclude this chapter by giving you an overview of the entire module, what the prerequisites are, what you will learn, and the outcomes of the module.

## History of Communication

Methods of communication advance in order to accommodate a growing society while new technological advances allow society to grow and expand.

<img width="1536" height="1024" alt="phone" src="https://github.com/user-attachments/assets/db0505a0-4922-4c16-8f47-e6db0e626d2b" />

Humans are social creatures by nature.
Effective communication has been crucial to our survival; in particular, it has been very important to share information about potential new sources of food and danger.
We communicated by gathering around the fire and talking to each other.
Over many thousands of years, the methods of communication have evolved to become more efficient and longer ranging until we have finally reached our modern age where nearly every device that we have in our possession, our phones, our TVs, our iPads, even our fridges are all connected to a massive internetwork, the Internet.
We can be separated by many thousands of kilometers, but when we communicate it almost feels as if we are all sharing the same fire like in the old times.
We have gone from local communication to truly global communication.

Let's see how such a massive transformation happened. In the next couple of paragraphs, you are going to see some famous examples from history illustrating the many different ways in which we have communicated.

After the invention of paper (or papyrus, parchment or vellum), the most obvious way was to take your message, write it on a piece of paper and send the message directly.

A very famous example of this method comes from Ancient Egypt. Around 3000 BC, the Pharaoh Djedkara Isesi is credited with establishing the world's first known courier service, expanding it across Egypt and into neighboring lands.

His couriers carried messages mostly by boat along the Nile, but also on foot along known desert routes, covering the full length of the kingdom, a distance of roughly 2,500 kilometers.
Messages were either memorized by the courier or written on sealed papyrus scrolls to protect their contents, and for important documents a duplicate was kept behind by the sender as a backup.
These couriers were valued so highly that some Pharaohs had them depicted on the walls of their tombs.
Later, in the New Kingdom, royal couriers used horse-drawn chariots to move even faster across the kingdom, with dedicated relay stations along the way where a tired courier and horse could be exchanged for a fresh pair, much like the American Pony Express that would appear thousands of years later.

But before we get to this revolution in communication technology, let's talk about these different ways of sending a message. A written letter can carry a fairly detailed and nuanced message.
However, sending a message directly in the form of a written letter is generally slow and suffers from reliability issues.
You may lose your papyrus scroll, or your courier may become exhausted and just give up the task.
If this happens you have to find another courier and resend the message, provided that you are even aware that the message has not been delivered yet.

An alternative to direct transmission was optical telegraphy. This is an old but ingenious method where the sender and the receiver share some pre-agreed signals. The sender uses some optical means in order to generate these signals such that the receiver can see them.
A very good example of this comes once again from **Ancient Egypt**.
During the **Middle Kingdom**, the **Pharaoh Senusret III** built a chain of massive mudbrick fortresses along the Nile in Lower Nubia, near the Second Cataract, at sites such as **Semna, Kumma, and Buhen**.
These fortresses doubled as watchtowers, positioned within sight of one another across the river, and likely used simple visual signals, such as smoke by day or fire by night, to warn neighboring forts of approaching boats or raiders from the desert.
As with any fire-based signal, the expressibility of this communication method was limited. Only certain messages could be sent, such as whether a threat had been spotted or not, or whether the fire was burning or not. One could extend this method a little further by lighting additional fires, so that the number of fires lit indicated the scale of the threat.

Despite this limited expressiveness, the system was efficient at giving early warning.
But for messages that needed far more detail than a signal fire could convey, the Nubian fortresses also relied on written reports, known today to Egyptologists as the **Semna Despatches**.
These were papyrus documents written by officials stationed at the frontier, recording in detail the movement of traders, patrols, and travelers around the fortresses.
They were carried by messenger back down the Nile to an official in the capital, Thebes, several hundred kilometers to the north.
Unlike a simple signal fire, a written despatch could convey an essentially unlimited variety of messages, at the cost of taking much longer to arrive.

As you can imagine, this dual approach also had its drawbacks. The fire-signal system required direct visual contact between fortresses, so it worked reliably only during the day and in clear weather, while a written despatch, however detailed, was only as fast as the messenger carrying it downriver.

This brings us finally to the advent of electrical telegraphy and the invention of the Morse code, which used electric signals to transmit messages and made both courier networks and fortress signal fires obsolete almost overnight. It worked by encoding the letters of the alphabet into a series of **dots and dashes**, as seen below.

<img width="447" height="447" alt="morse-code" src="https://github.com/user-attachments/assets/e9341dde-370e-4633-bb12-060f29a83b02" />

An operator used a telegraph key to close an electric circuit to produce a signal of desired length. Closing the electric circuit for a short time produced a **dot**, while keeping the circuit closed for a longer time produced a **dash**. If the length of a dot is one unit, then a dash has length of 3 units. Parts of the same letter are separated by 1 unit. Different letters are separated by a space of 3 units while different words are separated by 7 units. A skilled operator could transmit up to 30 words per minute, which were decoded by an operator at a distant telegraph station and passed onto the intended recipient. This communication method allowed for messages to be delivered across greater lengths, spanning continents within minutes, making direct communication and optical telegraphy obsolete.

Eventually, the electrical telegraph gave way to the **telephone**, which implemented the dream of communication between humans using the human voice. Early telephone connections were simple point to point. As the demand for communicating via the telephone grew, it became clear the **all-to-all** approach would not work. Imagine a network of telephones where all of them are directly connected to each other. Consider adding a new telephone to the network. In order for the new user to be able to call any of the existing telephones on the network, we have to add a physical connection to each of the existing telephones. Adding yet another telephone would require yet more connections. The all-to-all approach is intuitive but simply does not scale with the size of the network.

The solution came with the introduction of a switchboard. In order to call anybody on the network, each unit had to be connected only to the switchboard. You first called the switchboard, which would then connect you to the desired telephone unit. With this approach, adding a new telephone to the network required adding a single connection to the switchboard, presenting a **constant scaling**. In other words, the effort of adding new users to the network did not increase with the size of the network. Eventually, switchboards of different networks were interconnected together, allowing users from one network to call users on an entirely different network.

The Internet that our society has come to depend on so much works on the same principle. It is not a single network but a **network of networks**, allowing heterogeneous smaller networks to be interconnected. Nowadays, a message sent from a laptop can be read by its recipient half-way around the world on their phone within seconds. A broadcast stream of the FIFA World Cup Final can be enjoyed by millions around the world with minimal delay. We can even start the air conditioning in some modern cars remotely without having to leave the comfort of our house.

## Analog to Digital

The methods of communication described in the previous section were all very different from each other. However, at a fundamental level they all followed the same basic principle: a sender **encodes** her message into a form suitable for transmission. The encoded message is then sent to the **decoder**, which transforms the message back to a more easily readable form and passes it to the receiver.

To make this abstraction a little more concrete, let's consider the electrical telegraph as an example. The sender brings her message to an operator who knows how to use the Morse key. The operator uses the key to produce a series of dots and dashes, represented by short and long electrical signals which are transmitted to a distant telegraph station. There another operator receives these electrical signals, decodes them and reproduces the original message for the receiver.

The immediate question that arises is finding some good ways of encoding the message. The first method that we consider is encoding the message using an **analog** signal. Analog signals can admit a continuum of values. We perceive the world around us as analog. The loudness of sounds varies continuously from a quiet whisper to a loud music concert. The temperature rises and falls in a continuous way as measured by our thermometers. The three primary colors can be mixed together to produce a continuous spectrum of colors. Humans have evolved to process these types of analog signals; therefore, it makes sense to try using analog signals to encode our messages. The key is that analog signals can take on values from a continuous interval, representing the range of some quantity. For example, the voltage of an electric circuit can vary continuously depending on the pressure of sound waves in the microphone of an old telephone. Early AM radio signals and old TV broadcasting used continuous sinusoidal waves that required simple technology to produce and decode.

One problem with analog signals is that they are **susceptible to noise**. Even small changes to the signal can alter the meaning of the transmitted message. Due to this sensitivity to noise, analog signals are also difficult to copy. Every time an analog signal gets copied, it degrades in quality due to both the noise as well as the finite accuracy of the signal read out.

A clean analog signal looks like a smooth wave; the same signal affected by noise looks jagged and irregular. The noisy signal may have a meaning similar to the original noiseless message, or may be quite different.

An alternative to analog signals is **digital** signals. Digital signals are very different from analog signals; they only use a discrete set of values to represent the message and encode it. We can take the original analog signal, and try to encode it digitally. A way to do this is to **sample** the analog signal at discrete time steps $t_0$, $t_1$, $t_2$, $t_3$ and so on. The encoded digital signal is now a set of discrete values, $S_0, S_1, S_2, S_3, \ldots$, each of some finite accuracy.

The accuracy with which we can reproduce this analog signal depends on how often we look at and measure the signal, which is known as the **sampling rate**, and the precision of each sample, i.e. the number of discrete values that are used. For slowly varying signals, we don't have to sample that often, while still doing a pretty good job of encoding the analog signal accurately. But for analog signals that vary quickly, we should sample with higher frequency.

Digital signals are less affected by noise and are therefore easier to copy. Other advantages include the ease of producing digital signals and the ease of processing with digital logic.

## Bits as Building Blocks

We have seen that digital signals can be more practical than analog signals when it comes to communication. The question now is how do we represent these digital signals.

We saw an example of a digital system with the Nubian fortress signal fires described earlier. Let's go back and consider it again. Recall that a single sentry could light one fire to signal that a threat had been spotted, and that additional fires could be lit side by side to signal a larger-scale threat.

What does it take to change the state of this signal? Going from no fire to a single fire burning does not require that much effort. A lone guard simply has to light the one pile of wood that has already been prepared. On the other hand, going from no fire to three fires burning at once, signalling that a large force is approaching, requires much more effort. Several guards must prepare and light multiple fires within a short window of time so that the signal is unambiguous to the neighboring fortress. This change requires both more physical effort as well as more time.

A good representation for digital signals should require as little effort and time as possible in order to change the state of the digital signal. This suggests that having fewer internal states produces a better encoding for the message. The Morse code is such an example, where we only have two internal states. The letter "U" is encoded by two dots followed by a dash. The signal is switched on for a short time to represent a dot and for a long time to represent the dash. It is the presence or absence of a signal that conveys the information. When you change from *no signal* to *signal*, or when the signal *doesn't* change, this carries a small amount of information.

This unit of information is known as a **bit**, which is short for **binary digit**. In classical computation and in digital communication, the bit is the basic unit of information. It conveys the message of something being true or false, the signal being on or off. Usually we write the two states of a bit as 0 or 1. The signal encoding the letter "U" in Morse code can be written using bits as 1010111, where zeros and ones denote the state of the bit at different times. Even after being affected by noise, the different states of a bit can still be easily distinguished from each other, hence the meaning of the message can be read out without any ambiguity. Digital signals are generally more resilient to noise than analog signals.

We have said that a single bit can hold two different values. How many different values can multiple bits, also called **bit strings**, hold? The following table lists all possible bit string values for 1, 2, 3, and 4 bits.

| Number of bits | Possible bit strings | Total number |
|---|---|---|
| 1 | 0, 1 | 2 |
| 2 | 00, 01, 10, 11 | 4 |
| 3 | 000, 001, 010, 011, 100, 101, 110, 111 | 8 |
| 4 | 0000, 0001, 0010, 0011, 0100, 0101, 0110, 0111, 1000, 1001, 1010, 1011, 1100, 1101, 1110, 1111 | 16 |

It is clear that the total number of possible bit string values for $N$ bits is $2^N$.

Bits can be used to encode decimal numbers. Let's examine how decimal notation works. The decimal system uses ten numerals, 0-9. In a decimal number, the rightmost digit represents ones, the next digit to the left represents tens, the next hundreds and so on. For example, the number 1024 can be written in terms of powers of ten as follows:

$$
1024 = 1 \times 10^3 + 0 \times 10^2 + 2 \times 10^1 + 4 \times 10^0
$$

This idea carries over to binary numbers where the digits can only take values of 0 or 1, and represent multiples of powers of two. Let's see how we can write the binary number 1001 in decimal notation:

$$
1001 = 1 \times 2^3 + 0 \times 2^2 + 0 \times 2^1 + 1 \times 2^0 = 9
$$

Bits are the building blocks of modern communication. They are robust to noise, can be easily used to encode and decode information, and are easy for modern computers to process. Given that bits admit only two values, we might easily consider them to be the most fundamental units of information. In these lectures, we will learn that this is not quite true. We will see that quantum communication relies on more fundamental units of information. Classical bits are merely special cases of their quantum cousins.

## Quantum Communication

Information is physical (an aphorism coined by Rolf Landauer). It is carried by physical systems. The laws of physics determine how we can process or communicate this information. If we are only considering information processing in the context of classical mechanics, classical electromagnetism, and classical optics, then this will give us tools and ways of processing and communicating the information classically. However, if we expand our toolbox to include also quantum mechanics and quantum optics, then we are also expanding the ways in which we can process and communicate this information.

The question that we should answer before we start learning about quantum communication is, why do we need quantum mechanics? Why do we want to use quantum mechanics to process and communicate information? First, quantum mechanics is the fundamental theory of nature as we currently understand it. It describes the microscopic world where classical mechanics does not apply. It makes some stunning predictions, which, despite their counter-intuitiveness, have been tested very thoroughly over many decades. So far, the theory has always been proven correct. Furthermore, considering new laws of physics, and applying them to information processing and communication, often leads to new ways of processing and communicating this information.

These reasons in themselves are very fundamental, but there are also practical reasons. Current computing technology is hitting a classical to quantum boundary. Maybe you have heard of Moore's law, which despite its name is an observation rather than a physical law. Moore's Law states that the number of transistors in an integrated circuit doubles about every two years. It is astonishing that this observation has held for decades. Chip manufacturers now can pack about ten orders of magnitude more transistors into the same area than when integrated circuits were first invented. The chips themselves are not getting any bigger, so in order for Moore's Law to hold, the transistors must get smaller and smaller. In the beginning, the transistors were approximately 10 microns across. In the 1990s, they moved to about 600 nanometers. Now, we are at the level of single-digit nanometers. The transistors have gotten so small that we need to worry about the effects that quantum mechanics has on the transistors' operation.

What are the two main ingredients that set quantum communication apart from its classical counterpart? The first one is the **superposition principle**. This principle is not really anything new, as it is observed in the classical world as well. We are all familiar with superposition of waves. What is meant by superposition principle in quantum communication is the ability of quantum bits to be in a superposition of their usual classical states. The possibility of a quantum bit to be both on and off at the same time is mind-bending but is at the heart of quantum communication.

Expanding the principle of superposition to multiple particles, we arrive at the concept of **entanglement**. Entanglement has no classical counterpart whatsoever. It correlates distant quantum objects across large distances of space much more strongly than is possible using classical laws of nature. The beauty of entanglement is that it allows for radically new ways to communicate and is used as a resource in quantum communication. Distribution of entanglement is therefore one of the main jobs of quantum networks.

Quantum communication protocols are currently very difficult to implement. Quantum systems are very delicate as they **decohere** extremely rapidly, leading to loss of their quantum properties. They go from being true and false at the same time, to being only true or only false. Basically, they just become classical bits.

Quantum systems are difficult to build at the hardware level, but at the same time, it is also conceptually challenging to think about new ways of exploiting their quantum properties. Designing new protocols for processing and communication in the quantum realm requires new tools. It requires a completely new mental framework for how we approach problems, and how we solve problems. This all seems very daunting but these challenges should be viewed as opportunities. Quantum computation and quantum communication are vibrant and cross-disciplinary fields. Engineers, physicists, mathematicians, and computer scientists are all working together on cracking difficult questions whose solutions will lead to incredible new quantum technologies.

## Security in the Quantum Age

Quantum technologies carry the potential to impact a number of important areas. Quantum simulation and computation are thought to bring about new methods in developing materials with novel and useful properties, as well as novel drugs. Quantum metrology allows for measurements with unprecedented resolution and sensitivity. Quantum machine learning aims to exploit the properties of quantum mechanics to enhance artificial intelligence. Lastly, you may have heard that quantum computers will be able to crack some widely used encryption schemes deployed currently, which may sound like a doomsday scenario. Since these lecture notes focus on quantum communication, we will briefly discuss what this claim means and show how quantum technologies can also enhance security.

Computer security experts sometimes refer to the "CIA triad" of *confidentiality*, *integrity*, and *availability*. *Encryption* refers to a set of mathematical techniques for protecting digital information, making it difficult to read or to modify undetected, often used to achieve one of the CIA goals. In this book, we will loosely refer to "security" to mean this use of encryption.

Let's consider a sender wishing to send a message to a receiver. The message might be something mundane such as "Buy some milk, please" or might be something sensitive such as "My credit card number is ...". Either way, messages sent over public channels are encrypted to preserve the privacy of the conversation between the sender and the receiver. Let's consider a third party, an eavesdropper, who is trying to listen in on the conversation by intercepting the message. The most commonly deployed current classical encryption techniques offer **computational security**, meaning that cracking them is not impossible, merely very difficult and would require enormous classical resources. Quantum algorithms exist that have the potential to break this encryption if they capture the message sequence starting from the initial exchange. An eavesdropper with access to a quantum computer could in principle intercept the encrypted message, use their quantum computer to break the code and listen in on the conversation with impunity.

To overcome this problem, the communicating parties need to resort to using **quantum key distribution** (QKD). With the help of the superposition principle or entanglement, the sender and the receiver can discover the eavesdropper's attempts to intercept and tamper with their messages. They can then simply not transmit their sensitive message. This method of encryption offers **information-theoretic security**. Such security does not rely on the computational difficulty of certain mathematical problems and therefore is stronger than the computational security used currently (or at least offers a different attack surface). For this reason, QKD is one of the primary applications of quantum networks. We will explore the basics of QKD later in this book.

## Module Overview

Before concluding the first chapter, let's have a brief look at the structure of this module. The next three chapters deal with the basics of quantum mechanics relevant to quantum communication. We will learn about quantum bits and how they are different from classical bits, consider how noise affects the state of quantum states and how we can describe this effect mathematically. Finally, we will look at systems of multiple quantum bits, including entanglement and SPDC, a critical method of creating entanglement in optical systems.

Chapters 5-7 deal with the basics of optics. Light is an excellent information carrier and we will learn how lasers produce light. We will discuss interference, one of the fundamental phenomena in both classical as well as quantum physics. We will conclude this block of chapters by learning about waveguides and how light is guided in a network.

Chapters 8-10 look at fundamental quantum communication protocols. We will learn how teleportation can be used to transmit information without sending the physical system encoding this information as well as how quantum key distribution works.

In chapters 11-13, we will look at the basics of quantum repeaters, a quantum technology that makes long-distance quantum communication possible. The last two chapters look at quantum repeater systems.

There are some basic prerequisites for this module such as linear algebra (meaning vector and matrix multiplication; eigenvectors and eigenvalues; also, we will use the tensor product which will be introduced in this book), discrete probability, and complex numbers (e.g., $i = \sqrt{-1}$ and Euler's equation, $e^{i\pi} + 1 = 0$). The description of how lasers amplify light in a later chapter makes minimal use of derivatives from elementary calculus, but the core discussion is designed to be understandable without a background in calculus. It's very helpful if you have some introduction to quantum computing; programming and classical computing; and computer networks. Other than that there are no physics requirements.

If you don't have some of this background yet, there are a lot of online materials, particularly our MOOC (massively open online course), "Understanding Quantum Computers", which is targeted at learners at the high school level and requires very minimal math. It is available in English, Japanese, Thai and Indonesian. If you would like to learn a little bit more about some basic linear algebra you can have a look at the playlist on Professor Van Meter's YouTube channel. There are many other courses available. Other modules from the Quantum Academy of Science and Technology (supported by the Q-Leap Education office in Japan) cover some of this background material as well, and may be available to you.
