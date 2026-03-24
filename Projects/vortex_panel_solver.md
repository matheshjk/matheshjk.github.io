---
layout: default
title: Vortex Panel method
---

# Vortex Panel Method Solver

## Overview
This project implements aerodynamic solvers based on the **vortex panel method (VPM)** for two–dimensional potential flow analysis. The solver was first developed for **steady airfoil aerodynamics**, and later extended to simulate **unsteady aerodynamics of a pitching flat plate with vortex wake shedding**.

Panel methods are low–order aerodynamic tools widely used in early design and analysis. They assume **inviscid, incompressible and irrotational flow**, allowing the velocity field to be represented using singularity distributions on the body surface.

The work was carried out in two stages:

1. **Steady vortex panel solver** for airfoil analysis  
2. **Unsteady vortex panel solver** for a pitching flat plate

---

# 1. Steady Vortex Panel Solver

## Methodology
In the vortex panel method, the airfoil surface is discretized into a number of **straight panels**, each represented by a **constant-strength vortex element**. The unknown vortex strengths \( \gamma \) represent the circulation distribution required to satisfy the boundary conditions on the body.

For potential flow, the velocity field is obtained from the superposition of:

- freestream velocity  
- velocity induced by each vortex panel

The **no-penetration boundary condition** is enforced at control points located on the airfoil surface, ensuring that the flow remains tangent to the surface.

This results in a system of linear equations for the vortex strengths. To obtain a physically realistic solution, the **Kutta condition** is applied at the trailing edge, ensuring smooth flow leaving the airfoil.

Once the circulation distribution is known, the velocity on the surface can be computed and used to determine the **pressure coefficient distribution** using Bernoulli’s equation.

From this, the **lift coefficient** is obtained.

## Key Results

Airfoil discretization and panel geometry used in the solver:

![](/images/VP_distribution.png)

Pressure coefficient contour predicted by the vortex panel solver at 6deg AoA:

![](/images/VP_contour.png)

The obtained cp distribution is compared with the experimental resutls for NACA0012 airfoil.

![](/images/VP_cp.png)


These results demonstrate the ability of the panel method to capture the **pressure distribution and lift generation mechanisms** for airfoils in inviscid flow. 

---

# 2. Unsteady Vortex Panel Solver

## Methodology
The steady solver was extended to simulate **unsteady aerodynamics of a pitching flat plate**.

In unsteady flows, changes in circulation must satisfy **Kelvin’s circulation theorem**, which states that any change in bound circulation must be balanced by vorticity shed into the wake.

To model this behaviour, the solver introduces **discrete wake vortices** that are shed from the trailing edge at each timestep. The wake vortices are then convected downstream by the local velocity field induced by the freestream, the bound vortices on the plate, and the previously shed wake vortices.

The time-marching algorithm therefore consists of:

1. Solving the vortex panel system at each timestep  
2. Releasing a new wake vortex from the trailing edge  
3. Updating the positions of existing wake vortices  
4. Computing the resulting aerodynamic loads

This approach allows the solver to capture the **time-dependent development of circulation and wake dynamics**.

## Key Results

Wake vortex evolution behind the pitching flat plate:

![](/images/VPU_velocity.png)

lift coefficient hysteresis during the pitching motion:

![](/images/VPU_steady_unsteady.png)

Lift hysteresis at different reduced frequencies

![](/images/VPU_polar.png)

The unsteady solver captures the **dynamic lift response and wake vortex formation**, illustrating how changes in circulation generate vorticity that is shed into the wake.

---

## Repository
Solver implementation:

[Repository link](https://github.com/matheshjk/Vortex_panel_solvers.git)
