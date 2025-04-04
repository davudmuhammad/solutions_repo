# Problem 2# **Forced Damped Pendulum: Theoretical and Dynamic Analysis**

## **1. Theoretical Foundation**

### **Governing Equation**

The motion of a forced damped pendulum is described by:

\[
\frac{d^2\theta}{dt^2} + \gamma \frac{d\theta}{dt} + \omega_0^2 \sin\theta = A \cos(\omega t)
\]

Where:
- \( \theta(t) \): Angular displacement  
- \( \gamma \): Damping coefficient  
- \( \omega_0 \): Natural frequency \( = \sqrt{\frac{g}{L}} \)  
- \( A \): Driving amplitude  
- \( \omega \): Driving frequency  

---

### **Small-Angle Approximation**

Assuming \( \theta \ll 1 \), we use \( \sin\theta \approx \theta \):

\[
\frac{d^2\theta}{dt^2} + \gamma \frac{d\theta}{dt} + \omega_0^2 \theta = A \cos(\omega t)
\]

#### **Solution:**
\[
\theta(t) = B \cos(\omega t - \delta)
\]

Where:
- \( B = \frac{A}{\sqrt{(\omega_0^2 - \omega^2)^2 + (\gamma \omega)^2}} \)
- \( \delta = \tan^{-1} \left( \frac{\gamma \omega}{\omega_0^2 - \omega^2} \right) \)

---

### **Resonance Condition**

Maximum amplitude (resonance) occurs near:

\[
\omega_{\text{res}} = \sqrt{\omega_0^2 - \frac{\gamma^2}{2}}
\]

- At resonance, energy absorption is maximized.
- Damping limits amplitude growth.

---

## **2. Analysis of Dynamics**

### **Parameter Effects:**

- **Damping \( \gamma \)**:
  - High: Motion dies quickly, broad resonance.
  - Low: Sustained oscillations, sharp resonance.

- **Driving Amplitude \( A \)**:
  - Low: Periodic motion.
  - High: Nonlinear effects dominate; possible chaos.

- **Driving Frequency \( \omega \)**:
  - Near \( \omega_0 \): Resonance.
  - Far from \( \omega_0 \): Reduced response.

---

### **Numerical Simulation Results**

- **Parameters**:  
  \( \gamma = 0.2 \), \( \omega_0 = 1.5 \), \( A = 1.2 \), \( \omega = 0.666 \)

- **Initial Conditions**:  
  \( \theta(0) = 0.2 \), \( \dot{\theta}(0) = 0.0 \)

#### **Time Series Plot**

- Shows transient decay and steady-state periodic response.

#### **Phase Space Plot**

- Displays angular position vs. angular velocity.
- Structure hints at complexity (possibly quasi-periodic or chaotic depending on parameters).

---

## **Next Steps (Optional Visualizations)**

- Generate **Poincaré sections** to identify chaotic regimes.
- Construct **bifurcation diagrams** by varying \( A \) or \( \omega \).
- Calculate **Lyapunov exponents** to quantify chaos.
