# Electromagnetic Field Analysis of Base Stations

This project performs an analysis of electromagnetic fields measured at Base Stations (BS) in Brazil. It uses data from electromagnetic measurements and the geographical locations of base stations, applying machine learning techniques to explore patterns and build predictive models.

## Data

- **Electromagnetic Field Measurements:** [Source](https://dados.gov.br/dados/conjuntos-dados/medicoes-de-campos-eletromagneticos1)
- **BS Locations:** [Source](https://www.telecocare.com.br/mapaerbs/)

## Project Steps

### 1. Preprocessing
- **DataFrames:** Creation of `df` (measurements) and `dferb` (BS locations).
- **Join:** Combining dataframes into `mdf` to associate measurements with their respective BS.

### 2. Feature Engineering
- **BS-Measurement Point Distance:** Calculation using the [Haversine Formula](https://en.wikipedia.org/wiki/Haversine_formula).

### 3. Exploratory Data Analysis (EDA)
- **Companies and Measurement Types:** Data from 8 companies across 4,086 municipalities, including both fixed and broadband measurements.
- **Maps:** Bounding box extraction using [OpenStreetMap](https://www.openstreetmap.org/).

### 4. Clustering
- **K-Means (k=5):** Clustering of measurements by Brazilian regions.
- **DBSCAN:** Grouping of nearby measurements, related to Fresnel and Fraunhofer field regions.

### 5. Variable Correlation
- **Latitude/Longitude:** Highly correlated due to the proximity of measurements to the BS.
- **Mean Value and % of Limit:** Non-linear correlation (% of Limit = 0.1275 * (Mean Value)², with 99.99% correlation).

### 6. Supervised Modeling
- Algorithms: **LR, SGD, Ridge, Lasso, ElasticNet, KNR, DTR, ABR, RF**.
- **Learning Curves:** Observed overfitting in KNR and DTR; underfitting in ABR.

### 7. Advanced Feature Engineering
- **New Features:** Power, Gain, Height (Tx/Rx), Frequency.
- **Impact:** Model performance improvements after including these variables.

## Future Improvements
- Outlier filtering.
- Exploring new mathematical expressions (e.g., antenna tilt).
- Model optimization.

## References

- [Electric Field Intensity Analysis of Base Stations](https://www.inatel.br/revista/busca/144-5-analise-da-intensidade-de-campo-s504918-1/file)
- [Wibowo et al., 2010 - Electric Field Intensity](https://core.ac.uk/download/pdf/42954572.pdf)
- [Arnold et al., 2010 - Power Consumption Modeling](https://www.semanticscholar.org/paper/Power-consumption-modeling-of-different-base-types-Arnold-Richter/da078d9f4c22c01e7acc4d85cc7bc929c61f3442/figure/2)
