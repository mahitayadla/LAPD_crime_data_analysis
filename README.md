# LAPD Crime Analysis — Patterns, Trends & Demographics
*A Complete Data Cleaning, EDA, and Visualization Project*


## Overview
This project focuses on analyzing publicly available crime data from the Los Angeles Police Department (LAPD) to uncover patterns, trends, and demographic insights. The analysis combines Python-based Exploratory Data Analysis (EDA) with Tableau visual storytelling to present clear, data-driven findings.

The project workflow includes:

- Raw data inspection and understanding of structure  
- Data cleaning and preprocessing  
- Exploratory Data Analysis (EDA) using Python  
- Interactive dashboards and stories using Tableau

---

### Dataset  
**Source:** Crime Data from 2020 to Present — U.S. Government Open Data Portal  
Dataset Link: https://catalog.data.gov/dataset/crime-data-from-2020-to-present  

- **Total Records:** *901,695*

This dataset contains detailed records of reported crimes in Los Angeles, including:

- Crime type and crime code descriptions  
- Occurrence and reporting dates  
- Victim age, gender, and descent   
- Premise/location type  
- Geographic coordinates (latitude & longitude)
  
The overall goal of this project is to understand crime patterns across **time**, **location**, and **demographics**, visualize these insights in a meaningful way, and identify data-driven recommendations that can support better crime-prevention strategies.

---

### LAPD Divisions Shapefile

This project uses the **`LAPD_Divisions.shp`** file to enable geographic visualization of LAPD divisions in Tableau. The `.shp` file is a geospatial vector data format that represents geographic features as polygons. In this case, it contains the boundaries of all LAPD divisions in Los Angeles.

Source: https://geohub.lacity.org/datasets/lahub::lapd-divisions/about

#### Details of the `.shp` File

- **Content:** Contains polygon geometries representing each LAPD division. Each polygon defines the exact boundaries of a division using a set of vertices.
- **Purpose:** Provides the spatial layer in Tableau for creating maps where divisions can be visualized individually.

#### Usage in Tableau

1. **Importing the Shapefile**  
   - The `.shp` file was imported directly into Tableau as a spatial data source. Tableau automatically recognized the polygons and rendered them on a map.

2. **Integrating Crime Data**  
   - Crime statistics were visualized by mapping counts, categories, or other metrics onto the division polygons.  
   - This allowed the creation of interactive dashboards showing crime trends and patterns per division.

---

## Data Cleaning & Preprocessing

All cleaning steps are performed in **`Crime_data_EDA.ipynb`**.

### 1. Initial Inspection
- Checked dataset shape, column names, and data types  
- Identified missing values and inconsistent formats  

### 2. Date & Time Cleaning
- Converted date/time columns into `datetime` format  
- Adjusted any invalid or malformed date entries  

### 3. Handling Missing Values
- Dropped records with critical missing fields (e.g., crime code)  
- Handled missing demographic values appropriately  

### 4. Text Standardization 
- Merged inconsistent category labels (e.g., “UNK”, “Unknown”)  

### 5. Duplicate Rows Check
- Checked for duplicate rows using unique identifiers (e.g., DR Number)    

### 6. Outlier Detection & Fixing
- Removed impossible age values (e.g., < 0 or > 110)  
- Validated gender and descent categories  

### 7. Geospatial Processing
- Cleaned latitude/longitude values  
- Prepared cleaned location fields for Tableau mapping

### 8. Feature Engineering
- Extracted **Hour of Occurrence (`hour_occ`)** from the crime time field    

### 9. Column Selection
- Retained only the columns required for analysis and visualization   
- Ensured all selected features contributed meaningful analytical value  

### 10. Export
- Exported cleaned dataset as a CSV  
- Loaded into Tableau for interactive visualization  

---

## Exploratory Data Analysis (EDA)

A light EDA was performed mainly to understand the basic distribution of key variables before visualization.  
This included:

- Category counts for Crime Description, Premise Description, and Area Name
- Distribution analysis for Victim Age, Sex, and Descent
- Checking high-level patterns to guide Tableau visualizations


## Tableau Interactive Story

**View the full Tableau Story:**  
https://public.tableau.com/app/profile/mahita.yadla/viz/LAPDCrimeAnalysisPatternsTrendsDemographics/Story1

The Tableau story includes:

- Crime timelines & yearly patterns  
- Monthly and hourly distributions  
- Crime type breakdowns by division  
- Victim demographics  
- Heatmaps and geographic hotspots  
- Summary insights  

---

## Key Insights

- Hispanic/Latino individuals are the most affected at 30.3%, followed by White (20.3%) and Black (14%).
- Males and adults aged 25-44 are most commonly victimized.
- Central LA and 77th Street have the highest crime volumes, but Harbor division leads in clearance rate (13.2%).
- Afternoon hours see the highest crime activity across all divisions. Property crimes peak when homes are empty, while night consistently has the lowest crime.
- Property crimes constitute the majority of offenses
  
---

## Recommendations
- Prioritize patrol resources during afternoon and evening hours
- Study Harbor division's practices to improve other divisions
- Improve data collection to reduce "Unknown" demographic entries

---

## Limitations

- 23-25% of demographic data is missing, which may affect victim profile accuracy
- Analysis only includes reported crimes, unreported incidents are not captured
- External factors influencing clearance rates are not included in this dataset

---

## Future Improvements
- Integrating live and continuously updated LAPD crime data instead of a static snapshot  
- Deploying an interactive web app (Streamlit) with filters for year, month, area, and crime type, along with interactive mapping  
- Applying NLP techniques to crime narrative descriptions (when available) for pattern detection and key insights. 
