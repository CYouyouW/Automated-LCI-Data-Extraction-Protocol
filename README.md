# Automated LCI Data Extraction
💫This repository provides an automated data extraction and matrix construction tool for databases such as Ecoinvent. It can directly process native EcoSpold v2 (.spold) files without relying on commercial software, automatically handling data parsing, cleaning, and standardization, and ultimately generating a sparse flow × process matrix.

With this workflow, researchers can:

Efficiently extract and integrate LCI data, avoiding the complexity and errors of manual handling;

Obtain a high-quality numerical matrix consisting of tens of thousands of processes and flows ;

Retain rich textual information to support semantic modeling and machine learning tasks;

Build a solid data foundation for missing data prediction and automated LCA analysis.



# Input and Output
**Input**
- EcoSpold v2 `.spold` datasets from the Ecoinvent 3.11 APOS release (drop them under `data/spold/` or point `ECOSPOLD_ROOT` to another directory).
- `FilenameToActivityLookup.csv` (semicolon separated) that maps file prefixes to activity names and locations (defaults to `data/FilenameToActivityLookup.csv`, override with `FILENAME_LOOKUP`).
- `batch_number.txt`, which stores the rolling batch ID (created automatically in `outputs/` unless you set `LCA_BATCH_FILE`).

**Output**
Each run creates a timestamped batch folder (`<output_folder_base>/<MMDD>_<batch_number>/`) containing:
- A CSV per `.spold` file with cleaned intermediate and elementary exchanges (same basename as the source file).
- Logs and diagnostics: `processing_debug.txt`, `summary.txt`, `failed_files.txt`, and the spotlight lists `non1_amount_files.csv` and `neg1_amount_files.csv`.
- `global_activity_mapping.csv`, recording every activity ID discovered across the dataset.

The helper `build_lca_matrix` step then consolidates the per-activity CSVs into a sparse flow × process matrix and writes it to the path you pass as `output_file`.

Use `LCA_OUTPUT_ROOT` to relocate the batch directories if you prefer a different workspace.


# 📝Run
## ⛏️Installation
We recommend using a virtual environment.
```
git clone https://github.com/CYouyouW/Automated-LCI-Data-Extraction-Protocol.git
cd Automated-LCI-Data-Extraction-Protocol
pip install -r requirements.txt

```



# 💐Contributing to Automated LCI Data Extraction Protocol 
- **Reporting bugs.** To report a bug, simply open an issue in the GitHub [Issues](https://github.com/CYouyouW/Automated-LCI-Data-Extraction-Protocol/issues).
- **Suggesting enhancements.** To submit an enhancement suggestion, including completely new features or minor improvements on existing features, please open an issue in the GitHub [Issues](https://github.com/CYouyouW/Automated-LCI-Data-Extraction-Protocol/issues).
- **Pull requests.** If you made improvements to FidelityFusion, fixed a bug, or had a new example, feel free to send us a pull-request.
- **Asking questions.** To get help on how to use FidelityFusion or its functionalities, you can open a discussion in the GitHub.


# 🤗Citation
💥Please cite our paper if you find it helpful :) SemaNet: Bridging Words and Numbers For Predicting Missing Environmental Data in Life Cycle Assessment. DOI: https://doi.org/10.1021/acs.est.5c07557
