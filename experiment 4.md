# Experiment 04

## Differential Amplifier Analysis

---

## Aim

To design and simulate a MOSFET differential amplifier using LTspice and analyze its performance using DC, transient, and AC analysis.

---

## Introduction

A differential amplifier is one of the basic building blocks in analog circuits. It amplifies the difference between two input signals and rejects common signals.

These amplifiers are widely used in operational amplifiers and analog front-end circuits due to good noise rejection.

---

## Theory

A differential amplifier works by comparing two input voltages.

The differential input is given by
`v_id = v_in1 − v_in2`

The circuit consists of two identical MOSFETs sharing a constant current source.

When both inputs are equal, current splits equally:
`I_D1 = I_D2 = I_SS / 2`

When one input increases, more current flows through that transistor and less through the other.

For proper operation, MOSFETs must be in saturation:
`V_DS ≥ V_GS − V_T`

The voltage gain is given by:
`A_v = g_m · R_D`

where transconductance is:
`g_m = 2I_D / V_ov`

and
`V_ov = V_GS − V_T`

For linear operation:
`|v_id| < √2 · V_ov`

---

## Design Specifications

| Parameter      | Value  |
| -------------- | ------ |
| VDD            | 0.9 V  |
| VSS            | -0.9 V |
| Power          | 1.5 mW |
| Tail Voltage   | -0.7 V |
| Channel Length | 360 nm |

---

## Circuit Description

The circuit consists of:

* Two NMOS transistors (M1, M2)
* Tail current source
* Load resistors
* Input voltages applied at gates
* 
  ![Image description](https://github.com/ranjan815/lic/blob/main/images/circuit.png)

The output is taken from the drain terminals.

---

## DC Analysis

Total current:
`I_SS = P / (V_DD − V_SS)`

`I_SS = 1.5 mW / 1.8 V = 0.833 mA`

Drain current:
`I_D = I_SS / 2`

`I_D = 0.833 / 2 = 0.4165 mA`

Load resistance:
`R_D = V_DD / I_D`

`R_D = 0.9 / (0.4165 × 10⁻³) ≈ 2.16 kΩ`

(Used value: 2.25 kΩ)

Voltages:
`V_GS = 0 − (−0.7) = 0.7 V`

`V_ov = V_GS − V_T = 0.7 − 0.36 = 0.34 V`

`V_DS = 0 − (−0.7) = 0.7 V`

Since
`V_DS ≥ V_ov`

both transistors operate in saturation.

---

## Width Calculation

`W = (2 I_D L) / (μ_n C_ox V_ov²)`

`W = (2 × 0.4165×10⁻³ × 360×10⁻⁹) / (236.5×10⁻⁶ × (0.34)²)`

`W ≈ 10.97 μm`

---

![Image description](https://github.com/ranjan815/lic/blob/main/images/op%20.png)

## Transient Analysis

Differential input:
`v_id = v_in1 − v_in2`

Linear condition:
`|v_id| < √2 · V_ov`
`|v_id| < 1.414 × 0.34 ≈ 0.48 V`

### Case 1: Small Input (200 mV)

* Output is sinusoidal
* No distortion
* 
   ![Image description](https://github.com/ranjan815/lic/blob/main/images/transient%20200m.png)

### Case 2: Large Input (600 mV)

* Output is clipped
* One transistor turns OFF

  ![Image description](https://github.com/ranjan815/lic/blob/main/images/transient%20600m.png)

---

## AC Analysis

![Image description](__paste__image__link__here___)

Gain:
`A_v = 3.55 V/V`

Gain in dB:
`A_v(dB) = 20 log(3.55) ≈ 11 dB`

Bandwidth:
`f_-3dB ≈ 5.503 GHz`

Gain Bandwidth Product:
`GBW = A_v × f_-3dB`
`GBW = 3.55 × 5.503 GHz ≈ 19.5 GHz`

---

## Result

* Differential amplifier is successfully designed
* DC biasing is correct
* Linear operation observed for small signals
* Non-linear behavior observed for large signals
* Gain and bandwidth obtained as expected

---

## Conclusion

The MOS differential amplifier was designed and analyzed using LTspice.
The circuit satisfies the required conditions and shows proper operation in DC, transient, and AC analysis.

---

##  Result

The circuit operates correctly under all conditions (DC, transient, AC) and satisfies the design constraints.

---
