# Aviation Accident Analysis

## Project Overview

This project analyzes aviation accident data from 1948–2023 on behalf of a fictional airline insurance client. The goal is to identify which aircraft makes and models have the lowest rates of passenger injury and aircraft destruction in the event of an accident, and to uncover broader factors that contribute to accident severity.

The analysis is split into two notebooks: one focused on data cleaning and one on exploratory data analysis and recommendations.

---

## Business Problem

An airline insurer wants to know:
- Which aircraft manufacturers and specific models are the safest to insure?
- Are there conditions or flight characteristics that predict worse accident outcomes?
- Separate recommendations are needed for **small aircraft** (under 20 passengers) and **large commercial aircraft** (20+ passengers).

---

## Data

- **Source:** NTSB Aviation Accident Database (1948–2023)
- **Key fields used:** Make, Model, Total Fatal/Serious/Minor Injuries, Total Uninjured, Aircraft Damage, Weather Condition, Phase of Flight, Engine Type, Number of Engines
- **Filters applied:** accidents from 1983 onwards, professionally built aircraft only, fixed-wing airplanes only

---

## Notebooks

### 1. `Aviation_Accidents_Cleaning.ipynb`
Covers all data loading, inspection, and cleaning steps:
- Filtered data to 1983+ professional-build airplanes
- Imputed missing injury counts and created `Fatal.Serious.Rate` (fraction of passengers seriously or fatally injured)
- Created `Is.Destroyed` column (1 = aircraft destroyed, 0 = survived)
- Standardized the `Make` and `Model` columns and created a unique `Make.Model` identifier
- Cleaned auxiliary columns: Engine Type, Weather Condition, Number of Engines, Purpose of Flight, Phase of Flight
- Dropped columns with more than 50% missing values
- Saved cleaned data to `AviationData_Cleaned.csv`

### 2. `Aviation_Accidents_Data_Analysis.ipynb`
Covers exploratory data analysis and client recommendations:
- Split data into small (<20 passengers) and large (≥20 passengers) aircraft
- Ranked manufacturers by mean fatal/serious injury rate and destruction rate
- Visualized injury rate distributions using violin plots (small aircraft) and strip plots (large aircraft)
- Identified the safest specific Make + Model combinations for each group
- Analyzed two contributing factors: **Weather Condition** and **Phase of Flight**

---

## Key Findings

- **Small aircraft:** Cessna and Piper consistently show the lowest injury and destruction rates. The Cessna 172 (and its variants) is the top-recommended model.
- **Large aircraft:** Boeing and McDonnell Douglas lead on safety metrics. The MD-83, MD-80, and Boeing 737 variants show the lowest mean injury rates among models with sufficient data.
- **Weather:** Accidents in IMC (instrument meteorological conditions / bad weather) result in roughly 3× higher injury rates and destruction rates compared to VMC (clear weather).
- **Phase of flight:** Maneuvering and cruise accidents are the most deadly. Landing and taxi accidents, despite being the most frequent, result in the lowest injury rates.

---

## Technologies Used

- Python 3
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook 