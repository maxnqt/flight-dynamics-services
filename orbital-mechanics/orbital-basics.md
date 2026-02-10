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

- 

## Newton's laws

- 

## Credits

- [https://oer.pressbooks.pub/lynnanegeorge/chapter/copy-of-chapter-1__editing/](https://oer.pressbooks.pub/lynnanegeorge/chapter/copy-of-chapter-1__editing/)
