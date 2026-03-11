# Hypersonic Low-Fidelity Solver

A Python-based low-fidelity aerodynamic solver for rapid estimation of hypersonic pressure loads on arbitrary 3D geometries. The tool applies classical local surface inclination methods to STL-based configurations and is intended for preliminary aerodynamic assessment during early design stages.

## Physical Basis

In the hypersonic limit, pressure distributions can often be approximated from the **local inclination of the surface relative to the incoming flow**, since disturbances remain highly compressed and the surface pressure depends primarily on local flow turning. Based on this principle, the solver implements several inviscid methods for rapid estimation of pressure coefficients.

Implemented models include:

- Newtonian theory
- Modified Newtonian theory
- Newton–Busemann method
- Tangent wedge method
- Shock-expansion theory

The **tangent wedge** and **shock-expansion** methods are only applicable when the local flow produces an **attached oblique shock**. The solver includes a check to verify attached-shock applicability before using these methods.

## Capabilities

- Imports arbitrary geometries from STL files
- Computes surface pressure coefficient distributions
- Generates 3D surface pressure maps
- Computes aerodynamic force components
- Estimates lift and drag coefficients
- Produces aerodynamic polars over angle of attack using reusable object-oriented solver classes

## Outputs

The solver is currently focused on the **pressure-drag contribution** and does **not** include skin-friction drag, boundary-layer effects, or real-gas/high-temperature corrections. It is therefore intended for **rapid preliminary analysis**, not as a replacement for high-fidelity CFD.

## Implementation

The code is written in an **object-oriented framework**, with separate classes for each aerodynamic method and reusable utilities for geometry import, post-processing, and force estimation. This structure allows rapid generation of codes for various use-cases such as angle-of-attack sweeps and method-to-method comparison.

## Example Result

*Example 2D pressure coefficient distribution computed on 10% thick biconvex airfoil.*

![Pressure coefficient distribution](/images/Hypersonic_solver.png)

*Example 3D pressure coefficient distribution computed on 10mm ogive.*

![Pressure coefficient distribution](/images/Hypersonic_solver2.png)

## Relevance

This tool was developed to support **early-phase configuration studies**, where rapid estimation of aerodynamic loads and trends is more valuable than full high-fidelity simulation cost. It is particularly useful for comparing candidate shapes, generating preliminary aerodynamic databases, and studying sensitivity to angle of attack. Future capabilities include coupling it to a simple 6DoF trajectory analysis tool.
