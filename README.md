# Copernicus High-Resolution NO₂ Maps

This repository contains the source code and Jupyter notebooks used to estimate ground-level NO₂ concentrations using a Random Forest model integrating satellite, meteorological, land-cover, traffic, and ground-based monitoring data.

## Data and Code Availability

The project resources are provided in two separate repositories:

- **Data repository (SharePoint):**  
  [air_pollution_igik](https://igikedupl-my.sharepoint.com/:f:/g/personal/magdalena_lagiewska_igik_edu_pl/IgC84gtPFQfGT49Q6njjN3_xAWSNwF7nMQQQd9WWEiWK1hQ?e=IFNvba)

  This repository contains the datasets used for model training, validation, and independent testing.

- **Code repository (GitHub):**  
  This GitHub repository contains the source code, Jupyter notebooks, and configuration files required to reproduce the analyses described in the manuscript.

---

## Reproducibility

Two levels of reproducibility are provided.

### 1. Machine Learning Reproducibility — Quick Start

The Random Forest modelling workflow can be reproduced using the fully pre-processed datasets available in the data repository.

### Required datasets

Download the following files from the SharePoint data repository:

- `NO2_training_dataset_osm_8269826_hex_7_year_2023_2024_artificial_S5P_scaled_wind_shift_flag.csv`  
  Training dataset containing observations from multiple ground monitoring stations together with artificial non-urban reference points.

- `NO2_test_dataset_osm_8269826_hex_7_year_2023_2024.csv`  
  Independent spatial hold-out test dataset for the H3 resolution 7 grid. The dataset represents a single monitoring station that was completely excluded from model training and internal validation. Therefore, its spatial coordinates remain constant across observations, while temporal and environmental predictors vary.

- `NO2_test_dataset_osm_8269826_hex_9_year_2023_2024.csv`  
  Independent test dataset used to evaluate model inference at the finer H3 resolution 9 grid.

### Model reproduction

Run:

`Model reference NO2.ipynb`

The notebook reproduces the main machine learning workflow, including:

- training and internal validation split;
- Random Forest model fitting;
- model evaluation;
- Empirical Distribution Matching (EDM) correction;
- feature importance analysis;
- SHAP-based model interpretation.

The independent test datasets can then be used to evaluate the trained model at H3 resolutions 7 and 9.

---

### 2. Data Preparation Reproducibility — Full Pipeline

The complete preprocessing workflow requires the source datasets and a relational SQL database environment.

The preprocessing workflow includes:

- integration of satellite and ground-based observations;
- spatial aggregation to the H3 grid;
- generation of environmental and land-cover predictors;
- calculation of wind-dependent spatial features;
- generation of artificial non-urban reference points;
- preparation of the final machine-learning datasets.

### Database setup

1. Download the required source data from the data repository.
2. Import the provided source tables into a relational SQL database.
3. Update the database connection parameters in:

   `Data preparation.ipynb`

4. Run the notebook to reproduce the processed machine-learning datasets.

A database management application such as DBeaver can be used to manage the relational database.

---

## Windows Setup

### 1. Install Python

Install Python 3.11 or later.

### 2. Create a virtual environment

Open Command Prompt and run:

```bash
cd %HOMEPATH%
python -m venv no2predictrfvenv
%HOMEPATH%\no2predictrfvenv\Scripts\activate
