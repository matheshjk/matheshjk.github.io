# CFD Solver for Lid-Driven Cavity Flow

## Overview
This project involves the development of a **numerical CFD solver** to simulate the classical **lid-driven cavity flow** problem. The lid-driven cavity is a benchmark problem in computational fluid dynamics used to validate numerical methods for solving the **incompressible Navier–Stokes equations**.

In this configuration, fluid is contained inside a square cavity where the **top wall moves with constant velocity**, while the other walls remain stationary. The motion of the lid drives circulation inside the cavity, generating a primary vortex and secondary vortical structures depending on the Reynolds number.

The objective of this work was to implement a CFD solver capable of predicting:

- velocity field inside the cavity  
- vortex formation and recirculation patterns  
- effects of Reynolds number on flow structure

---

# Numerical Method

## Governing Equations
The flow is governed by the **2D incompressible Navier–Stokes equations** together with the continuity equation.

These equations describe conservation of:

- mass  
- momentum in the x-direction  
- momentum in the y-direction

The numerical solver computes the velocity and pressure fields within the cavity domain by discretizing these governing equations.

## Solver Implementation
The cavity domain was discretized using a structured computational grid. Discrete differential operators were assembled using **incidence matrices together with Hodge matrices**, allowing the Navier–Stokes equations to be expressed in a structured algebraic form on the computational grid. The governing equations were solved using a finite-difference based approach.

The main steps of the numerical algorithm include:

1. Discretisation of the Navier–Stokes equations on a structured grid  
2. Application of no-slip boundary conditions on the cavity walls  
3. Imposition of constant velocity on the moving lid  
4. Iterative solution of velocity and pressure fields  
5. Convergence monitoring of residuals

The numerical implementation allows simulation of the internal recirculating flow patterns that develop due to the motion of the lid.

---

# Flow Physics

The moving lid introduces momentum into the cavity, creating a **primary vortex** occupying the center of the cavity. As the Reynolds number increases, **secondary vortices** appear near the corners of the cavity due to viscous boundary layer interactions.

The lid-driven cavity is widely used to evaluate CFD solvers because the flow contains several important features:

- strong shear near the moving lid  
- recirculation zones  
- corner vortices  
- viscous diffusion of momentum

Accurate prediction of these structures indicates correct implementation of the numerical scheme.

---

# Key Results

Velocity against benchmark cavity flow solution:

![](/images/CFD2_velocity.png)

Streamlines against benchmark cavity flow solution:

![](/images/CFD2_vorticity.png)

Pressure along centerlines for various grid resolutions against cavity flow solution:

![](/images/CFD2_line_pressure.png)

These results illustrate the formation of the primary vortex within the cavity and demonstrate the solver’s ability to reproduce the characteristic flow behaviour of the lid-driven cavity benchmark.

---

## Repository
Solver implementation:

`[Repository link placeholder]`
