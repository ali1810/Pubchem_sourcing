# Sourcing Solubility Data from PubChem

## Overview
In this study, we processed 50 million SMILES to obtain solubility data from PubChem, the world's largest collection of freely accessible chemical information. After preprocessing, we retrieved 66,639 raw data points. Following data cleaning, we refined the dataset to 53,789 entries, each with numerical values and units (e.g., g/L, mg/mL). Raw data is saved in `raw_0k_50000k.csv`, and cleaned data in `clean_0k_50000.csv`.

## Data Evaluation
To assess the quality of the sourced data, we compared it with literature solubility data using `unique_train4_new_24.csv`. We found 631 unique matching data points, enabling a comparison of PubChem and literature solubility values. This matching data is saved in `Pubchem_match.xlsx` and `Pubchem_match.csv`.

## Data Retrieval Process
- **SMILES and CID**: Retrieved from [PubChem](ftp://ftp.ncbi.nlm.nih.gov/pubchem/Compound/Extras/CID-SMILES.gz) with over 111 million compounds.
- **Chunking**: Processed in chunks of 10,000 SMILES for efficiency.
- **Data Sourcing**: Solubility data sourced using Pubchempy, saved to CSV files.
- **Data Cleaning**: Extracted and standardized solubility values using custom functions.

## Repository Structure
├── Sol_exp
│   ├── compound_solubility_data.csv
│   ├── Steps_for_solubility_experiment.md
├── src
│   ├── data_processing.py
│   ├── data_cleaning.py
├── raw_0k_50000k.csv
├── clean_0k_50000.csv
├── Pubchem_match.xlsx
├── Pubchem_match.csv
├── README.md
├── requirements.txt
└── results
    ├── cleaned_solubility_data.csv


