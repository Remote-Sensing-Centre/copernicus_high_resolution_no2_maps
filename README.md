# Copernicus high resolution NO2 maps
High resolution maps of NO2 concentration predicted using Copernicus data by ML model.

## Reproducibility and Repository Structure
To ensure full transparency and reproducibility, this repository supports two levels of replication:

### 1. Machine Learning Reproducibility (Quick Start)
You can instantly reproduce the Random Forest training, evaluation metrics, EDM correction, and SHAP analyses without complex setup.
* **Datasets:** Use the fully pre-processed datasets provided in the data repository. 
  * NO2_training_dataset_osm_8269826_hex_7_year_2023_2024_artificial_S5P_scaled_wind_shift_flag.csv: The training dataset containing data from multiple stations and artificial points (varying spatial coordinates).
  * NO2_test_dataset_osm_8269826_hex_7_year_2023_2024.csv: The independent hold-out test dataset containing data from a single withheld monitoring station. **Note:** Because this represents a single location used exclusively for final spatial validation, its geographic coordinates correctly remain constant across all rows, while temporal features vary.
* **Script:** Run the `Model reference NO2.ipynb` notebook.

### 2. Data Preparation Reproducibility (Full Pipeline)
To fully replicate the spatial data merging, weighting, and preprocessing steps from scratch, a relational SQL database setup is required.
* **Database Setup:** Import the provided raw `.csv` files into a relational database environment (e.g., using database management tools like DBeaver).
* **Script:** Update the database connection credentials in the `Data preparation.ipynb` script and run it to generate the pre-processed datasets.

---

## Setup for Windows
1. Install Python 3.11 (or later) from the Microsoft Store.

2. Open command line terminal window from Start menu. Create virtual environment in user's main directory and activate it:
``` bash
cd %HOMEPATH%
python -m venv no2predictrfvenv
%HOMEPATH%\no2predictrfvenv\Scripts\activate

3. Clone this repository and unpack it. In the terminal window change the active directory to the main directory of repository.  
Install requirements:  
Bash
pip install -r requirements.txt
4. Download data files from the data repository and place them in data catalog.  
5. Run Jupyter to open the notebook files:  
Bash
jupyter lab
