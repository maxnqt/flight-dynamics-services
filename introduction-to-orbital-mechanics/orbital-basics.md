# Orbital basics

- [ ] Explain how early space explorers contributed to our understanding of orbits
- [ ] Understand Newton’s three basic laws of motion and how they apply to orbits
- [ ] Explain and use Newton’s Universal Law of Gravitation
- [ ] Use the two constants of orbital motion – specific mechanical energy and specific angular momentum, to explain basic properties of orbits
- [ ] Combine these laws to develop the two-body equation of motion
- [ ] Integrate the two-body equation of motion (optional)

## Review: vector mathematics, trigonometry and calculus

**Vector notation**

- _Scalar_ is a quantity (has magnitude only; **does not** have an arrow)
- _Vector_ is a quantity that has magnitude and direction (**denoted with an arrow**)
- _Unit vector_ is a vector with a magnitude of one (determines direction only)
- Vectors can be resolved into components: $\vec{F} = \vec{F_{x}} + \vec{F_{y}} + \vec{F_{z}}$
- $\vec{F} = F_{x}\widehat{I} + F_{y}\widehat{J} + F_{z}\widehat{K}$, where $\widehat{I}, \widehat{J}, \widehat{K}$ are the unit vectors in the x-, y-, and z-directions

**Vector operations**

- The _magnitude of a vector_ is the scalar part of a vector
- If $\vec{R} = R_{I}\widehat{I} + R_{J}\widehat{J} + R_{K}\widehat{K}$, then $|\vec{R}| = R = \sqrt{R_{I}^{2}\widehat{I} + R_{J}^{2}\widehat{J} + R_{K}^{2}\widehat{K}}$

**Dot products**

- The _Dot product_ of two vectors $\vec{A}$ and $\vec{B}$ multiplies the amoung of $\vec{A}$ that is in the direction of $\vec{B}$ by the magnitude of $\vec{B}$
- $\vec{A} \cdot \vec{B} = AB cos \theta = A_{I}B_{I} + A_{J}B_{J} + A_{K}B_{K}$
- Note: dot product is/produces a scalar

**Cross products (vector products)**

- The _Dot product_ of two vectors in three dimensions is a vector at right angles to both the original vectors
- _You can use the right-hand rule to find the direction of the third vector_
- Mathematically, you solve the determinant:

$$
\begin{vmatrix}
\widehat{I} & \widehat{J} & \widehat{K} \\
A_{I} & A_{J} & A_{K} \\
B_{I} & B_{J} & B_{K}
\end{vmatrix}
\quad
\textbf{so}
\quad
\vec{A} \times \vec{B} =
\left[(A_{J})(B_{K}) - (B_{J})(A_{K})\right]\widehat{I} - \left[(A_{I})(B_{K}) - (B_{I})(A_{K})\right]\widehat{J} + \left[(A_{I})(B_{J}) - (B_{I})(A_{J})\right]\widehat{K}
$$

- Note: cross product is/produces a vector

**Angles and quadrant checks**

- A lot of astrodynamics is _determining the angle between two vectors_
- Mainly done using dot products, which results in an _inverse cosine_

$$\vec{A} \cdot \vec{B} = AB cos \theta \rightarrow \theta =  cos^{-1}\left(\frac{\vec{A} \cdot \vec{B}}{AB}\right)$$

- Potential issue: cosine is periodic (!), mathematically, we get two answers, but physically, only one of them is correct
- Avoid this issue by using the _unit circle_:
  - We can use our vectors to determine which quadrant of the unit circle we're in
  - Then use that to determine the correct angle

## Kepler's laws

- Periapsis: Closest point
- Apoapsis: Farthest point
- Periapsis and apoapsis are the two extreme points in an elliptical orbit, defining the closest and furthest distances between an orbiter and its central body
- Eccentric orbit: Non-circular orbit
- Keppler believed that the planets moved around the Sun in elliptical orbits with the Sun not at the center, but at one of the ellipse’s focal points
- He developed _three Laws of Orbital Motion_

**Kepler's first law**

- The orbits of the planets are ellipses with the Sun at one focus

**Kepler's second law**

- When the planet is closest to the Sun (at perihelion), it must be travelling faster than when it is farther from the Sun
- Planets sweep out equal areas in equal times (_the line joining a planet to the sun sweeps out equal areas in equal times_)

**Kepler's third law**

- _Orbital period:_ The time it takes for a planet to complete one orbit
- The square of an orbit's period is proportional to the cube of the mean (or average) distance between the Sun and the planet

$$Period = 2\pi\sqrt{\frac{a^{3}}{\mu}}seconds$$

- Where $a$ is the semi-major axis, which describes the size of the orbit and $\mu = GM$ is called the gravitational constant
- $G$ is the universal gravitational constant, and $M$ is the mass of the central body
- The larger the orbit,  the longer it takes for the object to traverse it (!)
- Keplers third law allows us to predict the orbit of any object in space traveling around a central body

## Newton's laws

**Newton's first law of motion**

- _A body continues in its state of rest, or of uniform motion in a straight line, unless compelled to change that state by forces impressed upon it_
- Any object which is at rest will stay at rest unless some force makes it move
- Similarly, any object in motion will stay in motion forever, with a constant speed in a straight-line direction, until some force makes it change its speed or direction of motion
- How this law applies to satellites in orbit:
  - A satellite is traveling in a circle or ellipse about some central body
  - Since it is not traveling in a straight line, there must be some force acting on it
  - That force is gravity, and it must be pulling the satellite in the direction of the central body
  - Second, inertia keeps an object from moving without the application of an outside force
  - However, once it is moving, an object has momentum, which is the amount of resistance an object in motion has to changes in its speed or direction of motion
