# Experiment 04

## MOS Differential Amplifier using Resistive Load

---

##  Aim

To design and analyze a MOSFET differential amplifier using LTspice and evaluate its performance through **DC analysis, transient response, and AC frequency analysis**.

---

##  Introduction

A differential amplifier is a core analog circuit that amplifies the difference between two input signals while rejecting common-mode signals (noise).

This characteristic, called **Common Mode Rejection (CMR)**, makes it highly useful in precision electronics.

Applications include:

* Operational amplifiers
* Analog signal processing
* Communication circuits

---

##  Theory

### Differential Input

[
v_{id} = v_{in1} - v_{in2}
]

### Small Signal Gain

[
A_v = g_m \cdot R_{out}
]

### Transconductance

[
g_m = \frac{2I_D}{V_{ov}}
]

### Linear Operating Condition

[
|v_{id}| < \sqrt{2} \cdot V_{ov}
]

---

##  Design Specifications

| Parameter        | Value  |
| ---------------- | ------ |
| ( V_{DD} )       | +0.9 V |
| ( V_{SS} )       | -0.9 V |
| Total Supply     | 1.8 V  |
| Power Limit      | 1.5 mW |
| Tail Voltage     | -0.7 V |
| Channel Length   | 360 nm |
| Load Capacitance | 10 pF  |

---

## Circuit Description

The circuit consists of:

* Two matched NMOS transistors (M1, M2)
* Tail current source ( I_{SS} )
* Drain resistors ( R_D )
* Differential inputs

The output is taken from the drain nodes.

---

#  DC Analysis (Design Calculations)

## 1. Tail Current

[
I_{SS} = \frac{P}{V_{DD} - V_{SS}} = \frac{1.5 \times 10^{-3}}{1.8}
]

[
I_{SS} = 0.833 , mA
]

---

## 2. Drain Current

[
I_D = \frac{I_{SS}}{2} = 0.4165 , mA
]

---

## 3. Load Resistance

[
R_D = \frac{V_{DD}}{I_D} = \frac{0.9}{0.4165 \times 10^{-3}}
]

[
R_D \approx 2.16 , k\Omega
]

Practical value used:

[
R_D = 2.25 , k\Omega
]

---

## 4. Bias Voltages

[
V_G = 0 , V, \quad V_S = -0.7 , V
]

[
V_{GS} = 0.7 , V
]

Assuming ( V_T = 0.36 , V ):

[
V_{ov} = V_{GS} - V_T = 0.34 , V
]

---

## 5. Saturation Check

[
V_{DS} = 0 - (-0.7) = 0.7 , V
]

[
V_{DS} > V_{ov} \Rightarrow 0.7 > 0.34 , \checkmark
]

Therefore Transistors operate in saturation

---

## 6. Width Calculation

[
I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} V_{ov}^2
]

[
W = \frac{2 I_D L}{\mu_n C_{ox} V_{ov}^2}
]

Substituting values:

[
W \approx 10.97 , \mu m
]

---

##  DC Results Summary

| Parameter      | Value     |
| -------------- | --------- |
| ( I_{SS} )     | 0.833 mA  |
| ( I_D )        | 0.4165 mA |
| ( V_{GS} )     | 0.7 V     |
| ( V_{DS} )     | 0.7 V     |
| ( V_{ov} )     | 0.34 V    |
| ( R_D )        | 2.25 kΩ   |
| Output Voltage | -37 mV    |

---

#  Transient Analysis

## 1. Linear Range

[
|v_{id}| < \sqrt{2} \cdot V_{ov} = 0.48 , V
]

---

## 2. Case Analysis

### Case 1: ( v_{id} = 200 , mV )

[
200 , mV < 480 , mV , \checkmark
]

* Output is sinusoidal
* No distortion
* Gain ≈ 3 V/V

---

### Case 2: ( v_{id} = 600 , mV )

[
600 , mV > 480 , mV , \checkmark
]

* Output is clipped
* One transistor OFF
* Non-linear behavior

---

##  Transient Summary

| Parameter | Linear     | Non-linear |
| --------- | ---------- | ---------- |
| Input     | 200 mV     | 600 mV     |
| Output    | Sinusoidal | Distorted  |
| Operation | Linear     | Non-linear |

---

#  AC Analysis

## 1. Simulated Results

| Parameter | Value    |
| --------- | -------- |
| Gain      | 3.55 V/V |
| Gain (dB) | 11 dB    |
| Bandwidth | 5.5 GHz  |
| UGB       | 19.5 GHz |

---

## 2. Theoretical Gain

[
g_m = \frac{2I_D}{V_{ov}} = 2.45 , mA/V
]

[
A_v = g_m \cdot R_D
]

[
A_v = 5.51 , V/V
]

---

## 3. Gain Comparison

| Type        | Gain     |
| ----------- | -------- |
| Theoretical | 5.51 V/V |
| Simulated   | 3.55 V/V |

---

## 4. Reason for Difference

* Channel length modulation
* Mobility degradation
* Parasitic capacitances
* Non-ideal MOS behavior

---

#  Conclusion

The MOS differential amplifier was successfully designed and analyzed.

### Final Observations:

* Correct DC biasing achieved
* Saturation condition verified
* Linear operation confirmed for small inputs
* Non-linearity observed for large inputs
* Moderate gain with very high bandwidth achieved

The results closely match theoretical expectations, validating the design.

---

##  Result

The circuit operates correctly under all conditions (DC, transient, AC) and satisfies the design constraints.

---
