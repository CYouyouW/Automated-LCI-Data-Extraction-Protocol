# Automated LCI Data Extraction
💫This repository provides an automated data extraction and matrix construction tool for databases such as Ecoinvent. It can directly process native EcoSpold v2 (.spold) files without relying on commercial software, automatically handling data parsing, cleaning, and standardization, and ultimately generating a sparse flow × process matrix.

With this workflow, researchers can:

Efficiently extract and integrate LCI data, avoiding the complexity and errors of manual handling;

Obtain a high-quality numerical matrix consisting of tens of thousands of processes and flows ;

Retain rich textual information to support semantic modeling and machine learning tasks;

Build a solid data foundation for missing data prediction and automated LCA analysis.



# Input and Output
Input: .spold files from the Ecoinvent 3.11 database(allocation at the point of substitution, apos) and the corresponding mapping table (FilenameToActivityLookup.csv).
Output: An LCA matrix in CSV format with flows as rows and processes as columns.


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
💥Please cite our paper if you find it helpful :) 