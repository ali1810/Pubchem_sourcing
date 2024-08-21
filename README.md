This project aims to source solubility data from the PubChem database by processing SMILES (Simplified Molecular Input Line Entry System) strings for chemical compounds. The study involved processing 50 million SMILES to retrieve solubility data, which was further cleaned and evaluated against literature data.

## Project Overview

PubChem is the world's largest collection of freely accessible chemical information. In this project, we utilized the PubChemPy Python library to retrieve solubility data for 50 million SMILES. The steps involved in the project are:

## Data Retrieval Process
- **SMILES and CID**: Sourced from (https://ftp.ncbi.nlm.nih.gov/pubchem/Compound/Extras/CID-SMILES.gz), which contains information on over 111 million compounds.

- **Chunking**: Processed in chunks of 10,000 SMILES for efficiency.
- **Data Sourcing**: Solubility data sourced using Pubchempy, saved to CSV files.

2. **Data Processing**: Cleaning and converting the raw solubility data to a uniform format, including units like gm/l, mg/ml, g/ml, etc.
3. **Data Evaluation**: Comparing the sourced data with literature solubility data to evaluate quality.

## Data Processing Summary

- **Total SMILES Processed**: 50 million
- **Raw Data Extracted**: 66,639 entries
- **Clean Data**: 53,789 entries, including numerical solubility values with units.

The raw data is saved in `raw_0k_50000k.csv`, and the clean data is stored in `clean_0k_50000.csv`. For quality evaluation, we compared our results with literature solubility data and found 631 unique matching entries, which are saved in `Pubchem_match.xlsx` and `Pubchem_match.csv`.

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
