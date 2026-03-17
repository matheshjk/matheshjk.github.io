---
layout: default
title: Method of Characteristics Solver
---

# Method of Characteristics Solver for an Underexpanded Jet

A Python-based Method of Characteristics (MoC) solver developed to compute the two-dimensional flow field of an underexpanded supersonic jet. The solver resolves the characteristic structure generated when a jet exits a nozzle at a pressure higher than ambient, producing Prandtl–Meyer expansion waves, successive reflections, and eventual breakdown of the isentropic solution as shock formation is approached.

## Physical Basis

When a supersonic jet exits into a lower ambient pressure environment, the flow expands through a Prandtl–Meyer fan formed at the nozzle lip. In two-dimensional inviscid supersonic flow, the solution can be constructed along the characteristic families:

- **Γ+ characteristics**
- **Γ− characteristics**

Along these lines, the compatibility relations are:

- **ν + θ = constant** along **Γ−**
- **ν − θ = constant** along **Γ+**

where:

- **ν** is the Prandtl–Meyer function
- **θ** is the local flow turning angle

Using these relations, the jet plume can be marched point-by-point through successive reflection regions until the characteristic solution ceases to remain physically valid, indicating the onset of shock formation.

## Implementation

The solver was written in Python and computes:

- characteristic-line intersections
- local turning angles
- Prandtl–Meyer angles
- Mach number distribution
- static pressure distribution from isentropic relations
- characteristic net and Mach-number contours

The Prandtl–Meyer relation is inverted numerically to recover Mach number at each node, and characteristic intersections are obtained from the local line geometry.

## Capabilities

- Models the initial expansion fan from the nozzle exit
- Resolves successive reflected characteristic regions in the jet plume
- Computes the evolving Mach-number field in the underexpanded jet
- Identifies the region where the isentropic characteristic solution breaks down as shock formation is approached
- Produces flow visualizations for interpretation of jet structure

## Example Setup

A representative case was solved for:

- exit Mach number: **2**
- exit pressure: **2 × ambient**
- gas: **air**
- ratio of specific heats: **γ = 1.4**

The number of characteristics is user-defined, allowing control over solution resolution.

## Result


![Pressure distribution](/images/MoC1.png)
![Mach distribution](/images/MoC2.png)

## Relevance

This project demonstrates the application of classical compressible-flow theory to construct a full jet plume solution from first principles. It was developed to strengthen intuition in gas dynamics, characteristic methods, and numerical flow reconstruction, while also providing a reusable Python tool for visualising underexpanded jet structure.

## Skills Demonstrated

- compressible flow modelling
- Method of Characteristics
- Prandtl–Meyer expansion theory
- numerical root finding
- Python scientific computing
- scientific visualization
