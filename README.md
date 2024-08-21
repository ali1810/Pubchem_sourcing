# Sourcing Solubility Data from PubChem

## Overview
In this study, we processed 50 million SMILES to obtain solubility data from PubChem, the world's largest collection of freely accessible chemical information. After preprocessing, we retrieved 66,639 raw data points. Following data cleaning, we refined the dataset to 53,789 entries, each with numerical values and units (e.g., g/L, mg/mL). Raw data is saved in `raw_0k_50000k.csv`, and cleaned data in `clean_0k_50000.csv`.

## Data Retrieval Process
- **SMILES and CID**: Sourced from [PubChem](https://ftp.ncbi.nlm.nih.gov/pubchem/Compound/Extras/CID-SMILES.gz), which contains information on over 111 million compounds.

- **Chunking**: Processed in chunks of 10,000 SMILES for efficiency.
- **Data Sourcing**: Solubility data sourced using Pubchempy, saved to CSV files.
- **Data Cleaning**: Extracted and standardized solubility values using custom functions.

## Data Evaluation
To assess the quality of the sourced data, we compared it with literature solubility data using `unique_train4_new_24.csv`. We found 631 unique matching data points, enabling a comparison of PubChem and literature solubility values. This matching data is saved in `Pubchem_match.xlsx` and `Pubchem_match.csv`.

## Repository Structure

- **data/**: Contains all datasets used in the study.
  - `water_solubility_data.csv`
  - `dataset-not-FA.csv`
  - `Supplementary_data.csv`
  - `data_paper.csv`
  - `dataset-E.csv`
  - `unique_train4_new24.csv`
  - `unique_test_new24.csv`
  - `overlap_data_new.csv`

- **notebooks/**: Jupyter notebooks containing the analysis, preprocessing, and model training code.
  - `data_preprocess_3_24.ipynb`
  - `4_24.ipynb`
  - `feature_fg7_fe_38.ipynb`
  - `Sorkundata_improve_Preprocess.ipynb`
  - `mpnn.ipynb`

- **scripts/**: Function to create the discriptors used in the study.
  - `utilities.py`

- **results/**: Contains the comparative model results.
  - `model_results.csv`
  - `compare_results.csv`
