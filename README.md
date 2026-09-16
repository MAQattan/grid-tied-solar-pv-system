# Design and Performance Analysis of a Grid-Tied Solar PV System

[![CAD: AutoCAD](https://img.shields.io/badge/CAD-AutoCAD_2024-blue.svg)](https://www.autodesk.com)
![Software](https://img.shields.io/badge/PVsyst-v7.2.21-yellow.svg)
[![Code](https://img.shields.io/badge/Code-Typst-red.svg)](https://www.mathworks.com/products/matlab.html)
![Standard](https://img.shields.io/badge/Standard-IEC_60364-lightgrey)
![Institution](https://img.shields.io/badge/Institution-University_of_Aleppo-003366?style=flat-square)
![Graduation Thesis](https://img.shields.io/badge/Project-B.Sc._Graduation_Thesis-darkgreen?style=flat-square)

A highly optimized engineering design and dynamic performance analysis of a **23.40 kWp grid-tied rooftop solar photovoltaic system**. Designed for a critical banking facility in Aleppo, Syria, this project resolves the structural and electrical matching challenges of urban solar integration under complex spatial constraints.

## 1. Overview / Abstract

This repository contains the full engineering documentation, AutoCAD layouts, Single Line Diagrams (SLD), and PVsyst simulation models for a **23.40 kWp grid-connected rooftop solar PV system** designed to meet the critical loads of a commercial banking facility in Aleppo, Syria. By integrating state-of-the-art **N-Type Hybrid Passivated Back Contact (HPBC)** modules with a **Huawei SUN2000-25KTL-M5 Smart Inverter**, the system maximizes spatial power density on a highly constrained urban roof. Detailed dynamic simulations executed in **PVsyst v7.2.21** demonstrate an exceptional annual yield of **44.02 MWh** and an industry-benchmark **Performance Ratio (PR) of 89.30%**.

## 2. Problem Statement

Commercial and financial facilities in dense urban environments require highly reliable power supplies but are severely limited by **spatial constraints** and complex **architectural obstructions** on rooftops. The primary engineering challenges addressed in this design include:

- **The Rooftop Spatial Bottleneck:** Traditional inter-row spacing layouts designed to avoid mutual shading typically waste **40% to 50% of the usable rooftop area**, capping the maximum allowable installed capacity.
- **Localized Architectural Obstructions:** Permanent structures on the bank's roof—such as a **2.5-meter-high stairwell** and a **1.3-meter-high centralized AC unit**—impose complex, dynamic shadows during peak sun hours. Unmitigated shading triggers severe **mismatch losses** and high risks of localized **hotspot formation**, which degrade module life and threaten system safety.
- **Static Design Limitations:** Standard static hand calculations are insufficient for modeling time-varying, three-dimensional shading profiles and predicting real-world system behavior under extreme seasonal temperature fluctuations.

## 3. Methodology & Software Used

The project adopts a rigorous **five-stage Integrated Engineering Design Cycle**:

```mermaid
flowchart LR
    A["<b>1. Geo-Climatic Study</b><br/><i>(Global Solar Atlas)</i>"] --> B["<b>2. Spatial Design & Shading</b><br/><i>(AutoCAD 3D)</i>"]
    B --> C["<b>3. Thermal Sizing &<br/>Electrical Matching</b>"]
    C --> D["<b>Main DC/AC Cable<br/>Voltage Drop Analysis</b>"]
    D --> E["<b>4. Selectivity-Based<br/>Protections & SLD</b>"]
    E --> F["<b>5. PVsyst Digital Twin<br/>& Dynamic Simulation</b>"]
```

### Software Toolchain & Standards Conformed:

- **Meteonorm 8.0 & Global Solar Atlas:** Used to extract high-resolution, long-term meteorological time series (2006–2013) and geographical solar parameters for Aleppo.
- **AutoCAD:** Utilized for high-precision 2D architectural mapping, structural layouts, and 3D geometric shadow path modeling.
- **PVsyst v7.2.21:** Employed to construct a high-fidelity **Digital Twin** of the system, run dynamic simulations, optimize the DC/AC ratio, and evaluate the final annual system loss tree.
- **IEC 60364-7-712 & EN 50618:** Applied to govern the safety, selection, sizing, and protection of the DC/AC electrical distribution system.
- **IEEE 80:** Followed to design and verify the safety of the low-impedance earthing grid under fault currents.

## 4. System Architecture & Design Details

### 4.1. Geo-Climatic Parameters (Aleppo, Syria)

- **Coordinates:** Latitude: ${} 36.20^\circ\text{ N}$, Longitude:  $37.14^\circ\text{ E}$, Altitude: $379\text{ m}$.
- **Solar Resource Data:** Global Horizontal Irradiation (GHI) = $1930.4\text{ kWh/m}^2/\text{year}$. Global Incident Irradiation on Optimized Tilt ($31^\circ$) (GTI) = $2184.8\text{ kWh/m}^2/\text{year}$.
- **Optimum Tilt & Azimuth:** $31^\circ$ Fixed Plane tilted due South ($0^\circ$ Azimuth).
- **Annual Peak Sun Hours (PSH):** $5.98\text{ hours/day}$.

### 4.2. Spatial Engineering: Terraced Mounting & Shading Geometry

To overcome the urban rooftop spatial bottleneck, a **Terraced (Staircase) Mounting Structure** was engineered. This design aligns the trailing edge of each row with the leading edge of the subsequent row, reducing the inter-row pitch distance to zero ($D = 0$). By raising the subsequent rows step-by-step, the structural design completely neutralizes inter-row mutual shading while achieving an outstanding **areal power density of 119.59 W/m²** over a net exploited rooftop area of **195.67 m²**.

To verify that localized shadows from the AC unit (Height $H = 1.3\text{ m}$) and the Stairwell (Height $H_{stair} = 2.5\text{ m}$) do not impact the active cells of adjacent strings, a rigorous **3D trigonometric verification** was executed for the worst-case scenario (Winter Solstice, Dec 21, 9:00 AM):
$$\text{Minimum Spacing Equation: } D_{min} = D \times \cos(\psi_{Correction})$$
$$\text{Lateral Shading Spacing: } D_{Lat} = D \times \sin(\psi_{Correction})$$

At the critical intersection point on December 21, the maximum vertical shadow height ($H_{shadow}$) from the stairwell was calculated at $0.763\text{ m}$. Because the physical support frame raises the adjacent active module area to a minimum height of $1.173\text{ m}$:

$$H_{shadow}\ (0.763\text{ m}) < H_{collector\_min}\ (1.173\text{ m})$$

This confirms the shadow passes entirely below the active cells, eliminating hotspot risks and seasonal mismatch losses.

![AutoCAD drawing showing shadow projections for the stairwell and the central air conditioning unit.](images/PV-10-11.png)

### 4.3. Photovoltaic Module Specifications

The design utilizes **39 units** of high-efficiency **LONGi Hi-MO 6 Scientist LR5-72HTH-600M** modules featuring N-Type Hybrid Passivated Back Contact (HPBC) technology:

| Electrical Parameter                 | Symbol       | STC Value ($1000\text{ W/m}^2, 25^\circ\text{C}$)  |
| :----------------------------------- | :----------- | :------------------------------------------------- |
| Nominal Power                        | $P_{max}$    | $600\text{ Wp}$                                    |
| Open-Circuit Voltage                 | $V_{oc}$     | $52.81\text{ V}$                                   |
| Optimum Operating Voltage            | $V_{mp}$     | $44.66\text{ V}$                                   |
| Optimum Operating Current            | $I_{mp}$     | $13.44\text{ A}$                                   |
| Short-Circuit Current                | $I_{sc}$     | $14.46\text{ A}$                                   |
| Module Efficiency                    | $\eta$       | ${} 23.20\%$                                       |
| Temperature Coefficient of $P_{max}$ | $\gamma_{P}$ | $-0.290\%/^\circ\text{C}$                          |

### 4.4. Inverter Selection & DC/AC loading

The system is managed by a three-phase **Huawei SUN2000-25KTL-M5 Smart Inverter**:

- **Rated AC Power:** $25.00\text{ kW}$.
- **DC/AC Loading Ratio (R):** $23.40\text{ kWp} \div 25.00\text{ kW} = 0.936$. This ratio ensures the inverter operates in its peak efficiency window (${} 40\%$ to ${} 80\%$ load) for maximum daily hours.
- **MPPT Inputs:** 2 independent MPPT trackers with a wide operating voltage range ($200\text{ V} - 1000\text{ V}$).
- **Integrated Safety Features:** AI-powered Arc Fault Circuit Interrupter (AFCI) for instant arc detection, Type II DC and AC surge arresters.

### 4.5. Dynamic String Sizing & MPPT Mapping

Dynamic temperature-corrected calculations were performed to establish safe open-circuit voltages at $0^\circ\text{C}$ (extreme winter) and optimum operating voltages at $60^\circ\text{C}$ (extreme summer):

- $V_{oc}$ at $0^\circ\text{C}$ = $56.64\text{ V}$ per module.
- $V_{mp}$ at $60^\circ\text{C}$ = $40.12\text{ V}$ per module.

$$N_{ideal} = \frac{V_{rated\_inverter}}{V_{mp\_STC}} = \frac{600\text{ V}}{44.66\text{ V}} \approx 13\text{ Modules in Series}$$

The string layout consists of **3 Strings of 13 Modules** each. To isolate local shading losses, a **Multi-MPPT mapping strategy** is implemented:

- **MPPT 1:** 2 strings in parallel (26 modules total) placed in unshaded, safe zones (center and west of the roof).
    - _Max operating current:_ $2 \times 13.44\text{ A} = 26.88\text{ A} \le 30.00\text{ A}$ (Inverter limit).
- **MPPT 2:** 1 string (13 modules) placed in the eastern zone, which experiences temporary lateral shadows from the stairwell. This prevents shading losses on the eastern string from dragging down the performance of the unshaded strings.

![Configuring components and string layout in PVsyst](images/PV-11-03.png)

### 4.6. Cable Sizing, Protections & Grounding Grid

- **DC Cabling:** Specialty solar copper cables conforming to **EN 50618** (4 mm² cross-section). At $45^\circ\text{C}$ ambient, the derated ampacity ($I_{allowable} = 33.37\text{ A}$) easily exceeds the design current ($I_{dc\_max} = 18.075\text{ A}$). The total DC voltage drop is optimized at **${} 0.763\%$**, well below the academic ${} 1\%$ limit.
- **AC Cabling:** Low-voltage $4 \times 16\text{ mm}^2\text{ Cu/XLPE/PVC}$ cable (El Sewedy Cables). The derated ampacity of $85.26\text{ A}$ safely coordinates with the protective MCB. The AC voltage drop over a 30m run is kept at **${} 0.717\%$**.
- **Protections (Selectivity-Based Coordination):**
    - _String Fuses:_ $25\text{ A}$, $1000\text{ Vdc}$, gPV class (IEC 60269-6) protecting modules from reverse fault currents.
    - _DC Isolator:_ $32\text{ A}$, $1000\text{ Vdc}$, 2-pole load-break switch.
    - _Inverter Output MCB:_ $50\text{ A}$ nominal, 4-pole, Curve C, $10\text{ kA}$ breaking capacity.
    - _Main Bank Circuit Breaker:_ $63\text{ A}$, 4-pole MCCB, $\ge 25\text{ kA}$ breaking capacity.
- **Earthing Grid (IEEE 80 & Dwight’s Formula):** Designed for a target resistance of $R_e \le 3.98\ \Omega$ ($< 5\ \Omega$ standard code). The grid consists of **10 vertical flemish-copper-clad steel rods** (Length $L = 2.5\text{ m}$, Diameter $d = 16\text{ mm}$) spaced 5m apart, buried at 0.8m, and interconnected with a $50\text{ mm}^2$ bare copper conductor.

![Single line diagram](images/SLD.png)
> **[📄 Click here to download or view the complete single-line diagram in high-resolution PDF format.](images/SLD.pdf)**

### 4.7. Bill of Materials (BOM)

The following table summarizes the primary structural and electrical equipment selected for this grid-tied installation:

|Item|Component|Technical Specification|Proposed Manufacturer|Qty|Unit|
|:-:|:--|:--|:-:|:-:|:-:|
|**1**|PV Modules|N-Type HPBC, 600 Wp, 23.2% Efficiency, LR5-72HTH-600M|LONGi Solar|39|Pcs|
|**2**|Grid-Tied Inverter|25 kW AC rated, 2 MPPTs, SUN2000-25KTL-M5|Huawei|1|Unit|
|**3**|DC String Fuses|25 A, 1000 Vdc, gPV class, 10x38 mm|Schneider / ABB|6|Pcs|
|**4**|DC MCB/Isolators|2-Pole, 32 A, 1000 Vdc|Schneider / ABB|3|Pcs|
|**5**|DC Combiner Box|IP66 Enclosure with DIN rail, UV-Stabilized Polycarbonate|Hensel|1|Unit|
|**6**|Solar DC Cable|4 mm² cross-section, tinned copper, double-insulated XLPO|KBE / Prysmian|300|Meters|
|**7**|AC Circuit Breaker|4-Pole, 50 A, Curve C, 10 kA|Schneider / ABB|1|Pcs|
|**8**|Main AC Cable|4 x 16 mm² Cu/XLPE/PVC, 0.6/1 kV|El Sewedy Cables|50|Meters|
|**9**|Smart Power Sensor|3-Phase, DTSU666-H 250A/50mA, Modbus-RTU|Huawei|1|Unit|
|**10**|Mounting Structure|Terraced / Stepped design, Anodized Al Rail, HDG Steel frame|Custom Structural|1|Lot|
|**11**|Earthing System|10 solid copper rods, 50 mm² bare copper cable, inspection pit|Custom Electrical|1|Lot|

## 5. Results & Analysis

The simulated performance metrics of the grid-tied system:

### 📊 PVsyst Simulation Yield Indicators (Aleppo Site)

| Metric                         |      Symbol       |   Value    |     Unit     |
| :----------------------------- | :---------------: | :--------: | :----------: |
| **Annual Energy Injected**     | $E_{\text{Grid}}$ | **44.02**  |   MWh/year   |
| **Specific System Production** |         —         |  **1881**  | kWh/kWp/year |
| **System Performance Ratio**   |       $PR$        | **89.30%** |      —       |
| **Avg. Daily Useful Energy**   |       $Y_f$       |  **5.15**  | kWh/kWp/day  |

### 5.1. Energy Yield and PR Dynamics

- **Annual Energy Yield ($E_{Grid}$):** The system feeds **$44.02\text{ MWh/year}$** of clean power into the bank's local distribution network and the public utility grid.
- **Performance Ratio (PR):** Achieves an annual **${} 89.30\%$ PR**. Under cold, clear sky winter conditions (January), the system hits peak performance with a **${} 94.80\%$ PR** due to reduced module thermal degradation. Conversely, high summer temperatures (July) degrade $V_{mp}$, driving the PR down to **${} 85.80\%$**.

![System Output Power Distribution](images/PV-11-09.png)

### 5.2. Daily Normalized Performance

- **Daily Useful Energy ($Y_f$):** Evaluated at **$5.15\text{ kWh/kWp/day}$**, meaning each installed kWp yields over 5 hours of full-load equivalent production daily.
- **Collection Losses ($L_c$):** **$0.52\text{ kWh/kWp/day}$** is lost due to thermal module degradation, minor dust buildup, and wiring resistance.
- **System Losses ($L_s$):** Just **$0.09\text{ kWh/kWp/day}$** is lost during inverter DC-to-AC conversion.

![Normalized productions](images/PV-11-07.png)

### 5.3. PVsyst Loss Diagram Breakdown

The complete transformation chain from raw irradiance to useful grid energy, as simulated by the PVsyst loss model:

1. **Global Horizontal Irradiation (GHI):** $1862\text{ kWh/m}^2$.
2. **Tilt Transposition Gain (to $31^\circ$):** **${} +13.10\%$**.
3. **Effective Global Incident Radiation (GTI):** $2071\text{ kWh/m}^2$.
4. **Nominal PV Array Energy (at STC):** $48.63\text{ MWh}$.
5. **PV Loss due to Temperature:** **${} -4.64\%$** (highly stabilized by LONGi's low thermal coefficient).
6. **Mismatch Loss (modules and strings):** **${} -2.10\%$** (mitigated successfully by the parallel Multi-MPPT mapping layout).
7. **Ohmic Wiring Loss (DC cabling):** **${} -0.73\%$** (validating the selection of the $4\text{ mm}^2$ solar cable cross-section).
8. **Inverter Conversion Efficiency Loss:** **${} -1.72\%$** (driven by the high ${} 98.40\%$ peak efficiency of the Huawei unit).
9. **Final Energy Injected to Grid:** **$44.02\text{ MWh}$**.

![Loss Diagram](images/PV-11-08.png)

## 6. Conclusion & Future Work

### 6.1. Design Accomplishments

- **Spatial Optimization:** The custom **Terraced Mounting** structure bypassed the typical urban spacing penalty, reclaiming **${} 40\%$ to ${} 50\%$ of lost rooftop space** to establish an excellent spatial power density of **$119.59\text{ W/m}^2$**.
- **Electrical Selectivity & Isolation:** Isolating the shade-affected eastern string on a dedicated MPPT channel successfully confined mismatch losses to just **${} 2.10\%$**, ensuring the system maintains a benchmark **${} 89.30\%$ PR**.
- **Thermal & Compliance Success:** The tinned copper solar and AC cabling layouts kept voltage drop parameters below **${} 0.85\%$**, ensuring complete compliance with standard code guidelines.

### 6.2. Future Work Recommendations

- **Hybrid Configuration (Battery Storage Integration):** To prevent grid-tie dropouts under regional utility blackout events, integrating a hybrid battery backup loop would secure continuous supply for critical banking operations.
- **Bifacial Module Upgrades:** If roof reflectivity is improved by applying a white reflective coating to elevate the current $0.20$ albedo, upgrading to bifacial modules would enable up to ${} 5\% - 10\%$ additional back-side generation gains.

## 7. Project Metadata

- **Student/Author:** Muhammad Ali Qattan (محمد علي قطان)
- **Academic Institution:** University of Aleppo, Faculty of Electrical and Electronic Engineering, Department of Electrical Power Engineering (2026 CE / 1448 AH)
- **Project Supervisor:** Dr. Karima Sukkar (د. كريمة سكر)
