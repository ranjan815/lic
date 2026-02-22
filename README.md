#   CS AMPLIFIER

 INTRODUCTION :

 The Common Source (CS) amplifier is a basic MOSFET amplifier setup. In this design,
 the source terminal serves as the common reference for both the input and output circuits.
 The input signal connects at the gate terminal, while the amplified output comes from the 
 drain terminal. This setup is popular because it provides a significant voltage gain and 
 creates a 180° phase shift between the input and output signals. For the amplifier to function
 correctly in the linear region, the MOSFET must be biased in the saturation region. Choosing
 the DC operating point, also called the Q-point, ensures this. To assess the performance of 
 the CS amplifier, three types of analyses are done: DC Analysis establishes and verifies the
 proper operating bias point of the MOSFET. Transient Analysis observes the time-domain behavior
 and determines the voltage gain of the amplifier. AC Analysis examines the frequency response
 characteristics and calculates the bandwidth of the circuit.

 DESIGN CALCULATIONS

Given:
Supply voltage,
VDD = 1.5 V
Chosen drain current,
ID = 200 uA
as source is grounded therefore 
Vs=0V
VDS=VD

consider MOSFET operates in saturation region.

VD = VDD / 2
from given
VD = 1.5 / 2
VD = 0.75 V 

  calculation for Power Dissipation

P = VDD × ID
P = 1.5 × (200 × 10⁻⁶)
P = 0.3 mW
calulation for width (w):
   
given: ID = 200 uA = 200 × 10^-6 A, un = 273.8094 x 10^-4 ,Cox = 8.616 × 10^-3 ,VGS = 0.9 V ,VT = 0.366 V ,L = 180 nm

Vov = VGS − VT
Vov = 0.9 − 0.366
Vov = 0.534 V

unCox =un × Cox
unCox = 273.8094 × 8.616 × 10^-3
unCox ≈ 2.359 x10^-4

as MOSFET operating in saturation region, the Drain current euqation will be :

ID = (1/2) unCox (W/L) (Vov)^2

W = L[2ID / [µnCox (Vov)^2]]

W = 5.95 × (180 × 10^-9)

W =1.07 x 10^-6

Schematic
![Image description](https://github.com/ranjan815/lic/blob/main/Screenshot%202026-02-22%20230552.png)

# DC ANALYSIS

1)Open New Schematic to create a new circuit
2) place NMOSN transistor on the screen from the componenets.
3) change the name of the mosfet to CMOSN.
4)connect a DC voltage source  VDD = 1.5 V
5)Place a resistor RD between Drain and VDD
6)Directly  ground the source terminal 
7) connect a voltage source to gate and set it to 0.9v
8)Now click on simute
9)Select “Operating Point”
10) Place the .op command on the schematic
11)Run the simulation


DC O.P IMAGE
![Image description](https://github.com/ranjan815/lic/blob/main/Screenshot%202026-02-22%20231454.png)


Conclusion :

Based on the initial design equations, the calculated values were W = 1.07 um and RD = 3.75 kΩ.
However, to meet the necessary operating conditions, the transistor width was adjusted.
The goal was to achieve a drain voltage of 0.75 V and a drain current of 200 uA. By changing the
width parameter, we successfully established the desired Q-point. The final optimized width needed 
to maintain ID = 200 uA at a drain voltage of 0.75 V was found to be W = 1.572 um.

# TRANSIENT ANALYSIS

Procedure

1)apply input voltage as SINE(0.9 10m 1000) to gate terminal
2)Place transient command .tran and set stop time as 5m.
3) And run simulation and note  Vin and Vout peak to peak voltages
4) calculate the gain(Vout/vin) from the obtained voltages

Output graph:
![Image description](https://github.com/ranjan815/lic/blob/main/Screenshot%202026-02-22%20231148.png)

Input graph
![Image description](https://github.com/ranjan815/lic/blob/main/Screenshot%202026-02-22%20231259.png)


 Calculation for Gain calculations:

Vin =19.8mV
vout =44.3mv

Av = Vout/Vin
   =44.3/19.8
     =2.295
Avdb=20 log(Av)
 =20log(2.295)
     =7.21
     
  Theoritical gain calculation :

  Av =gmx rd
gm =2ID/VGS-VT
gm =0.74 x10^-3
rd =3.75 x10^3
Av = 0.74x 3.75
=2.7
Avdb =20 log(Av)
=8.6


# AC ANALYSIS

![Image description](https://github.com/ranjan815/lic/blob/main/WhatsApp%20Image%202026-02-22%20at%202.26.31%20PM.jpeg)


Procedure:

 1) apply the ac analysis command ( .ac dec 100 0.1 100G)
 2) Run the simulation and observe the frequency responce 

Output expected graph:





Conclusion:

From the experimental observations, the voltage gain of the amplifier was found to be Av = 2.295. 
The corresponding bandwidth was about 428.5 kHz. Using these values, the unit gain bandwidth was estimated
to be around 0.983 kHz. This is close to the unity gain frequency obtained from the simulation results. 
The slight variation, if there was any, is minimal. This shows a good correlation between theoretical 
calculations and simulated performance.

Overall experiment result:

The common source amplifier using a 180 nm channel length MOSFET was evaluated through transient analysis
to check its amplification behavior. From the simulation waveforms, the input signal amplitude measured
nearly 19.8 mV (peak-to-peak), while the output signal amplitude was about 44.3 mV (peak-to-peak).
Based on these measurements, the voltage gain of the circuit is calculated to be around -2.24. The negative
gain value shows a phase reversal between the input and output signals, which is a key feature of the 
common source configuration. The results confirm that the amplifier works well in the small-signal region.
Proper biasing keeps the MOSFET in the saturation (active) region, leading to stable and expected 
amplification performance. Overall, the experimental observations prove that the CS amplifier is designed
correctly and functions as intended.

Inference :

The observations from the experiment show that the common source MOSFET amplifier behaves as expected.
The increase in output signal amplitude compared to the input confirms that effective voltage amplification
has taken place. The clear 180° phase difference between the input and output waveforms shows the inverting
nature of the common source setup. The calculated voltage gain of nearly –2.24 indicates stable and moderate
amplification under small-signal conditions. Additionally, the lack of waveform distortion suggests that the
MOSFET stays properly biased in the saturation region during operation. Thus, both the predictions and the
simulation results match well, proving the design and performance of the amplifier circuit are reliable.
