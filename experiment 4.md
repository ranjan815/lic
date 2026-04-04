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

Input Common Mode Range (ICMR)

Minimum input voltage:

`V_ICM(min) = V_S + V_T = -0.7 + 0.36 = -0.34 V`

Maximum input voltage:

`V_ICM(max) = V_D + V_T ≈ 0 + 0.39 = 0.39 V`

Output Common Mode Range (OCMR)

Minimum output voltage:

`V_out(min) = V_S + V_ov = -0.7 + 0.34 = -0.36 V
`
Maximum output voltage:

`V_out(max) = V_DD = 0.9 V`

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

![Image description](https://github.com/ranjan815/lic/blob/main/images/ac%20analysis.png)

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

Comparison Insight 

Output resistance is limited by resistor  RD
Gain is lower compared to active load circuit
Bandwidth is higher due to lower output resistance


## Result

* Differential amplifier is successfully designed
  
* DC biasing is correct
  
* Linear operation observed for small signals
  
* Non-linear behavior observed for large signals
  
* Gain and bandwidth obtained as expected

---

## Conclusion

Conclusion

The MOS differential amplifier using resistive load is simple and provides stable operation with good bandwidth.

However, due to limited output resistance, the voltage gain is lower compared to active load amplifiers.

This circuit demonstrates the basic operation of differential amplifiers and highlights the tradeoff between gain and bandwidth.

---

# Circuit 2: Differential Amplifier with PMOS Active Load

---

## Working Principle

The circuit consists of two NMOS transistors (M1, M2) forming a differential pair, a PMOS current mirror load (M3, M4), and an NMOS transistor (M5) acting as a tail current source.

The differential input is:
`v_id = v_in1 − v_in2`

The tail current `I_SS` provided by M5 is steered between M1 and M2 depending on the input difference.

- If `v_in1 > v_in2` → M1 draws more current  
- If `v_in2 > v_in1` → M2 draws more current  

The PMOS current mirror converts this current difference into a single-ended output voltage.

Output relation:
`i_out = g_m · v_id`

Voltage gain:
`A_v = g_m · R_out`

where:
`R_out = r_o2 || r_o4`

**Justification:**  
Since both `r_o2` and `r_o4` are large, the effective output resistance is high. This directly increases voltage gain compared to resistive load circuits.

---

## DC Analysis

Total current:
`I_SS = P / (V_DD − V_SS) = 1.5 mW / 1.8 V = 0.833 mA`

Drain current:
`I_D = I_SS / 2 = 0.4165 mA`

Gate-source voltage:
`V_GS = 0 − (−0.7) = 0.7 V`

Overdrive voltage:
`V_ov = 0.7 − 0.36 = 0.34 V`

Drain-source voltage:
`V_DS ≈ 0.67 V`

**Justification:**  
Since `V_DS > V_ov`, both M1 and M2 operate in saturation, which is necessary for linear amplification and constant transconductance.

---

## Tail Current Source (M5)

Drain-source voltage:
`V_DS = 0.2 V`

Overdrive voltage:
`V_ov5 = 0.2 V`

Bias voltage:
`V_B = -0.34 V`

**Justification:**  
M5 operates near saturation and controls the total current `I_SS`. Any variation in M5 directly affects the differential pair performance, making it a critical element of the circuit.

---

## PMOS Active Load Operation

For M3 and M4:

`V_SD = 0.9 V`

**Justification:**  
Since `V_SD > |V_TP|`, both PMOS transistors remain in saturation. This ensures proper current mirroring and high output resistance.

Additionally, the current mirror forces:
`I_D3 = I_D4`

which helps convert differential current into output voltage efficiently.

---

## Width Calculation

For M1, M2:
`W ≈ 10.97 μm`

For M5:
`W ≈ 63.4 μm`

**Justification:**  
A larger width for M5 is required to sustain the full tail current. Proper sizing ensures accurate current distribution and stable biasing.

---

## Input Common Mode Range (ICMR)

`V_ICM(min) = -0.34 V`

`V_ICM(max) = 0.39 V`

**Justification:**  
This range ensures:

- M1 and M2 remain ON  
- M5 remains in saturation  
- PMOS load operates correctly  

Outside this range, the circuit loses proper differential operation.

---

## Output Common Mode Range (OCMR)

`V_out(min) = -0.36 V`

`V_out(max) = 0.65 V`

**Justification:**  
The output is limited by:

- Lower limit → NMOS saturation  
- Upper limit → PMOS saturation  

This defines the usable output swing.

---

## Transient Analysis

Linear condition:
`|v_id| < √2 · V_ov ≈ 0.48 V`

- 50 mV → Linear and undistorted output  
- 600 mV → Distorted output  

**Justification:**  
When input exceeds the limit, one transistor carries almost all current while the other turns OFF, leading to non-linear behavior.

Also, due to current mirror action, clipping is **asymmetric**, unlike resistive load circuits.

---

## Gain Analysis

Transient gain:
`A_v ≈ 4.2 V/V`

AC gain:
`A_v ≈ 3.02 V/V`

Gain in dB:
`≈ 9.59 dB`

**Justification:**  
Theoretically, gain should be high due to large `R_out`, but practical gain is reduced due to reduced `g_m` and finite output resistance.

---

## AC Analysis

Bandwidth:
`≈ 1.3585 GHz`

UGB:
`≈ 4.10 GHz`

**Justification:**  
Higher output resistance creates a dominant pole at the output node, reducing bandwidth compared to Circuit 1.

---

## Deviation Analysis

### 1. Tail Current Reduction

Actual current provided by M5 is lower than expected, which reduces:
`g_m = 2I_D / V_ov`

Lower `g_m` directly reduces gain.

---

### 2. Channel Length Modulation

`r_o = 1 / (λ · I_D)`

Since λ increases in short-channel devices, output resistance reduces, lowering gain.

---

### 3. Short Channel Effects

At `L = 360 nm`:

- Velocity saturation occurs  
- Mobility reduces  

This limits current and transconductance.

---

### 4. Bias Point Shift

Actual node voltages differ slightly from ideal values, affecting:

- `V_ov`
- Current distribution  

This changes overall circuit behavior.

---

### 5. Parasitic Capacitances

Capacitances (`C_gs`, `C_gd`) create poles that:

- Reduce high-frequency gain  
- Limit bandwidth  

---

## Key Observations

- Active load increases output resistance significantly  
- Gain is theoretically higher than resistive load  
- Bandwidth is reduced due to high impedance node  
- Circuit is more sensitive to bias variations  

---

## Final Insight

This circuit clearly shows that:

- Increasing output resistance improves gain  
- But reduces bandwidth  

This confirms the fundamental tradeoff in analog circuit design.

---

## Conclusion

The differential amplifier with PMOS active load is successfully designed and analyzed.

It provides higher gain due to increased output resistance, but practical non-idealities reduce the achievable gain. The circuit demonstrates proper differential operation, saturation conditions, and expected transient and AC behavior.

This design highlights the importance of current source accuracy, device sizing, and bias stability in achieving desired amplifier performance.
