# CS Amplifier using NMOS — LTspice (180nm Technology)

## Aim
To design and analyze a Common Source (CS) amplifier using an NMOS transistor in 180nm technology using LTspice and to study its DC bias point, transient response, and AC frequency behavior.

---

## Given Specifications

- Technology: 180 nm NMOS
- VDD = 1.5 V
- Power limit ≤ 0.5 mW
- Load capacitor CL = 1 pF
- Channel length L = 180 nm

---

## Theory

A Common Source amplifier is a basic MOSFET amplifier where the source terminal is grounded, the input is applied at the gate, and the output is taken from the drain. It provides good voltage gain and produces a 180° phase shift between input and output. Proper biasing is required to fix the Q-point so that the amplifier works in the saturation region for linear amplification.

---

## Circuit Description

The circuit was built in LTspice using the 180nm NMOS model.  
A drain resistor RD is connected to VDD and the output is taken at the drain node.  
The gate is biased using a DC source along with a small AC signal for testing.  
The Q-point was adjusted such that VDS is approximately equal to VDD/2 for maximum output swing.

---

## Design Calculations

Maximum allowed current from power constraint:

ID ≤ P / VDD

RD was selected using:

RD = (VDD − VDS) / ID

The W/L ratio of NMOS was tuned to obtain the required drain current and correct operating point.

(Write your final selected values here.)

---

## DC Analysis

DC sweep analysis was performed to find the operating point.

Observations:
- Obtained Q-point near mid supply
- Drain current = ___
- VDS = ___
- RD selected = ___

### DC Simulation Plot
(Add DC screenshot here)

---

## Transient Analysis

Transient simulation was done using a sine wave input to check linear and non-linear behavior.

Observations:
- Output waveform is inverted
- Small input signal gives linear amplified output
- Large input signal shows distortion
- Measured gain ≈ ___

### Transient Waveform
(Add transient screenshot here)

---

## AC Analysis

AC sweep was performed to measure frequency response.

Measured parameters:
- Midband gain = ___ dB
- 3 dB bandwidth = ___
- Unity gain bandwidth = ___
- Gain Bandwidth Product = ___

### AC Response Plot
(Add AC screenshot here)

---

## Observations

- Bias point selection strongly affects linearity
- Increasing RD increases gain but reduces bandwidth
- Larger W/L increases drain current
- Load capacitor reduces high frequency response

---

## Conclusion

The Common Source amplifier was successfully designed and simulated in LTspice using 180nm NMOS technology. DC, transient, and AC analyses were performed. The amplifier showed expected inverted output and good voltage gain. Proper Q-point selection ensured linear amplification within the given power constraint.
