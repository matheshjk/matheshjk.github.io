---
layout: default
title: Tiltrotor Bicopter UAV Design
---

# Tiltrotor Bicopter UAV Design and Prototype Development

## Overview
This bachelor final project focused on the design, fabrication, and testing of a **tiltrotor bicopter UAV** intended to combine the **vertical take-off and landing capability of multirotors** with the **improved cruise efficiency of fixed-wing aircraft**.

Conventional hybrid VTOL configurations often use separate lift and cruise propulsors, which leaves some motors inactive during forward flight and increases drag. The concept explored in this project was a **tiltrotor bicopter**, where the same two motors provide both hover thrust and forward propulsion through a tilting mechanism.

The project combined:

- conceptual aircraft design  
- low-order aerodynamic analysis in XFLR5  
- mechanical design of a tilting motor mechanism  
- FEA-based structural verification  
- prototype fabrication and hover-mode testing  

The main objective was to evaluate whether a tiltrotor bicopter could provide a more efficient alternative to a conventional bicopter or hybrid VTOL layout for small UAV applications.

---

# Design Methodology

## Problem Statement
Multirotors are highly effective for take-off, landing, and low-speed manoeuvring, but become inefficient in cruise because the propellers must continuously generate lift while also producing forward motion. Fixed-wing aircraft are far more efficient in cruise, but require a runway and cannot hover.

This project aimed to address that tradeoff by developing a **hybrid eVTOL system** that could operate efficiently in both regimes. The specific project statement was to develop an optimised hybrid UAV design to reduce the inefficiencies associated with forward flight in conventional multirotor systems. :contentReference[oaicite:1]{index=1}

---

## Concept Selection
The selected concept was a **tiltrotor bicopter** inspired by the operating logic of larger tiltrotor aircraft such as the V-22 Osprey. In this configuration:

- the motors point upward during take-off, landing, and hover  
- the motors tilt forward during transition and cruise  
- the same propulsion system is used for both vertical and forward flight  

This avoids the drag penalty of idle lift motors found in many hybrid VTOL concepts and also offers the possibility of reducing wingtip-vortex effects through the placement and rotation direction of the tip-mounted propellers. :contentReference[oaicite:2]{index=2}

---

# Aerodynamic Design

## Airfoil Selection
A preliminary airfoil comparison was carried out in **XFLR5** using low-Reynolds-number aerodynamic data over a range of operating conditions.

Three candidate airfoils were compared:

- SD7032  
- Clark Y  
- NACA 2415  

The comparison showed that SD7032 and Clark Y had broadly similar aerodynamic performance, while NACA 2415 produced significantly lower aerodynamic efficiency in the relevant operating range. Although SD7032 showed slightly stronger lift performance, **Clark Y** was selected because its flat lower surface made fabrication and wing mounting much simpler. :contentReference[oaicite:3]{index=3}

---

## Wing Sizing
A rectangular wing was adopted for simplicity, and the design was iterated using **Vortex Lattice Method (VLM)** analysis in XFLR5.

### Initial Wing
The first wing design used:

- span = 0.8 m  
- chord = 0.2 m  
- area = 0.16 m²  
- aspect ratio = 4  

This configuration was found to be insufficient to generate the required lift for the target **MTOW of 1.5 kg**. Even at higher angles of attack, the predicted lift was not enough to support the full aircraft weight. :contentReference[oaicite:4]{index=4}

### Final Wing
A revised wing was then developed with:

- span = 1.0 m  
- chord = 0.2 m  
- area = 0.2 m²  
- aspect ratio = 5  

This updated design was predicted to generate about **20 N of lift at 7° angle of attack** for a cruise speed of **15 m/s**, making it sufficient to support the aircraft at the intended maximum take-off weight. :contentReference[oaicite:5]{index=5}

---

## Stability Analysis
The combined wing-tail configuration was analysed in XFLR5 to evaluate trim and static stability.

The final aircraft geometry used:

- 5° wing tilt  
- -1° elevator tilt  
- NACA0015 tail surfaces  
- CG located near 25% chord  

The resulting configuration showed a **negative slope of pitching moment coefficient with angle of attack**, indicating static longitudinal stability. The trim condition occurred at about **2° angle of attack**, where the aircraft produced roughly **20 N of lift**, **1.38 N of drag**, and a **CL/CD of about 14.5**. :contentReference[oaicite:6]{index=6}

---

# Tilt Mechanism Design

## First Design Iteration
The initial tilt mechanism used separate mounts for the motor and servo, directly coupling the motor pod to the servo output. These parts were fabricated using **PLA via FDM 3D printing**.

While the mechanism worked under gradual manual inputs, it failed when coupled to the flight controller. Oscillatory control inputs introduced loads that the design could not withstand reliably, so a redesign was required. :contentReference[oaicite:7]{index=7}

