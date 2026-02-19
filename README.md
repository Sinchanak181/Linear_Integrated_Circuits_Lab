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
## DC PARAMETER VARIATION STUDY

### (a) Effect of Varying RD (For Fixed W/L)

The width and length of the transistor were kept constant (W = 2.5 µm, L = 180 nm).  
The drain resistor RD was varied to observe its effect on the Q-point.

Observation:

- Increasing RD increases the voltage drop across RD.
- As RD increases, VDS decreases.
- Drain current slightly reduces for larger RD values.
- Proper RD selection is required to maintain VDS ≈ VDD/2.

Thus, RD ≈ 2.245 kΩ was selected to obtain VDS ≈ 0.75 V.
### DC Sweep Result

The DC sweep of input voltage was performed from 0 V to 1.5 V to observe variation in supply current and verify the power constraint.

![DC Sweep Current](dc_sweep.png)


---

### (b) Effect of Varying W (For Fixed RD)

The drain resistor was kept constant at RD ≈ 2.245 kΩ.  
The transistor width (W) was varied to analyze its effect on drain current.

Observation:

- Increasing W increases drain current.
- Larger W shifts the Q-point due to higher ID.
- Smaller W reduces ID and moves VDS closer to VDD.

From simulation tuning, W = 2.5 µm provided the required drain current (≈ 0.33 mA) and correct biasing.
### DC Transfer Characteristic (Vout vs Vin)

The DC sweep was performed by varying input voltage from 0 V to 1.5 V.  
The variation of output voltage with respect to input voltage is shown below.

![DC Transfer Curve](dc_transfer.png)
## TRANSIENT ANALYSIS

Transient analysis was performed using a sinusoidal input signal:

SINE(0.9 10m 1k)

The input amplitude was kept small to observe linear amplification.

### Observation

- The output waveform is inverted with respect to the input.
- A phase shift of approximately 180° was observed.
- The amplifier operates in the linear region for small input signals.
- For larger input amplitudes, distortion begins to appear.

Transient analysis was performed using:

.tran 5m

A sinusoidal input was applied:
SINE(0.9 10m 1k)

### Input Waveform

![Vin Waveform](vin_transient.png)

### Output Waveform

![Vout Waveform](vout_transient.png)

### Observation
...


### Gain Calculation

From transient waveform:

Gain (Av) = Vout / Vin  

Measured practical gain ≈ 2.087  

Gain in dB:

Av(dB) = 20 log(2.087)  

Av ≈ 6.39 dB  

The theoretical gain using:

Av = gm × RD  

was approximately 2.808  

Theoretical gain in dB ≈ 8.94 dB  

Thus, practical gain is slightly lower than theoretical gain due to non-ideal effects.
### Transient Waveform

![Transient Output](transient.png)



