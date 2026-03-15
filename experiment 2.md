#  CS AMPLIFIER

Aim : Design the amplifier configurations using tsmc in LT spice.Compare the
performance and justify the interpretations

 a)

 b)

 c)

Procedure or steps : 

1) first, make the circuit connections as shown above.
2) Connect the DC power supplly to the gate terminal.
3) Connect the source terminal to the ground.
4) Select the input voltage  VDD to 1.5 V .
5) Using formula for power , P=VI we will get the values of Id as , Id = 
6) we have to get the output current , Id and output voltage for the given circuits by adjusting 
the values of W of both MOSFET's.
2) Perform DC analysis and fix the operating point to ensure all the transistors 
are in saturation region.Calculate the power.
3) Perform transient analysis maintaining the transistors in saturation region and
behaves as linear amplifier.
4) Extract the gain, output swing (maximum), input swing (maximum) and compare with
theoretical values.
4) Perform AC analysis and extract Gain, BW, UGB, 3 dB BW, with CL load.
5) Perform step 1 to 4 for all the three configurations and compare the parameters.

Circuit 1 :

# DESIGN CALCULATIONS FOR CIRCUIT A

Given: Supply voltage, VDD = 1.5 V Chosen drain current, threshold voltage = 0.36v
consider Vov =0.25v so that both the MOSFET's operates in saturation region and P<=0.5mW

Bias current (ID) :

```
P <= VDD * ID
0.5 mW ≥ 1.5 x ID

ID ≤ 0.33 mA

Chosen operating current:

ID = 200 uA
 ```

for NMOS(M1) :

      Vov = Vgs - Vt
      0.25 = Vgs - 0.36
      Vgs = 0.61v

      Vgs = Vg - Vs
      Vg = Vgs + Vs 
         Vg = 0.81v

we know that ID = (1/2) un cox (W/L) Vov^2

            W = (2 x 180n x 200 x 10^-6)/ (273.89 x 10^-4 x 8.616 x 10^-3 x 0.25^2)
            W =   4.2*10^-6
            
for PMOS(M2) :

```
  Vov = Vsg - Vt
  Vsg = 0.25 + 0.39
  Vsg = 0.64v

  Vg = Vs + Vsg
  Vg = 0.86v

  ID = (1/2) up cox (W/L) Vov^2
 
W = (2 x 180n x 200 x 10^-6)/ (115.6 x 10^-3 x 10^-4 x 8.616 x 10^-3 x 0.25^2)
W = 11.8*10^-6
```

MAXIMUM OUTPUT VOLTAGE AND RESISTOR VALUE :
```

  Vo = VDD/2 + 0.2
  Vo = 0.95v

  VRs = ID*Rs
  Rs = 1K Ohm
```
  
# DC ANALYSIS:


schematic :


based on the initial design equations, the calculated values of  Width of both the mosfet were w1=4.2*10^-6  um and w2= 11.8*10^-6 um Rs = 1kΩ.
However, to meet the necessary operating conditions, the transistor width was adjusted. The goal was to achieve a drain voltage of  0.95 V and a drain current of 200 uA. By changing the width parameter, we successfully established the desired Q-point. The final optimized width needed to maintain ID = 200 uA at output voltage of   V was found to be W1 = 26*10^-6  um and w2= 40*10^-6 um

# TRANSIENT ANALYSIS


Procedure

1) apply input voltage as SINE(__ 10m 1000) to gate terminal
2) Place transient command .tran and set stop time as 5m.
3) And run simulation and note  Vin and Vout peak to peak voltages
4) calculate the gain(Vout/vin) from the obtained voltages

 ** INPUT VOLTAGE



 ** OUTPUT VOLTAGE



**Calculation for Gain calculations:
```

Vin(p-p) = 19.9 mV
vout(p-p) = 0.206 mv

Av = Vout/Vin
   =  10.34 v/v
     =
Avdb=20 log(Av)
 =20log(10.34)
     = 20.294 dB
  ```   
  
   # AC ANALYSIS

 
