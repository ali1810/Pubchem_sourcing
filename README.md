This project aims to source solubility data from the PubChem database by processing SMILES (Simplified Molecular Input Line Entry System) strings for chemical compounds. The study involved processing 50 million SMILES to retrieve solubility data, which was further cleaned and evaluated against literature data.

## Project Overview

PubChem is the world's largest collection of freely accessible chemical information. In this project, we utilized the PubChemPy Python library to retrieve solubility data for 50 million SMILES. The steps involved in the project are:

## Data Retrieval Process
- **SMILES and CID**: In order to source the data from Pubchem we need to know the CID(compound identifiers) of the compound along with smiles which we have Sourced from (https://ftp.ncbi.nlm.nih.gov/pubchem/Compound/Extras/CID-SMILES.gz), which contains information on over 111 million compounds.
We clean this file make the CID collumn and smiles column and save in the csv file with name 

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
## Installation

To install the required Python packages for this project, you can use the `requirements.txt` file. Run the following command:


pip install -r requirements.txt

## Contributing

Contributions are welcome! Please follow these steps to contribute:

1. Fork the repository.
2. Create a new branch:
   ```bash
   git checkout -b feature-branch-name

## License

This project is licensed under the MIT License.

## Contact

For any questions or further information, you can contact:

- **Mushtaq Ali** - [mushtaq.ali@kit.edu](mailto:dev.punjabi@kit.edu)
- **Nicole Jung** - [nicole.jung@kit.edu](mailto:nicole.jung@kit.edu)

- **Institution**:  - [https://www.ibcs.kit.edu](https://www.ibcs.kit.edu)

### Conclusion

The project successfully sourced, processed, and evaluated solubility data from the PubChem database for 50 million chemical compounds. Utilizing the PubChemPy library, we retrieved 66,639 raw solubility data entries, which were subsequently cleaned and standardized, resulting in 53,789 usable data points.

This clean dataset, which includes numerical solubility values with appropriate units, serves as a valuable resource for further chemical research and analysis. Our comparison with literature data identified 631 matching entries, validating the accuracy and reliability of the sourced solubility data.

This study demonstrates the feasibility of large-scale data extraction and processing from PubChem, providing a foundation for other researchers to obtain and analyze chemical data at scale. The resulting dataset and scripts are available for further exploration and improvement, supporting ongoing research in the fields of chemistry and material science.
