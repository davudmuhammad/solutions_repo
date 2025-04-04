# Problem 1# Orbital Period and Orbital Radius

##  1. Derivation of the Relationship for Circular Orbits

We start by equating the gravitational force and centripetal force:

\[
\frac{G M m}{r^2} = \frac{m v^2}{r}
\]

Where:
- \( G \): Gravitational constant
- \( M \): Mass of central body (e.g., Sun)
- \( m \): Mass of orbiting body
- \( r \): Orbital radius
- \( v \): Orbital speed

Solving for \( v \):

\[
v = \sqrt{\frac{G M}{r}}
\]

The orbital period \( T \) is the time to complete one orbit:

\[
T = \frac{2\pi r}{v} = 2\pi \sqrt{\frac{r^3}{G M}}
\]

Squaring both sides:

\[
T^2 = \frac{4\pi^2}{G M} \cdot r^3
\]

 **Conclusion**: \( T^2 \propto r^3 \)

---

##  2. Implications in Astronomy

Kepler’s Third Law enables astronomers and scientists to:

- Measure the **mass of stars and planets**
- Calculate **distances between celestial bodies**
- Predict **satellite orbits** (e.g., GPS, weather satellites)
- Analyze **binary star systems** and discover **exoplanets**

It’s crucial for both **space navigation** and **cosmology**.

---

## 3. Real-World Examples

### 🌕 Moon-Earth System

- **Orbital radius**: \( 3.84 \times 10^8 \, \text{m} \)
- **Orbital period**: \( 27.3 \, \text{days} \)
- Perfectly fits \( T^2 \propto r^3 \) using Earth's mass.

### ☀️ Solar System Planets

Using actual data:

| Planet   | Radius (m)           | Period (s)         | \( T^2 \propto r^3 \) |
|----------|----------------------|--------------------|-----------------------|
| Earth    | \( 1.496 \times 10^{11} \) | \( 3.156 \times 10^7 \) | ✅ Confirmed |
| Mars     | \( 2.279 \times 10^{11} \) | \( 5.935 \times 10^7 \) | ✅ Confirmed |
| Jupiter  | \( 7.785 \times 10^{11} \) | \( 3.743 \times 10^8 \) | ✅ Confirmed |
| Neptune  | \( 4.503 \times 10^{12} \) | \( 5.200 \times 10^9 \) | ✅ Confirmed |

These obey Kepler’s Third Law even on a cosmic scale.

---

##  4. Computational Model

We numerically verified Kepler’s Third Law using the formula:

\[
T^2 = \frac{4\pi^2 r^3}{G M}
\]

Using Python, we:

- Simulated orbital periods for various radii.
- Applied the formula to real Solar System data.
- Plotted \( \log(T^2) \) vs \( \log(r^3) \).

### Result:

The plot is a straight line with slope ≈ 1, confirming:

\[
\log(T^2) \propto \log(r^3)
\]

This validates Kepler’s Third Law computationally.

---

## Conclusion

Kepler’s Third Law elegantly links **orbital dynamics** with **universal gravitation**. It empowers astronomers to decode the cosmos — from satellite navigation to exoplanet discovery.

Theoretical derivation, observational data, and computational simulation all confirm the law:

\[
T^2 \propto r^3
\]
