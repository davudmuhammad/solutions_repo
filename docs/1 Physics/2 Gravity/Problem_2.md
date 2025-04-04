# Problem 2
# Escape Velocities and Cosmic Velocities

## Motivation

The concept of escape velocity is central to celestial mechanics and space exploration. It defines the speed required to overcome a celestial body's gravitational pull. Extending this idea, the first, second, and third cosmic velocities set the thresholds for:

- Maintaining orbit,
- Escaping a planet’s gravity,
- Leaving the Solar System entirely.

These principles are foundational for modern space missions — from satellite deployment to interstellar probes.

---

## 1. First Cosmic Velocity (Orbital Velocity)

### Definition

The **first cosmic velocity** is the minimum speed required to maintain a stable circular orbit just above a planet’s surface (neglecting atmospheric drag).

### Formula

\[
v_1 = \sqrt{\frac{G M}{R}}
\]

Where:
- \( G \): Gravitational constant (\(6.67430 \times 10^{-11} \, \text{m}^3/\text{kg} \cdot \text{s}^2\))
- \( M \): Mass of the planet
- \( R \): Radius of the planet

### Physical Meaning

It represents the speed at which the gravitational pull provides exactly the centripetal force needed to keep the object in orbit.

### Examples

- Earth: ~7.9 km/s
- Mars: ~3.6 km/s
- Jupiter: ~42.1 km/s

---

## 2. Second Cosmic Velocity (Escape Velocity)

### Definition

The **second cosmic velocity** is the speed needed to break free from a celestial body’s gravitational influence, reaching infinity with zero kinetic energy.

### Formula

\[
v_2 = \sqrt{2} \cdot v_1 = \sqrt{\frac{2 G M}{R}}
\]

### Physical Meaning

At this speed, the kinetic energy of the object matches the gravitational potential energy pulling it back.

### Examples

- Earth: ~11.2 km/s
- Mars: ~5.0 km/s
- Jupiter: ~59.5 km/s

---

## 3. Third Cosmic Velocity (Interstellar Escape)

### Definition

The **third cosmic velocity** is the speed required to escape the gravitational field of the **entire Solar System** from Earth’s orbit.

### Approximate Formula

\[
v_3 \approx \sqrt{2 G M_{\text{Sun}} / R_{\text{orbit}}}
\]

Where:
- \( M_{\text{Sun}} \): Mass of the Sun
- \( R_{\text{orbit}} \): Earth's orbital radius (~1 AU)

### Example

- Earth to Interstellar space: ~16.7 km/s
- Voyager 1's speed (with gravity assists): ~17 km/s

---

## Importance in Space Exploration

| Cosmic Velocity | Application                                |
|------------------|--------------------------------------------|
| 1st              | Satellite and space station deployment     |
| 2nd              | Planetary missions (e.g., Moon, Mars)      |
| 3rd              | Interstellar missions (e.g., Voyager, future probes) |

Understanding these velocities helps design efficient propulsion systems and plan interplanetary trajectories, slingshots, and deep-space exploration.

---

## Python Implementation: Calculating Cosmic Velocities

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Gravitational constant
G = 6.67430e-11  # m^3 kg^-1 s^-2

# Celestial bodies
bodies = [
    {"Name": "Earth", "Mass": 5.972e24, "Radius": 6.371e6},
    {"Name": "Mars", "Mass": 6.417e23, "Radius": 3.390e6},
    {"Name": "Jupiter", "Mass": 1.898e27, "Radius": 6.9911e7}
]

# Compute cosmic velocities
results = []
for body in bodies:
    M = body["Mass"]
    R = body["Radius"]
    v1 = np.sqrt(G * M / R)
    v2 = np.sqrt(2) * v1
    v3 = np.sqrt(2 * G * M / R) * 2  # Simplified estimate of third cosmic velocity

    results.append({
        "Body": body["Name"],
        "First Cosmic Velocity (m/s)": v1,
        "Second Cosmic Velocity (m/s)": v2,
        "Third Cosmic Velocity (m/s, approx.)": v3
    })

# DataFrame
df = pd.DataFrame(results)
print(df)

# Plotting
labels = df["Body"]
x = np.arange(len(labels))
width = 0.25

fig, ax = plt.subplots(figsize=(10, 6))
bar1 = ax.bar(x - width, df["First Cosmic Velocity (m/s)"], width, label='1st Cosmic Velocity')
bar2 = ax.bar(x, df["Second Cosmic Velocity (m/s)"], width, label='2nd Cosmic Velocity')
bar3 = ax.bar(x + width, df["Third Cosmic Velocity (m/s, approx.)"], width, label='3rd Cosmic Velocity')

ax.set_ylabel('Velocity (m/s)')
ax.set_title('Cosmic Velocities for Earth, Mars, and Jupiter')
ax.set_xticks(x)
ax.set_xticklabels(labels)
ax.legend()
plt.grid(True)
plt.tight_layout()
plt.show()
