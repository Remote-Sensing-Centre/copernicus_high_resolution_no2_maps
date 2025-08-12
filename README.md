# Copernicus high resolution NO2 maps
High resolution maps of NO2 concentration predicted using Copernicus data by ML model

## Setup for Windows
1. Install Python 3.11 (or later) from the Microsoft Store.

2. Open command line terminal window from Start menu. Create virtual environment in user's main directory and activate it:
``` bash
cd %HOMEPATH%
python -m venv no2predictrfvenv
%HOMEPATH%\no2predictrfvenv\Scripts\activate
```

3. Clone this repository and unpack it. In the terminal window change the active directory to the main directory of repository.

4. Install requirements:
``` bash
pip install -r requirements.txt
```

5. Download data files from the [data repository](https://igikedupl-my.sharepoint.com/:f:/g/personal/konrad_wroblewski_igik_edu_pl/EnYfqpWu4QdAgoqeYczef7EBzU4ocOp5rrZ3vwNQqHy7ZQ?e=3rvnPK) and place them in **data** catalog.

6. Run Jupyter to open the notebook files:
``` bash
jupyter lab
```