Procedure:

 1) apply the ac analysis command ( .ac dec 100 0.1 100G)
 2) Run the simulation and observe the frequency responce 

**Output expected graph:

 Gain bandwidth product = Av * gain at -3dB
  GBP=10.345 x 316.68 Mhz GBP=3.269Ghz

  CIRCUIT 2 :
  
 ** Schematic diagram

# DESIGN CALCULATIONS FOR CIRCUIT :

 Given: Supply voltage, VDD = 1.5 V Chosen drain current, threshold voltage for NMOS = 0.36v and for PMOS = -0.39 V
consider Vov =0.25v so that both the MOSFET's operates in saturation region and P<=0.5mW

Bias current (ID) :
```
P <= VDD * ID
0.5 mW ≥ 1.5 x ID

ID ≤ 0.33 mA

Chosen operating current:

ID = 200 uA
```
For mosfet 3 :
```
VGS2	=VTHn + Vov	0.36 + 0.25
VGS2= 0.61 V
```
Source Voltage	Ground	0 V
Gate Voltage	Bias value	0.61 V
Drain Voltage	VS1 =	0.30 V
VDS2 =	VD2 − VS2
VDS2 = 0.30 V
```
Therefore 
 VDS2 ≥ Vov
 0.30 ≥ 0.25
```
Thus M2 operates in saturation.

For mosfet 1 :

```
Gate Voltage	Given
VG = 0.91 V
Source Voltage
VS1 =	0.30 V
VGS1 =	VG1 − VS1	
= 0.91 − 0.30 
VGS1= 0.61 V
```
```
Vout = VDS1 + VS1

VDS1	= VDD / 2
= 1.5 / 2
VDS1	= 0.75 V
Vout =	0.75 + 0.30	
Vout = 1.05 V

```
```
VDS1 ≥ Vov	0.75 ≥ 0.25
```
 Hence M1 remains in saturation

PMOS Active Load (Mosfet 3):
```
Source Voltage (VS) =	VDD	= 1.5 V
Gate Voltage	Given	
VG = 0.91 V
VSG3 =	VS − VG	
= 1.5 − 0.91 
VSG3 = 0.59 V
```
```
VSD3 =	VS − Vout
=1.5 − 1.05
VSD3 = 0.45 V

VSD3 ≥ Vov	
=0.45 ≥ 0.25
```
Thus PMOS load operates in saturation.

Width Calculation :
```
For NMOS :
From current equation: ID = (1/2) un cox (W/L) Vov^2
W = 5u

And For PMOS :
W = 11.83u
```
# DC ANALYSIS

