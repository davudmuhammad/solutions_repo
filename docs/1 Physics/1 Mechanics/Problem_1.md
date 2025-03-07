# Problem 1
# Theoretical Foundation

## 1. Governing Equations of Motion

### Newton's Second Law
The motion of a system is fundamentally governed by Newton’s Second Law:

\[ F = ma \]

where:
- \( F \) is the force acting on a body,
- \( m \) is the mass of the body,
- \( a \) is the acceleration \( a = \frac{d^2x}{dt^2} \).

For a conservative system with a restoring force \( F(x) \), we assume a linear force:

\[ F = -kx \]

where \( k \) is a proportionality constant (such as the stiffness of a spring). Applying Newton’s Second Law:

\[ m \frac{d^2x}{dt^2} = -kx \]

Rearranging:

\[ \frac{d^2x}{dt^2} + \frac{k}{m} x = 0 \]

Defining \( \omega^2 = \frac{k}{m} \), we get the standard form of the simple harmonic oscillator equation:

\[ \frac{d^2x}{dt^2} + \omega^2 x = 0 \]

where \( \omega \) is the natural angular frequency.

## 2. General Solution
This is a second-order homogeneous differential equation with characteristic equation:

\[ r^2 + \omega^2 = 0 \]

Solving for \( r \):

\[ r = \pm i \omega \]

The general solution is:

\[ x(t) = A \cos(\omega t) + B \sin(\omega t) \]

where \( A \) and \( B \) are constants determined by initial conditions.

## 3. Effect of Initial Conditions
Let the initial conditions be:

\[ x(0) = x_0, \quad \dot{x}(0) = v_0 \]

Using \( x(0) = x_0 \):

\[ x_0 = A \cos(0) + B \sin(0) = A \]

Thus, \( A = x_0 \).

Taking the derivative:

\[ \dot{x}(t) = -A\omega \sin(\omega t) + B\omega \cos(\omega t) \]

Applying \( \dot{x}(0) = v_0 \):

\[ v_0 = -x_0 \omega \sin(0) + B\omega \cos(0) = B\omega \]

Thus, \( B = \frac{v_0}{\omega} \).

## 4. Final Expression for Motion
Substituting \( A \) and \( B \) into the general solution:

\[ x(t) = x_0 \cos(\omega t) + \frac{v_0}{\omega} \sin(\omega t) \]

## 5. Family of Solutions
The solution depends on initial conditions:
- If \( x_0 > 0 \) and \( v_0 = 0 \), motion starts from rest at \( x_0 \).
- If \( x_0 = 0 \) and \( v_0 > 0 \), motion starts from equilibrium with an initial velocity.
- Different values of \( x_0 \) and \( v_0 \) lead to different phase shifts in oscillatory motion.

This derivation establishes the fundamental equation of motion and demonstrates how varying initial conditions yield a family of sinusoidal solutions.

# Simulating Particle Motion

## 1. Motion in a Uniform Magnetic Field
A charged particle of charge \( q \) moving with velocity \( \mathbf{v} \) in a uniform magnetic field \( \mathbf{B} \) experiences a Lorentz force:

\[ \mathbf{F} = q (\mathbf{v} \times \mathbf{B}) \]

This results in circular motion with radius:

\[ r = \frac{m v}{q B} \]

and angular frequency:

\[ \omega_c = \frac{qB}{m} \]

The trajectory is a helix if there is an initial velocity component parallel to \( \mathbf{B} \).

## 2. Motion in Combined Electric and Magnetic Fields
When both electric \( \mathbf{E} \) and magnetic \( \mathbf{B} \) fields are present, the Lorentz force equation becomes:

\[ m \frac{d \mathbf{v}}{dt} = q (\mathbf{E} + \mathbf{v} \times \mathbf{B}) \]

The motion depends on the relative orientations of \( \mathbf{E} \) and \( \mathbf{B} \), leading to drift motion.