---

## Second Design Iteration
A second design was developed using:

- an integrated motor-servo mount  
- a pair of **helical gears** with 1:1 ratio  
- a bearing-supported rotating mount around the wing spar  

The design intent was to place the **centre of gravity of the tilt mechanism on the wing spar axis**, so that the aircraft CG would remain nearly unchanged during transition between hover and cruise.

The main gear design parameters were:

- centre distance = 41.5 mm  
- module = 2 mm  
- teeth = 20  
- helix angle = 15°  
- pressure angle = 20°  
- face width = 10 mm :contentReference[oaicite:8]{index=8}

---

# Structural Verification

## FEA of Mount, Gears, and Wing Spar
Structural simulations were carried out in **ANSYS 2022 R1** for the main parts of the tilt mechanism and wing structure.

### Mount and Gears
The mount and gears were analysed using PLA material properties. The gear loading was based on the **MG996R servo stall torque**, and the simulations showed that the maximum induced stress was about **43 MPa**. :contentReference[oaicite:9]{index=9}

### Wing Spar
The wing spar was modelled as an aluminium tube with symmetric loading assumptions. It was subjected to:

- a vertical force of **10.3 N**  
- a reaction torque of **0.39092 Nm** from motor operation  

The resulting maximum stress was about **24 MPa**, and the maximum deformation was about **2 mm**, both of which were within acceptable limits for the intended application. :contentReference[oaicite:10]{index=10}

These results indicated that the final structural design was adequate for prototype operation.

---

# Prototype Development and Testing

## Bicopter Prototype
To test the control concept in hover before implementing full fixed-wing transition, a **bicopter prototype** was built using the same core propulsion and tilt-mechanism hardware.

The electronics setup included:

- 2 BLDC motors  
- 2 ESCs  
- 2 servos  
- KK2.1.5 flight controller  
- LiPo battery  
- RC receiver and transmitter  

The prototype centre of gravity was balanced at the intersection of the spars, and the wiring and control-channel setup were configured for differential thrust and servo-based attitude control. :contentReference[oaicite:11]{index=11}

---

## Hover Testing and Iterative Corrections
Several hover-mode test iterations were carried out, and the prototype behaviour was improved step by step.

### Initial Issues Identified
The early tests revealed multiple problems:

- ESC mismatch causing asymmetric motor response  
- undesirable servo drift caused by integral gain settings  
- mechanical failure of the tilt mechanism under counter-torque loads  
- unstable behaviour caused by incorrect self-level settings  
- vibration issues on one motor side  

### Corrective Actions
The main corrective steps included:

- calibrating the ESCs with the flight controller  
- setting the **I gain to zero** during initial testing  
- bonding the tilt mechanism securely to the spar  
- enabling self-level mode  
- reducing vibration by removing imbalance sources on the motor assembly  

After these corrections, the prototype became significantly more stable in static hover testing on the test stand. The final report notes that free flight would still require further tuning, especially to mitigate vibration and refine the control gains. 

---

# Key Results

The project achieved the following main outcomes:

- Developed a full conceptual design for a **tiltrotor bicopter UAV**  
- Selected **Clark Y** as the most practical airfoil for the intended Reynolds-number range  
- Sized a **1 m span, 0.2 m chord wing** capable of supporting the 1.5 kg MTOW at 15 m/s  
- Obtained a **statically stable aircraft configuration** with trim near **2° AoA**  
- Designed and structurally validated a **helical-gear-based tilt mechanism**  
- Fabricated and assembled a working bicopter prototype  
- Improved hover behaviour through iterative testing and debugging of both hardware and control settings  

The final prototype did not yet complete full free-flight validation, but the project successfully demonstrated the design workflow and established a functioning hardware and control architecture for further development. :contentReference[oaicite:13]{index=13}

---

# Key Figures



Airfoil comparison and wing sizing:

![](/images/tiltrotor_airfoil_selection.png)

Trim and stability analysis:

![](/images/tiltrotor_stability.png)

Tilt mechanism Design 1:

![](/images/tiltrotor_design1.png)

Tilt mechanism Design 2:

![](/images/tiltrotor_design2.png)

Tiltrotor Design:

![](/images/tiltrotor_design.png)

Prototype and hover-test setup:

![](/images/tiltrotor_prototype.png)

---

## Relevance
This project was one of my earliest attempts at combining **aerodynamic design, structural design, controls integration, and prototyping** into a single UAV development effort.

Although it was a bachelor-level project, it gave me practical experience in:

- conceptual aircraft design  
- low-order aerodynamic analysis  
- CAD and additive manufacturing  
- FEA-based structural verification  
- flight-controller setup and debugging  
- prototype iteration through testing  

It also shaped my later interest in bridging aerodynamic modelling with real-world implementation and system-level design.

---

