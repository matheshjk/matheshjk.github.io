# Solid Rocket Motor Analysis and Hot-Fire Test Evaluation

## Overview
This project involved the analysis of a **solid rocket motor (SRM)** using both **analytical internal ballistics modelling** and **experimental hot-fire test data**.

The objective was twofold:

1. Use an **analytical model** to estimate chamber pressure and motor performance.
2. Analyse **hot-fire test datasets** from multiple test cases to investigate the effects of:
   - propellant grain surface coatings
   - ignitor configurations

The analytical model was first used to predict the behaviour of one test case. The results were then compared with experimental measurements to evaluate how closely the simplified internal ballistics model matched the real motor behaviour.

Subsequently, different experimental test cases were compared to assess how **grain coatings and ignitor designs influence motor ignition and pressure development**.

---

# Experimental Setup

Hot-fire testing was conducted by DARE team on a laboratory-scale solid rocket motor equipped with instrumentation to measure **chamber pressure and thrust history** during motor operation.

![](/images/srm_test_setup.png)

The test campaign included multiple configurations with variations in:

- **grain surface coatings**
- **ignitor compositions and configurations**

These variations were introduced to study their effect on ignition behaviour and pressure evolution.

---

# Analytical Internal Ballistics Model

The analytical model describes the relationship between **propellant burn rate, chamber pressure and mass flow rate through the nozzle**.

The propellant burn rate follows a pressure-dependent law:

r = aPⁿ

Using this relationship, the following quantities are evaluated:

- propellant regression rate
- gas generation rate
- chamber pressure
- nozzle mass flow rate

In this project the opensource BurnSim code was used. It provides an estimate of the **steady operating conditions of the motor**, allowing comparison with measured test data.

---

# Experimental Data Analysis

The hot-fire dataset was analysed to extract key propulsion parameters from the recorded pressure-time histories.

The analysis focused on:

- ignition delay
- pressure rise rate
- peak chamber pressure
- burn duration

One representative test case was compared directly with the **analytical internal ballistics prediction** in order to evaluate the validity and limitations of the simplified model.

---

# Hypothesis Testing

The experimental dataset was used to test two hypotheses regarding motor performance.

### Hypothesis 1 – Effect of Grain Coating
Different grain surface coatings were expected to influence the **ignition characteristics and initial burn behaviour**.

Comparison of pressure histories between coated and uncoated grains showed that **coated grains produced a more stable pressure rise and improved ignition consistency**, indicating that the coating enhanced the initial combustion behaviour of the propellant surface.

### Hypothesis 2 – Effect of Ignitor Configuration
Different ignitor combinations were hypothesised to influence the **initial energy release and pressure build-up during ignition**.

Analysis of the pressure–time curves showed that the **thermite configuration resulted in the shortest ignition delay and fastest pressure build-up**, while other ignitor configurations produced slower ignition transients.

---

# Key Results

Grain Burn Back results:

![](/images/SRM_analytical.png)

Example pressure-time history from hot-fire testing:

![](/images/SRM_hotfire.png)

### Comparison Between Analytical Model and Static Fire Test

| Parameter | Grain burn back – no inhibitor | Static fire – grains coated | Error percentage |
|-----------|--------------------------------|------------------------------|------------------|
| Burn time [s] | 1.14 | 1.98 | 73.7% |
| Total impulse [Ns] | 541.68 | 514.33 | 5.0% |
| Maximum Specific Impulse [s] | 149.86 | 137.66 | 8.9% |
| Apogee [m] | 1306.6 | 1290 | 1.3% |


The analysis showed that while the analytical internal ballistics model provides reasonable estimates of steady-state motor behaviour, experimental results reveal additional effects associated with ignition dynamics and propellant surface conditions.

---

## Repository
Analysis scripts and data processing tools:

`[Repository link placeholder]`
