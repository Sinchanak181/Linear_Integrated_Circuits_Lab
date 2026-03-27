# 🔷 Experiment 4  
## CMOS Differential Amplifier – Design and Analysis (180 nm)

---

## 🎯 Aim

To design a CMOS differential amplifier and analyze its operation using DC conditions based on given specifications.

---

## 📘 Introduction

A differential amplifier is an important analog circuit that amplifies the voltage difference between two input signals while rejecting common noise present at both inputs.

Such amplifiers are widely used in analog systems like operational amplifiers and signal processing circuits due to their high noise immunity and stability.

---

## 📖 Theory

A differential amplifier consists of two matched MOSFETs connected with a common source node and a tail current element.

When a differential input is applied:

vd = Vin1 − Vin2  

- If Vin1 increases → current through M1 increases  
- If Vin2 increases → current through M2 increases  

For small input signals, both transistors operate in saturation and the circuit behaves linearly.

The small-signal gain is given by:

Av = gm × Rout  

where:

- gm = transconductance  
- Rout = effective output resistance  

and,

gm = (2ID) / Vov  

---
## 🔷 Circuit Diagram

![Circuit Diagram](circuit1.png)

---
## 📌 Design Calculations

### 🔸 Given Parameters

| Parameter | Value |
|----------|------|
| Technology | TSMC 180 nm |
| VDD | +0.9 V |
| VSS | -0.9 V |
| Power (P) | 1.8 mW |
| Channel Length (L) | 480 nm |
| Vth | 0.36 V |
| Load Capacitance | 10 pF |

---

### 🔸 Total Supply Voltage

Vtotal = VDD − VSS  

Vtotal = 0.9 − (−0.9) = 1.8 V  

---

### 🔸 Tail Current (ISS)

Using power relation:

P = Vtotal × ISS  

ISS = 1.8 mW / 1.8 V  

ISS = 1 mA  

---

### 🔸 Drain Current

For balanced differential pair:

ID1 = ID2 = ISS / 2  

ID = 0.5 mA  

---

### 🔸 Load Resistance (RD)

Using:

Vout = VDD − ID × RD  

Assuming symmetric output:

Vout ≈ 0 V  

0 = 0.9 − (0.5 mA × RD)

RD = 0.9 / (0.5 × 10⁻³)

RD ≈ 1.8 kΩ  

---

### 🔸 Bias Point Calculation

#### Source Voltage

Given:

Vp = −0.7 V  

Vs = Vp = −0.7 V  

---

#### Gate Voltage

For DC condition:

VG1 = VG2 = 0 V  

---

#### Gate-Source Voltage

VGS = VG − VS  

VGS = 0 − (−0.7)  

VGS = 0.7 V  

---

#### Overdrive Voltage

VOV = VGS − Vth  

VOV = 0.7 − 0.36  

VOV = 0.34 V  

---

#### Drain Voltage

Vout = 0 V  

---

#### Drain-Source Voltage

VDS = VD − VS  

VDS = 0 − (−0.7)  

VDS = 0.7 V  

---

### 🔸 Saturation Check

Condition:

VDS ≥ VOV  

0.7 ≥ 0.34  ✔  

👉 Both transistors operate in saturation region

---

### 🔸 Width Calculation

Using MOSFET equation:

ID = (1/2) μnCox (W/L) (VOV)²  

Rewriting:

W = (2 ID L) / (μnCox (VOV)²)

Initial value:

W ≈ 17.5 µm  

### 🔸 Width Tuning and Practical Adjustment

The width obtained from theoretical calculation is based on ideal square-law MOSFET assumptions.  
However, practical device behavior deviates due to several non-ideal effects.

To achieve the required bias condition:

Vs ≈ -0.7 V  

the transistor width was adjusted through simulation.

By varying W, the drain current was controlled such that the desired source voltage and operating point were accurately obtained.

| Condition | Width |
|----------|------|
| Initial calculated width | ≈ 17.5 µm |
| Final tuned width | ≈ 28.5 µm |