- **There must be a force on satellites - gravity (!)**
- **Momentum is conserved - orbits are constant (in orientation and size)**
- _Momentum:_ The amount of resistance an object in motion has to changes in its speed or direction of motion
- There are two types: Linear momentum and angular momentum
- Linear momentum is defined as mass times velocity and often represented by the variable $\vec{p}$

$$\vec{p} = m\vec{V}$$

- $\vec{p}$ is the linear momentum vector $\left(\frac{kg \cdot m}{s}\right)$
- $m$ is mass $\left(kg\right)$
- $\vec{V}$ is the velocity vector $\left(\frac{m}{s}\right)$

**Newton's second law of motion**

- _The time rate of change of an object’s momentum is equal to the applied forces_
- Linear momentum is a vector $\vec{p} = m\vec{V}$
- The time rate of change of the momentum is then the derivative of the product of mass and velocity

$$\frac{d\vec{p}}{dt} = \frac{d(m\vec{V})}{dt} = \frac{dm}{dt}\vec{V} + m\frac{d(\vec{V})}{dt}$$

- Newton's second law says this product is equal the applied forces, which can be one or more

$$‎‎\sum{\vec{F}} = \frac{dm}{dt}\vec{V} + m\frac{d\vec{V}}{dt}$$

- $\frac{d\vec{V}}{dt} = \vec{a}$ where $\vec{a}$ is the acceleration vector
- $\frac{dm}{dt} = 0$ only if mass is not changing, meaning

$$‎‎\sum{\vec{F}} = m\vec{a}$$

**only when mass is not changing (!)**

**Newton's third law of motion**

- _For every action there is an equal and opposite reaction_

**Newton's universal law of gravitation**

- The force of gravity must somehow be related to the distance between the two bodies
- The force of gravity between the earth and any object is inversely proportional to the square of the distance that separates the object from the earth’s center
- Universal: All objects attract each other with a force of gravitational attraction, and that force is directly dependent upon the masses of both objects and inversely proportional to the square of the distance that separates their centers

$$F_{grav} \propto \frac{m_{1}m_{2}}{R^{2}}$$

- Note: $\propto$ is the symbol for _proportional to_; $R$ is the distance between the two object’s **centers**

$$F_{grav} = \frac{Gm_{1}m_{2}}{R^{2}}$$

- Where $G$ represents the universal gravitational constant $\left(G = 6.67 \times 10^{-11}\frac{Nm^{2}}{k\hspace{0.1cm}kg^{2}}\right)$
- We will define a new parameter $\mu$, the Earth’s gravitational constant, as follows:

$$\mu = Gm_{Earth} = 398600.5 \frac{km^{3}}{s^{2}}$$

so, Newton's universal law of gravitation for an object around earth becomes

$$\Rightarrow F_{grav} = \frac{\mu m_{s}}{R^{2}}$$

where $m_{s}$ is the mass of the satellite

## Laws of conservation

- If a certain property or quantity remains unchanged for a system, that property or quantity is said to be _conserved_

### Specific angular momentum

- Linear momentum is conserved for a system as follows: $\vec{p} = m \vec{V}$
- Momentum: Amount of resistance an object in motion has to a change in its speed or direction of motion
- Angular momentum: Moment of momentum is given by

$$\vec{H} = \vec{R} \times \vec{p} = \vec{R} \times m \vec{V}$$

- $\vec{H}$ is alwats perpendicular to the plane of motion
- Note: Mass does not matter in free fall; let's define **$\vec{h}$, specific angular momentum** as follows

$$\vec{h} = \frac{\vec{H}}{m} = \vec{R} \times \vec{V}$$

- Implications for satellites in orbit:
  - A satellite's orbital plane is fixed unless external torque is applied
  - It takes a lot of energy to change an orbital plane

### Specific mechanical energy

- Total mechanical energy consists of kinetic and potential energy
- Total mechanic energy is equal to the combination of kinetic and potential energy; those two energies are traded off such that the total energy is constant

$$E = KE + PE$$

where $E$ is the total mechanical energy, $KE$ is kinetic, and $PE$ is potential energy

$$KE = \frac{1}{2} m V^{2} \hspace{0.25cm} \left(\frac{kg \hspace{0.1cm} m^{2}}{s^{2}}\right)$$

$$PE = mgh \hspace{0.25cm} \left(\frac{kg \hspace{0.1cm} m^{2}}{s^{2}}\right)$$

where $m$ is mass, $V$ is velocity, $g$ the gravitational constant ($9.81 \frac{m}{s^{s}}$ for earth), and $h$ the height from datum (_datum_ is where you define $PE = 0$)

- Specific mechanical energy (typically in units of $\frac{km^{2}}{s^{2}}$) is given by

$$\Epsilon = \frac{E}{m}$$

- Specifc kinetic energy: $\frac{V^{2}}{m}$

## Credits

- [https://oer.pressbooks.pub/lynnanegeorge/chapter/copy-of-chapter-1__editing/](https://oer.pressbooks.pub/lynnanegeorge/chapter/copy-of-chapter-1__editing/)
