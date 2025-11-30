# 📡 2.4 GHz Microstrip Patch Antenna Design with Inset Feed

This project demonstrates the design, calculation, and simulation of a rectangular Microstrip Patch Antenna operating at **2.4 GHz** (ISM Band) using **CST Studio Suite**.

The design utilizes the **Inset Feed** technique to achieve perfect impedance matching ($50\Omega$) without external matching networks.

## 🎯 Project Goals
* **Target Frequency:** 2.40 GHz (Wi-Fi / Bluetooth / IoT)
* **Return Loss ($S_{11}$):** < -10 dB
* **Gain:** > 6 dBi
* **Impedance:** $50\Omega$

## 📐 Design Parameters & Mathematics

The dimensions of the antenna were theoretically calculated using the **Transmission Line Model** and implemented via Python scripts.

### 1. Substrate Properties
We used **FR-4 (Lossy)** as the dielectric material.
* Dielectric Constant ($\epsilon_r$): **4.3**
* Height ($h$): **1.6 mm**

### 2. Width Calculation ($W$)
To achieve high efficiency, the width is calculated as:
$$W = \frac{c}{2f_r} \sqrt{\frac{2}{\epsilon_r + 1}} \approx 38.39 \text{ mm}$$

### 3. Effective Dielectric Constant ($\epsilon_{eff}$)
Since the waves travel partially in air and partially in the substrate, we calculate the effective permittivity:
$$\epsilon_{eff} = \frac{\epsilon_r + 1}{2} + \frac{\epsilon_r - 1}{2} \left[1 + 12\frac{h}{W}\right]^{-1/2}$$

### 4. Length Calculation ($L$)
The physical length is slightly shorter than $\lambda/2$ due to the **fringing fields** ($\Delta L$):
$$L = L_{eff} - 2\Delta L \approx 29.78 \text{ mm (Theoretical)}$$
*(Optimized to **29.1 mm** in CST for exact 2.40 GHz resonance)*

### 5. Inset Feed Depth ($F_i$) - The "Sweet Spot"
To match the high edge impedance (~300$\Omega$) to the 50$\Omega$ feed line, we cut a notch into the patch. The depth $y_0$ is found using the cosine-squared rule:
$$R_{in}(y_0) = R_{edge} \cos^2\left(\frac{\pi}{L} y_0\right)$$
Solving for $50\Omega$:
$$y_0 = \frac{L}{\pi} \arccos\left(\sqrt{\frac{50}{R_{edge}}}\right) \approx 10.93 \text{ mm (Theoretical)}$$
*(Optimized to **8.5 mm** in CST for -14.5 dB Return Loss)*

---

## 🛠️ Simulation Results (CST Studio Suite)

### 1. Return Loss ($S_{11}$)
The antenna shows a deep resonance at **2.403 GHz** with a return loss of **-14.5 dB**. This indicates that 96% of the power is transmitted, with only 4% reflection.

![S11 Graph](S11_Parameter.png)
*(Fig 1: S-Parameter Magnitude in dB)*

### 2. 3D Radiation Pattern (Farfield)
The antenna exhibits a directional radiation pattern with a main lobe magnitude of **6.33 dBi**, directed towards the Z-axis (broadside).

![Radiation Pattern](3D_Radiation_Pattern.png)
*(Fig 2: 3D Farfield Radiation Pattern showing directivity)*

### 3. Antenna Structure
The final geometry includes the optimized Inset Feed gap to ensure $50\Omega$ matching.

![Structure](Antenna_Structure.png)

---

## 📂 How to Run
1. Open `Microstrip_Patch_2_4GHz.cst` in CST Studio Suite.
2. Check the **Parameter List** for optimized values ($L=29.1$, $Fi=8.5$).
3. Run the **Time Domain Solver**.

---
*Author: Utku Turan*
*Tools: CST Studio Suite 2024, Python*