---

### 🔸 Reason for Deviation

The difference between theoretical and simulated width occurs due to:

- Channel length modulation (λ effect)
- Mobility degradation at higher fields
- Non-ideal MOSFET behavior in 180 nm technology
- Process variations in model parameters
- Influence of parasitic capacitances

Hence, width tuning is necessary to meet exact design specifications in simulation.
## 🔷 DC Analysis

![DC Analysis Screenshot](your_dc_image.png)

The DC operating point analysis is performed to verify whether all transistors are properly biased in saturation.

From the simulation results:

- Drain voltages are close to the expected operating value
- Source node voltage is maintained by the tail current source
- Equal current distribution is observed in both branches

✔ This confirms correct biasing and stable operation of the differential amplifier.

---

## 🔷 Input Common Mode Range (ICMR)

The input common-mode range defines the allowable range of input voltage for which the circuit operates correctly.

### 🔹 Minimum Input Voltage

For proper operation:

Vgs ≥ Vth  

Since:

Vgs = Vcm − Vs  

Therefore:

Vcm(min) = Vs + Vth  

Substituting values:

Vcm(min) = -0.7 + 0.36 = **-0.34 V**

---

### 🔹 Maximum Input Voltage

To keep NMOS in saturation:

Vds ≥ Vov  

Using:

Vds = Vd − Vs  

From bias point:

Vds ≈ 0.7 V  

Thus:

Vcm(max) = Vd + Vth = **0.36 V**

---

### ✅ Final ICMR

| Parameter | Value |
|----------|------|
| Vcm(min) | -0.34 V |
| Vcm(max) | 0.36 V |

---

## 🔷 Output Common Mode Range

The output voltage limits are determined by maintaining transistor saturation.

### 🔹 Maximum Output Voltage

Limited by supply voltage:

Vout(max) ≈ VDD = **0.9 V**

---

### 🔹 Minimum Output Voltage

Condition:

Vds ≥ Vov  

So:

Vout(min) = Vs + Vov  

Substituting:

Vout(min) = -0.7 + 0.34 = **-0.36 V**

---

### ✅ Final Output Range

| Parameter | Value |
|----------|------|
| Vout(min) | -0.36 V |
| Vout(max) | 0.9 V |

---

## 🔷 Differential Input Range (Linear Region)

For linear operation:

|Vid| ≤ 2Vov  

Given:

Vov = 0.34 V  

Therefore:

|Vid| ≤ 0.68 V  

---

### ✅ Linear Operating Range

| Parameter | Value |
|----------|------|
| Maximum differential input | ±0.68 V |

---

## 🔷 Transient Analysis

Transient analysis is performed to verify linearity of the amplifier under different input conditions.

---

### 🔹 Case 1: Small Signal Input (Linear Region)

![Transient Linear](your_linear_image.png)

Input applied:

Vid = 50 mV (< 0.68 V)

#### Observation:

- Output is clean sinusoidal
- No distortion observed
- Both transistors operate in saturation
- Gain remains constant

---

### 🔹 Case 2: Large Signal Input (Non-Linear Region)

![Transient Nonlinear](your_nonlinear_image.png)

Input applied:

Vid = 500 mV (> 0.68 V)

#### Observation:

- Output waveform shows distortion
- Clipping is observed
- One transistor moves towards cutoff
- Linear amplification is lost

---

## 🔷 Comparison of Operation

| Parameter | Linear Region | Non-Linear Region |
|----------|-------------|------------------|
| Input (Vid) | Small | Large |
| Output | Sinusoidal | Distorted |
| Gain | Constant | Reduced |
| Operation | Both active | One cuts off |

---

## 🔷 Interpretation

When the input difference is small, current splits equally and the amplifier behaves linearly.

As the input increases, current shifts toward one transistor, causing imbalance and distortion.

---

## 🔷 Conclusion

The differential amplifier operates linearly only within a limited input range.

✔ Linear condition:

|Vid| < 2Vov  

Beyond this limit:

