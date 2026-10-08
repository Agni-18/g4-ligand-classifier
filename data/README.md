# Data

This folder holds the three ChEMBL activity exports used by the notebook, named `DOWNLOAD-*.csv`.

- Source: ChEMBL web interface, https://www.ebi.ac.uk/chembl/
- Format: semicolon-separated, double-quoted
- Columns used: `Molecule ChEMBL ID`, `Smiles`, `Standard Type`, `Standard Value`, `Standard Units`
- License: ChEMBL data are released under CC BY-SA 3.0. Please cite ChEMBL if you reuse them.

The notebook reads every file matching `DOWNLOAD-*.csv` in this folder.
