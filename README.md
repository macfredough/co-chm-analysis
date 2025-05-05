# 🌲 Colorado Canopy Change Detection

This project investigates forest canopy change over time at NEON field sites in Colorado using multi-year Canopy Height Model (CHM) data. Through exploratory data analysis (EDA), terrain analysis, and supervised machine learning, it identifies zones of canopy **gain**, **loss**, or **stability**. The work blends geospatial raster processing with model-based classification to produce interpretable ecological insights.

---

## Project Goals

- Quantify canopy height changes using CHM raster differencing  
- Visualize spatial patterns of forest disturbance and regrowth  
- Build a Random Forest classifier to predict canopy change classes  
- Map predictions back to the landscape for spatial interpretation  

---

## Data Sources

- NEON CHM Data (DP3.30015.001)  
- NEON Vegetation Indices (DP3.30026.001)  
- NEON Slope and Aspect Data (DP3.30025.001)  
- Study area: Colorado NEON sites (NIWO, WLOU, STER, CPER, RMNP, ARIK)  

> All data is accessed via the NEON API or preprocessed into site-year mosaics using Python.

---

## Methodology Overview

The workflow consists of 7 key phases:

### **Phase 1 – Data Preparation**
- Mosaicked 1 km² CHM and VegIndex tiles for each site-year
- Aligned all rasters to the CHM reference grid (first year per site)

### **Phase 2 – Feature Extraction**
- Computed CHM difference rasters per site-year pair
- Aggregated 100×100 pixel block summaries: gain/loss/stable %, mean CHM stats
- Sampled aligned VegIndex rasters and computed index means per block

### **Phase 3 – Class Distribution**
- Assigned labels using a 10% gain/loss threshold per block  
- Addressed class imbalance by downsampling the dominant “Stable” class  

### **Phase 4 – Topographic Feature Integration**
- Downloaded and resampled terrain rasters (slope, aspect)
- Validated spatial alignment with CHM rasters
- Added terrain-derived features to the feature table

### **Phase 5 – Hybrid Resampling and Model Training**
- Combined CHM, VegIndex, and terrain features
- Trained a Random Forest classifier using stratified train-test splits
- Evaluated accuracy, F1 scores, and feature importance

### **Phase 6 – Model Integrity Check**
- Verified spatial alignment and feature consistency
- Removed high-leakage features (e.g., direct CHM differences) to improve generalization

### **Phase 7 – Spatial Prediction and Visualization**
- Applied trained model to the full dataset
- Exported predicted labels with spatial offsets
- Visualized gain/loss/stable patterns as block-based maps
- Compared predicted maps to actual CHM-Δ rasters for qualitative validation

---

## 📓 Notebooks

This repository includes two core Jupyter Notebooks:

### `CHM_Analysis_and_Thresholds.ipynb`
- Loads NEON CHM data  
- Runs EDA and CHM histogram comparisons  
- Defines labeling strategy using block-level percent change  
- Tests threshold sensitivity and class balance  

### `ML_Pipeline_CanopyChange.ipynb`
- Loads all extracted features  
- Trains Random Forest models on terrain-only and hybrid features  
- Evaluates classification performance  
- Maps predictions spatially and compares to CHM-Δ rasters  

---

## Tools & Libraries

- **Python**: rasterio, numpy, pandas, matplotlib, seaborn, scikit-learn, geopandas  
- **Jupyter Notebooks** for development and reproducibility  
- **GitHub** for version control and collaboration  

---

## Timeline

This work was conducted as part of the final practicum for the Regis University M.S. in Data Science program.  
Project milestones followed the agile phases described above.

---

## Acknowledgments

- NEON data provided courtesy of Battelle and the National Science Foundation (NSF).
- Project supervised by faculty from the MSDS 696 Practicum II course at Regis University.
