# Colorado Canopy Change Detection

This project investigates forest canopy change over time at NEON field sites in Colorado using multi-year Canopy Height Model (CHM) data. Through exploratory data analysis (EDA) and supervised classification, the project identifies zones of canopy growth, loss, or stability. The work blends geospatial raster analysis with machine learning to produce interpretable ecological insights.

## 📊 Project Goals
- Quantify canopy height changes using CHM raster differencing
- Visualize spatial patterns of forest disturbance and regrowth
- Train a machine learning model to classify land cover or canopy change zones

## 🗂️ Data Sources
- **NEON CHM Data** ([DP3.30015.001](https://data.neonscience.org/data-products/DP3.30015.001))
- **NEON Vegetation Indices** ([DP3.30006.001](https://data.neonscience.org/data-products/DP3.30006.001)) – optional
- **NEON Disturbance Logs** ([DP1.10111.001](https://data.neonscience.org/data-products/DP1.10111.001)) – optional
- Study area: Colorado NEON sites (e.g., NIWO, CPER, ARIK)

## 🧠 Methods
- Load and align multi-year CHM rasters
- Calculate canopy height difference raster (e.g., CHM_2023 - CHM_2019)
- Conduct EDA: histograms, spatial plots, patch summaries
- Train a classification model (e.g., Random Forest) to categorize patches

## 📦 Tools & Libraries
- Python: `rasterio`, `numpy`, `pandas`, `matplotlib`, `scikit-learn`, `geopandas`, `seaborn`
- Jupyter Notebooks for reproducibility
- GitHub for version control and documentation

## 🗓️ Timeline
See the [project proposal](./project_proposal.md) for a full breakdown.

## 🧾 License
MIT License or add your preferred license.

## 🤝 Acknowledgments
NEON data is provided courtesy of Battelle and the National Science Foundation.