**schematic
![Image description](https://github.com/ranjan815/lic/blob/main/images/Screenshot%202026-03-15%20223631.png?raw=true)

based on the initial design equations, the calculated values of  Width of the 3 mosfet were W1 = W2 = 5 um and W3 = 11.83 um 
However, to meet the necessary operating conditions, the transistor width was adjusted. The goal was to achieve a drain voltage of  1.05 V and a drain current of 200 uA. By changing the width parameter, we successfully established the desired Q-point. The final optimized width needed to maintain ID = 200 uA at output voltage of 1.05 V was found to be W1 = w3 =   um and w2=  um


# TRANSIENT ANALYSIS :


**input and output graph 



**Calculation for Gain calculations:
```
Vin(p-p) = 0.3256  mV
vout(p-p) = 0.01908 mv

Av = Vout(p-p) / Vin(p-p)	
= 0.03256 / 0.01908
   Av  = 	1.71 V/V
Avdb=20 log(Av)
 =20log(1.71)
  = 4.66 dB

```
 # AC ANALYSIS

 **Output expected graph:


**Frequency Response Results
```
 Gain bandwidth product = Av * gain at -3dB
 = 
  GBP =   Mhz GBP=   Ghz
  ```
  # CIRCUIT 3 :

  ** Schematic diagram

  # DESIGN CALCULATIONS FOR CIRCUIT :
  
Given: Supply voltage, VDD = 1.5 V Chosen drain current, threshold voltage for NMOS = 0.36v and for PMOS = -0.39 V
consider Vov =0.25v so that both the MOSFET's operates in saturation region and P<=0.5mW Bias current ID = 200uA  

For mosfet 3 :

The gate and drain are shorted Therefore:
VG = VD          

The source of M3 is connected to ground.                                            VS3	0 V  

Using the selected bias point,  
VG3 = VD3	= 0.5 V     

Since this node is directly connected to the source of M1, we obtain              VS1	0.5 V  

The diode-connected NMOS establishes a stable bias node where
VG3 = VD3 = VS1 = 0.5 V,

allowing the circuit to maintain the required current (~200 µA).

For mosfet 1 :

 To maintain the required drain current in M1, the gate–source voltage must satisfy        
 VGS1 = VTH + VOV = 0.36 + 0.25
 VGS1=0.61 V
Since
VS1 = 0.5 V

the gate voltage becomes  
```
VG1 = VS1 + VGS1
= 0.5 + 0.61	
VG1 = 1.11 V  
```
Therefore,
VIN(DC) ≈ 1.11 V

This bias keeps M1 operating in saturation.   

Output Voltage: 
```
VDS ≈ VDD / 2 
= 1.5 / 2
VDS ≈ 0.75 V  
Vout = VDS + VS1
= 0.75 + 0.5	
Vout ≈ 1.25 V
```                  
This operating point allows adequate output swing while maintaining saturation.

For mosfet 2 : 
```
VSG2 = (VTHp + VOV)
= 0.39 + 0.25
VSG2 = 0.64 V
```
Since the source of M2 is tied to the supply
VS2 = VDD = 1.5 V

The gate voltage becomes   
```
VG2 = VS2 − VSG2
= 1.5 − 0.64	
VG2 = 0.86 V     
```
```
VSD2 = VS2 − Vout
= 1.5 − 1.25	
VSD2 = 0.25 V
```
Width Calculation :

For M1 :
```
From current equation: ID = (1/2) un cox (W/L) Vov^2
W1 = 19.35 µm 
W2 = 60.75 µm      
W3 = 41.65 µm
```
conclusion : As all three transistors M1, M2, and M3 are in saturation condition.
Therefore, the circuit operates correctly with all devices biased in the saturation region, which is necessary for proper amplifier operation.


# RESULT

The MOSFET amplifier circuits were designed and simulated using the required parameters. First, the DC analysis was performed to set the proper biasing conditions so that all the transistors operate in the saturation region. After confirming the correct operating point, AC analysis was carried out to study the small-signal behavior of the amplifier.

From the simulation results, the voltage gain, bandwidth, output resistance, and other important parameters were obtained. The waveform of the output signal was observed and compared with the input signal. The amplifier successfully amplified the input signal while maintaining the expected phase relationship depending on the configuration used.

The results obtained from the simulation were consistent with theoretical expectations. The gain and frequency response of the amplifier were clearly observed from the plots generated during AC analysis. Thus, the designed MOSFET amplifier circuit performed as intended.

# CONCLUSION

In this experiment, the MOSFET amplifier configuration was successfully designed and analyzed using simulation tools. The DC analysis helped in determining the correct biasing conditions so that the MOSFET operates in the saturation region, which is necessary for proper amplification.

After performing AC analysis, important parameters such as voltage gain and bandwidth were evaluated. The simulation results demonstrated that the amplifier is capable of amplifying small input signals effectively. The comparison between theoretical expectations and simulation results showed good agreement.

Overall, this experiment helped in understanding the working principle of MOSFET amplifiers, the importance of proper biasing, and how different parameters affect the amplifier performance. It also provided practical experience in analyzing amplifier circuits using simulation tools.




 



  



    







