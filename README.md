This project aims to source solubility data from the PubChem database by processing SMILES (Simplified Molecular Input Line Entry System) strings for chemical compounds. The study involved processing 50 million SMILES to retrieve solubility data, which was further cleaned and evaluated against literature data.

## Project Overview

PubChem is the world's largest collection of freely accessible chemical information. In this project, we utilized the PubChemPy Python library to retrieve solubility data for 50 million SMILES. The steps involved in the project are:

## Data Retrieval Process
- **SMILES and CID**: In order to source the data from Pubchem we need to know the CID(compound identifiers) of the compound along with smiles which we have Sourced from (https://ftp.ncbi.nlm.nih.gov/pubchem/Compound/Extras/CID-SMILES.gz), which contains information on over 111 million compounds.
We clean this file (CID-SMILES.csv) make the CID column and smiles column and save in the csv file (CID-SMILES-fine.csv). These steps followed in the notrebook ( Pubchem_data_preparation.ipynb)

- **Chunking**: Processed in chunks of 10,000 SMILES for efficiency.
- **Data Sourcing**: Solubility data sourced using Pubchempy library and used a function to source the data and saved started with a csv file pubchem_0k_10k,csv after sourcing solubility data save this to (pubchem_new_0_10000_new.csv) file.These steps followed in the notrebook ( Pubchem_data_sourcing.ipynb)Once we have file with solubilities values the then we go further processing. 

2. **Data Processing**: Cleaning and converting the raw solubility data to a uniform format, including units like gm/l, mg/ml, g/ml, etc. We saved the processd and clean data file in to (pubchem_clean_0k_10000k.csv)'
3. **Data Evaluation**: Comparing the sourced data with literature solubility data to evaluate quality.These steps followed in the notrebook ( Pubchem_Post_Process.ipynb)

Above steps we have followed for all the raw files . Fisrt we have combine all the raw files namely newdf1 to newdf17 
and then combinbed all and saved to the file raw_0k_50000k.csv and then after preprocesing and cleaning save the file to clean_0k_50000k.csv . 
## Data Processing Summary
- **Total SMILES Processed**: 50 million
- **Raw Data Extracted**: 66,639 entries
- **Clean Data**: 53,789 entries, including numerical solubility values with units.
- **Furher Clean Data**: 32,874 entries, including numerical solubility values with units.
- **Match data with Literatute**: We also compare Literature dataponits 19219 with Pubchem data and found 368 mathcing dataponits and the compare the soulbilities values and and did the analysis.  
- **Again devided**: We have further devided the data in to salts and without salts compound where we found 811 (with salts) 32063 (without salts) 
- **Solubility prediction with Husskonen Data**: We also compare the with salts and without salts data to compare the solubility prediction on the Husskonen test data.This comparison has given that without salts data point has given better result compare the to with salts data ponits. Without salts 32063 dataponitns has given with 123 descriptors on the Husskonen 1282 dataponits MAE 0.92 and R2 0.62.


## Data Evaluation
The raw data is saved in `raw_0k_50000k.csv`, and the clean data is stored in `clean_0k_50000.csv`. For quality evaluation, we compared our results with literature solubility we compare with file unique_train4_new24.csv and found 631 unique matching entries, which are saved in `Pubchem_match.xlsx` and `Pubchem_match.csv`.

## Repository Structure

- **data/**: Contains all datasets used in the study.
  - `Pubchem_match.csv`
  - `clean_0k_50000.csv`
  - `pubchem_0k_10k.csv`
  - `pubchem_clean_0k_10000k_new.csv`
  - `pubchem_new_0_10000.csv`
  - `pubchem_new_0_10000_new.csv`
  - `raw_0k_50000k.csv`
- **notebooks/**: Jupyter notebooks containing the analysis, preprocessing, and model training code.
  - `Pubchem_Post_Process.ipynb`
  - `Pubchem4_data_preparation.ipynb
  - `Pubchem_final_process_0k_50000.ipynb`
  - `pubchem_data_sourcing.ipynb`

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

The project successfully sourced, processed, and evaluated solubility data from the PubChem database for 50 million chemical compounds. Utilizing the PubChemPy library, we retrieved 66,639 raw solubility data entries, which were subsequently cleaned and standardized, resulting in 53,789 usable data points. To ensure data accuracy, we performed a thorough cleaning process to align our source data with literature values. This involved detailed filtering to exclude values marked with "greater than" or "less than" indicators, ultimately yielding a refined dataset of 32,784 data points. This dataset was then compared with a curated literature dataset containing 19,219 data points (Used for solubility prediction work 17,937 for training and 1,282 for testing). Upon comparison, we identified 368 matching compounds, providing insight into discrepancies between PubChem data and literature standards. This process established clear guidelines for data cleaning, ensuring a more reliable dataset. You can access the data file [here](data/Pubchem_match_368.csv).

This study demonstrates the feasibility of large-scale data extraction and processing from PubChem, providing a foundation for other researchers to obtain and analyze chemical data at scale. The resulting dataset and scripts are available for further exploration and improvement, supporting ongoing research in the fields of chemistry and material science.
