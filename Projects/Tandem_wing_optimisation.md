# Tandem Wing Aerodynamic Optimisation using CFD and Response Surface Modelling

## Overview
This project focuses on the aerodynamic optimisation of a **tandem wing UAV configuration** using CFD simulations combined with surrogate modelling and gradient-based optimisation techniques.

The configuration consists of a front and rear wing whose aerodynamic interaction strongly influences lift, trim, and stability. The study aims to identify the optimal geometric arrangement that maximises aerodynamic performance while satisfying stability constraints.

The optimisation problem was formulated using three key design variables:

- **Gap (H):** vertical distance between front and rear wings  
- **Stagger (L):** horizontal distance between wings  
- **Decalage (αd):** difference in incidence angle between front and rear wings  

---

# Numerical Method

## Problem Formulation

The optimisation objective was to:

**Maximise cruise lift coefficient (Cl₍cruise₎)**  

evaluated at an operating condition corresponding to **AoA ≈ 2°**, obtained by interpolation from CFD simulations :contentReference[oaicite:0]{index=0}.

---

## Constraints

The optimisation was subject to **trim and stability constraints**:

- **Moment constraint:**  
  \[
  C_m \approx 0
  \]  
  ensuring longitudinal trim (level flight)

- **Aerodynamic center constraint:**  
  \[
  X_{ac} \in [0.09,\; 0.12]
  \]  
  ensuring static stability :contentReference[oaicite:1]{index=1}  

These constraints ensure that the configuration is not only high-lift but also **physically flyable and stable**.

---

## CFD and Surrogate Modelling

A **15-point D-optimal Design of Experiments (DoE)** was used to sample the design space.

For each design point:

- ANSYS Fluent simulations were performed at:
  - AoA = 0°  
  - AoA = 4°  

- The following quantities were extracted:
  - Lift coefficient (Cl)  
  - Moment coefficient (Cm)  
  - Aerodynamic center location (Xac)  

Cruise lift at AoA = 2° was then interpolated from these results :contentReference[oaicite:2]{index=2}.

---

### Response Surface Model (RSM)

A **second-order Response Surface Model** was constructed for:

- Cl₍cruise₎  
- Cm  
- Xac  

This enabled rapid evaluation of objective and constraints without repeated CFD simulations.

Monotonicity and concavity analysis were performed to ensure:

- existence of a valid optimum  
- well-posed optimisation behaviour :contentReference[oaicite:3]{index=3}  

---

## Optimisation Techniques

The optimisation was carried out in two stages:

### 1. Reduced 2D Optimisation (H, αd)

Used to understand constraint behaviour:

- Sequential Linear Programming (SLP)  
- Sequential Quadratic Programming (SQP)  
- Steepest Descent (self-implemented)  
- Cyclic Coordinate Search  

---

### 2. Full 3D Optimisation (H, αd, L)

Final optimisation including all variables:

- SLP / SQP (MATLAB fmincon)  
- **Sequential Approximate Optimisation (SAO)**  
  - Local RSM fitting  
  - Trust-region refinement  

All optimisation methods converged to the **same solution**, demonstrating robustness of the problem formulation :contentReference[oaicite:4]{index=4}.

---

# Flow Physics

The optimisation is governed by **aerodynamic interaction between the two wings**:

- The front wing generates **downwash**, reducing the effective AoA of the rear wing  
- This interaction can generate a **pitch-up moment**, reducing the need for large decalage  
- Excessive decalage misaligns wings from optimal lift conditions, reducing efficiency  

Thus, the optimisation effectively seeks to:

→ **Minimise required decalage while satisfying trim constraints** :contentReference[oaicite:5]{index=5}  

---

# Key Results

All optimisation approaches converged to the same optimal configuration:

### Optimal Geometry

- **Gap:**  
  \[
  H \approx -60 \text{ mm}
  \]  
  (front wing positioned slightly above rear wing)

- **Decalage:**  
  \[
  \alpha_d \approx 0.9^\circ
  \]

- **Stagger:**  
  \[
  L = 750 \text{ mm (maximum allowable)}
  \]  
  (minor influence on performance) :contentReference[oaicite:6]{index=6}  

---

### Physical Interpretation

- Negative H enhances **downwash-induced pitch-up moment**  
- This reduces required decalage for trim  
- Both wings operate closer to their **optimal lift conditions**  
- Result: **maximum cruise lift under stability constraints**

---
### Media
Schematic of tandem wing

![](/images/Op_schematic.png)

2d Optimisation plot

![](/images/Op_2d.png)

3d Optimisation plot

![](/images/Op_3d.png)

---
### Key Insights

- Lift is highly sensitive to **H and αd**, but weakly dependent on L  
- Optimal design balances:
  - aerodynamic efficiency  
  - trim requirement  
  - stability constraint  

- All optimisation methods converging to the same result confirms:
  → **well-conditioned and physically meaningful solution**

---
