# Dataset README
**Title:** Thermogravimetric and Microscale Calorimeter Data on Cast PMMA

---

## 1. General Information

**Principal Creator**
- **Name:** Felix Armbrust
- **Affiliation:** Technische Universität Braunschweig, Institute of Building Materials, Concrete Construction and Fire Safety
- **Address:** Beethovenstraße 52, 38106 Braunschweig, Germany

**Co-Creators**
- Prof. Dr.-Ing. Jochen Zehfuß
- Dr.-Ing. Olaf Riese

**Date of Data Collection:** November 2024 -- April 2025
**Location of Data Collection:** Braunschweig, Germany
**Funding:** No funding was received for this work.

---

## 2. Abstract

This dataset contains thermogravimetric analysis (TGA) and micro-scale combustion calorimeter (MCC) data for cast polymethyl methacrylate (PMMA). The experiments were conducted to investigate influences on micro-scale experiments in the context of kinetic modelling of PMMA decomposition.

Two sample preparation methods were applied:
- **Pieces** (larger solid fragments)
- **Powder** (finely ground material)

For further information regarding the experiments, see https://doi.org/10.24355/dbbs.084-202507041233-0

---

## 3. Sharing & Access Information

- **License:** CC BY 4.0
- **Access Restrictions:** None

---

## 4. Methodological Information

### 4.1 Data Processing
The dataset represents **raw experimental data** with minor adjustments:
- In TGA data, the initial **settling phase** and final **holding phase** were removed, as these phases ensured boundary conditions but did not involve relevant processes.
- For non-isothermal TGA data, values recorded below **130°C** were removed to eliminate measurement artefacts caused by the transition from the settling to the transient heating phase.
- **Time data** was not adjusted during processing.

### 4.2 Instrumentation
- **TGA:** TGA/DSC 3+, Mettler Toledo
- **MCC:** Micro-scale Combustion Calorimeter, Fire Testing Technology

### 4.3 Calibration and Standards
- Devices were calibrated and verified according to the respective standards.

### 4.4 Experimental Conditions

**Environmental Conditions:**
- 23 ± 2°C, 50% relative humidity (standard laboratory air conditioning)

**TGA -- Isothermal:**
- After settling phase: heating to target temperature, then holding at constant temperature

**TGA -- Non-isothermal:**
- After settling phase: heating at constant heating rate until final temperature

**MCC:**
- Manual settling phase followed by heating at constant heating rate to final temperature
- Method A according to ASTM D7309:2021
- Additional experimental details are included within the respective data files

**Information regarding the mass (initial, end):**
- At the end of each experiment, the residual mass was measured. The residual mass was below the measurement uncertainty. It was therefore concluded that no mass remained at the end of the experiment.
- In MCC files, initial mass is given explicit.
- The mass signal of the TGA is initially set to the entered mass. The TGA itself only measures the difference in weight.

---

### 4.5 File Naming Convention

| Element         | Meaning                                      |
|-----------------|----------------------------------------------|
| `dynXY`         | Heating rate of XY K/min                      |
| `piece` / `powder` | Sample configuration                      |
| `1mg`, `2mg`, ...¦ | Nominal sample mass                           |
| `r1`, `r2`, ...¦   | Repetition number                             |
| `dynamic`       | Non-isothermal experiment                     |
| `isotherm`      | Isothermal experiment                         |
| `n2highXY`,`n2lowXY`      | Non-isothermal experiment with overall purge rate of XY ccm/min                         |

---

## 5. Data & File Overview

**Folder Structure:**
- **`mcc`** --  MCC data
- **`tga_isotherm`** -- Isothermal TGA data
- **`tga_nonisotherm`** -- TGA data with constant heating rate

**TGA Data Columns:**

| Column Name | Unit  | Description               |
|-------------|-------|---------------------------|
| `ts`        | °C    | Sample temperature        |
| `t`         | s     | Time                      |
| `weight`    | mg    | Sample weight             |
| `tr`        | °C    | Reference temperature     |