- One transistor turns off  
- Output becomes non-linear  
- Gain reduces  

Thus, proper input range selection is essential for accurate amplification.
## 🔷 Gain Calculation (From Transient Analysis)

The output waveform is observed to be amplified and inverted with respect to the input.

### 🔹 Input Signal Details

| Parameter | Value |
|----------|------|
| Signal type | Sine wave |
| Frequency | 1 kHz |
| Differential amplitude | 50 mV |
| DC offset | 0 V |

---

### 🔹 Measured Peak-to-Peak Values

| Quantity | Value |
|----------|------|
| Vin(p-p) | 100 mV |
| Vout(p-p) | 604 mV |

---

### 🔹 Voltage Gain

\[
A_v = \frac{V_{out(p-p)}}{V_{in(p-p)}}
\]

\[
A_v = \frac{604 \times 10^{-3}}{100 \times 10^{-3}} = 6.04
\]

---

### 🔹 Gain in dB

\[
A_v(dB) = 20 \log_{10}(6.04)
\]

\[
A_v(dB) \approx 15.62 \, dB
\]

---

## 🔷 Theoretical Gain Estimation

To estimate gain analytically, small-signal parameters are considered.

### 🔹 Output Resistance

\[
r_o = \frac{1}{\lambda I_D}
\]

Given:

- λ = 0.1 V⁻¹  
- ID = 0.5 mA  

\[
r_o = \frac{1}{0.1 \times 0.5 \times 10^{-3}} = 20\,k\Omega
\]

---

### 🔹 Effective Output Resistance

\[
r_{out} = r_{o1} \parallel r_{o2}
\]

\[
r_{out} = 20k \parallel 20k = 10k\Omega
\]

---

### 🔹 Transconductance

\[
g_m = \frac{2I_D}{V_{ov}}
\]

(Use your Vov value here)

---

### 🔹 Theoretical Gain

\[
A_v = g_m \cdot r_{out}
\]

✔ This gives an approximate value since ideal conditions are assumed.

---

## 🔷 AC Analysis

![AC Response](your_ac_plot.png)

The AC analysis provides the frequency response of the amplifier.

---

### 🔹 Key Parameters from Bode Plot

| Parameter | Value |
|----------|------|
| Midband Gain | ≈ 9.87 dB |
| -3 dB Gain | ≈ 6.87 dB |
| Lower Cutoff (fL) | ~ 0 Hz |
| Upper Cutoff (fH) | 4.819 MHz |

---

### 🔹 Bandwidth

\[
BW = f_H - f_L
\]

\[
BW = 4.819 \, MHz
\]

---

## 🔷 Observation on Frequency Response

- Gain remains constant in midband region  
- Gain decreases at higher frequencies  
- Roll-off occurs due to parasitic capacitances  
- Bandwidth is mainly limited by output node capacitance  

---

## 🔷 Reason for Difference (Theoretical vs Practical)

The difference between calculated and simulated gain arises due to:

- Channel length modulation (finite output resistance)
- Mobility degradation in short-channel devices  
- Parasitic capacitances in MOSFET model  
- Non-ideal current distribution  
- Approximation in hand calculations  

✔ Simulation includes all second-order effects, hence more accurate.

---

## 🔷 Inference

The differential amplifier using resistive load has been successfully designed and analyzed.

### 🔹 Key Outcomes

- Power constraint is satisfied  
- Tail current ensures proper biasing  
- Both transistors operate in saturation  
- Gain is moderate due to resistive load  
- Bandwidth is relatively high  

---

### 🔹 Performance Summary

| Parameter | Value |
|----------|------|
| Gain (Simulated) | ~6.04 V/V |
| Gain (dB) | ~15.62 dB |
| Bandwidth | ~4.8 MHz |

---

### 🔹 Final Understanding

- For small differential input → circuit behaves linearly  
- For large input → distortion occurs  
- Gain is limited by output resistance  
- Bandwidth is affected by parasitic capacitances  

✔ Thus, the amplifier meets design requirements and demonstrates expected behavior.