## 3. Motion in Crossed Electric and Magnetic Fields
For perpendicular \( \mathbf{E} \) and \( \mathbf{B} \) fields, the particle undergoes **E×B drift** with velocity:

\[ \mathbf{v}_d = \frac{\mathbf{E} \times \mathbf{B}}{B^2} \]

which is independent of the charge and mass of the particle.

Numerical simulations can visualize these trajectories by solving the differential equations governing the motion using computational methods such as the Runge-Kutta method.

# Implementation

## 1. Developing a Computational Tool
A Python script or Jupyter notebook can be used to implement simulations for projectile motion. This involves solving the equations of motion numerically using methods like Euler's method or Runge-Kutta integration.

## 2. Visualization of Range vs. Angle
A key computational task is to visualize the projectile range as a function of launch angle:
- Solve the motion equations for different launch angles.
- Incorporate drag force for realistic modeling.
- Generate range vs. angle plots to determine optimal launch parameters.


# Practical Applications

## 1. Sports Science and Ballistics
Understanding projectile motion helps optimize sports strategies, such as improving basketball shooting angles or golf swings. Similarly, ballistics relies on precise trajectory calculations for targeting.

## 2. Spacecraft and Orbital Dynamics
Satellite launches and interplanetary missions require accurate motion predictions under gravitational fields and atmospheric drag.

## 3. Engineering and Defense
Projectile motion equations are used in designing missile guidance systems, artillery range calculations, and even civil engineering applications like structural impact analysis.

This task provides a deep understanding of motion equations while showcasing their applicability in real-world scenarios.

import numpy as np
from scipy.integrate import odeint
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11  # Gravitational constant, m^3 kg^-1 s^-2
M_EARTH = 5.972e24  # Mass of Earth, kg
R_EARTH = 6371e3  # Radius of Earth, m
C_D = 2.2  # Drag coefficient (assumed)
A = 20  # Cross-sectional area of the spacecraft, m^2 (assumed)
rho_0 = 1.225  # Sea level atmospheric density, kg/m^3
H = 8500  # Scale height for atmosphere, m

# Initial conditions
r0 = R_EARTH + 400e3  # Initial altitude of 400 km
v0 = 7.8e3  # Initial velocity, m/s (assumed)
angle = np.radians(45)  # Launch angle, degrees converted to radians
x0 = r0 * np.cos(angle)
y0 = r0 * np.sin(angle)
vx0 = v0 * np.cos(angle)
vy0 = v0 * np.sin(angle)
initial_conditions = [x0, y0, vx0, vy0]

# Equations of motion
def equations_of_motion(y, t):
    x, y, vx, vy = y
    r = np.sqrt(x**2 + y**2)
    
    # Gravitational force
    F_grav = -G * M_EARTH / r**3
    ax_grav = F_grav * x
    ay_grav = F_grav * y
    
    # Atmospheric drag
    altitude = r - R_EARTH
    rho = rho_0 * np.exp(-altitude / H)
    v = np.sqrt(vx**2 + vy**2)
    F_drag = 0.5 * C_D * A * rho * v**2
    ax_drag = -F_drag * vx / (v * initial_conditions[0])
    ay_drag = -F_drag * vy / (v * initial_conditions[0])
    
    # Total acceleration
    ax = ax_grav + ax_drag
    ay = ay_grav + ay_drag
    
    return [vx, vy, ax, ay]

# Time span for the simulation
t = np.linspace(0, 5400, 1000)  # Simulate for 1.5 hours

# Solve the equations of motion
solution = odeint(equations_of_motion, initial_conditions, t)

# Extract the results
x_sol = solution[:, 0]
y_sol = solution[:, 1]

# Plot the trajectory
plt.plot(x_sol, y_sol)
plt.xlabel('x (m)')
plt.ylabel('y (m)')
plt.title('Spacecraft Trajectory')
plt.axis('equal')
plt.grid(True)
plt.show()
