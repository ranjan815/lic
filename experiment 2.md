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

DESIGN CALCULATIONS

Given: Supply voltage, VDD = 1.5 V Chosen drain current, ID = 200 uA and threshold voltage = 0.36v
consider Vov =0.25v so that both the MOSFET's operates in saturation region 

for NMOS(M1):

      Vov = Vgs - Vt
      0.25 = Vgs - 0.36
      Vgs = 6.1v

      Vgs = Vg - Vs
      Vg = Vgs + Vs 
         Vg = 0.81v

we know that ID = (1/2) un cox (W/L) Vov^2
            W = (2 x 180n x 200 x 10^-6)/ (273.89 x 10^-4 x 8.616 x 10^-3 x 0.25^2)
            W =   

for PMOS(M2): 
 Vov = Vsg - Vt
 Vsg = 0.25 + 0.39
Vsg = 0.64v

Vg = Vs + Vsg
Vg = 0.86v

 ID = (1/2) up cox (W/L) Vov^2
W = (2 x 180n x 200 x 10^-6)/ (115.6 x 10^-3 x 10^-4 x 8.616 x 10^-3 x 0.25^2)
w = 


# DC ANALYSIS:


schematic :


based on the initial design equations, the calculated values of  Width of both the mosfet were w1=  um and w2=  um Rs =   kΩ.
However, to meet the necessary operating conditions, the transistor width was adjusted.
The goal was to achieve a drain voltage of   V and a drain current of 200 uA. By changing the
width parameter, we successfully established the desired Q-point. The final optimized width needed 
to maintain ID = 200 uA at output voltage of   V was found to be W1 =  um and w2=  um

# TEANSIENT ANALYSIS


Procedure

1) apply input voltage as SINE(__ 10m 1000) to gate terminal
2) Place transient command .tran and set stop time as 5m.
3) And run simulation and note  Vin and Vout peak to peak voltages
4) calculate the gain(Vout/vin) from the obtained voltages






