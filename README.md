# Experiment – 1  
## DC, Transient and AC Analysis of Common Source Amplifier using 180nm NMOS in LTspice

---

## AIM :

To design a Common Source (CS) amplifier using 180nm NMOS technology in LTspice and to perform DC, Transient and AC analysis as per the given specifications.

---

## GIVEN SPECIFICATIONS :

- VDD = 1.5 V  
- Power constraint P ≤ 0.5 mW  
- Load capacitor CL = 1 pF  
- Channel length L = 180 nm  
- Technology : 180 nm TSMC library  

---

## COMPONENTS USED :

- NMOS transistor (180nm model)  
- Drain resistor (RD)  
- DC power supply  
- AC signal source  
- Load capacitor (1 pF)  
- Ground and connecting wires  
---

## CIRCUIT DIAGRAM :

The Common Source amplifier circuit was designed in LTspice using 180nm NMOS technology.  
The drain resistor RD is connected between VDD and drain terminal.  
The input signal is applied at the gate terminal and output is taken from the drain.  
A load capacitor of 1 pF is connected at the output node.


![CS Amplifier Circuit](circuit.png)

---

## THEORY :

A Common Source (CS) amplifier is one of the fundamental MOSFET amplifier configurations.  
In this configuration, the source terminal is grounded, the input is applied at the gate and the output is taken from the drain.
The amplifier provides voltage gain with a phase inversion of 180 degrees between input and output.  
For proper amplification, the MOSFET must operate in the saturation region.  
Therefore, the Q-point is fixed such that VDS ≈ VDD/2 to allow maximum symmetrical output swing.


## PROCEDURE :

1. The 180nm NMOS model file (tsmc018.lib) was included in LTspice using the .include directive.

2. The Common Source amplifier circuit was constructed with:
   - VDD = 1.5 V  
   - Drain resistor RD ≈ 2.245 kΩ  
   - NMOS transistor with L = 180 nm and W = 2.5 µm  
   - Load capacitor CL = 1 pF  

3. DC analysis was performed using the .op and .dc commands to determine the Q-point by setting VDS ≈ VDD/2.

4. RD was adjusted and W/L ratio was varied to achieve the required drain current under the power constraint (P ≤ 0.5 mW).

5. Transient analysis (.tran 5m) was carried out using a sine input SINE(0.9 10m 1k) to observe linear and non-linear behavior.

6. AC analysis (.ac dec 10 0.1 100G) was performed to obtain frequency response and determine gain and bandwidth parameters.
   
## DC ANALYSIS AND CALCULATIONS

To fix the Q-point at VDS ≈ VDD/2, the drain current was first calculated using the power constraint.

Given:

P ≤ 0.5 mW  
VDD = 1.5 V  

Using,

P = V × I  

0.5 mW = 1.5 × ID  

Therefore,

ID = 3.34 × 10⁻⁴ A  
ID ≈ 0.334 mA  

For maximum symmetrical swing,

VDS = VDD / 2  
VDS = 1.5 / 2 = 0.75 V  

The drain resistor was calculated using:

RD = (VDD − VDS) / ID  

RD = (1.5 − 0.75) / (3.34 × 10⁻⁴)  

RD ≈ 2.245 kΩ  

The transistor width was initially calculated using the MOSFET saturation current equation:

ID = (kn'/2) × (W/L) × (VGS − Vth)²  

From calculations,

W ≈ 1.83 µm  

After simulation tuning to achieve correct Q-point,

Final selected W = 2.5 µm  

The obtained DC operating point from LTspice:

ID ≈ 0.33 mA  
VDS ≈ 0.75 V  

Thus, the Q-point was successfully fixed near mid-supply.
### DC Simulation Result

![DC Operating Point](dc.png)


