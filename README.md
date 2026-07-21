# G-Quadruplex Ligand Bioactivity Classifier



Predicts whether a small molecule stabilises G-quadruplex DNA with 0.974 cross-validated AUC, trained on 600 compounds from ChEMBL using interpretable ML.



## Highlights

- **CV AUC-ROC: 0.974 ± 0.010** across 5 stratified folds (Logistic Regression)

- **Test AUC-ROC: 0.895**, AUPRC: 0.950 on held-out data

- **9/10 known G4 ligands correctly identified** (PDS, BRACO-19, Berberine, Ellipticine, Doxorubicin)

- SHAP analysis identifies molecular weight and aromatic ring count as top predictors — consistent with the known G4 intercalation pharmacophore

- Built on ECFP4 Morgan fingerprints (2048-bit) + 7 RDKit physicochemical descriptors



## Results



![Test Set Evaluation](Results/test_evaluation.png)



ROC curve (AUC=0.895), Precision-Recall curve (AP=0.950), and confusion matrix on held-out test set.



![SHAP Summary](Results/shap_summary.png)



SHAP beeswarm plot, top 20 features driving G4 activity predictions. Red = high feature value pushes toward Active.



## Why This Project
G-quadruplexes (G4s) are four-stranded DNA structures in telomeres and oncogene promoters (c-MYC, KRAS, BCL2). Molecules that stabilise G4s suppress oncogene transcription and inhibit telomerase, a proven anticancer strategy. Experimental screening can be expensive, this classifier enables fast computational pre-screening from SMILES alone.

**Domain context:** Experimental work on G4 structures at Bose Institute (CD spectroscopy, thermal stabilisation assays) directly shaped the data curation decisions and made the SHAP findings interpretable in biological terms along with statistical ones.



## Methodology

- **Data**: 600 compounds from ChEMBL, labeled active/inactive for G4 stabilization

- **Features**: ECFP4 Morgan fingerprints (2048-bit) + 7 RDKit physicochemical descriptors

- **Class imbalance**: handled with SMOTE

- **Models benchmarked**: Logistic Regression, Random Forest, XGBoost, SVM

- **Validation**: 5-fold stratified cross-validation, held-out test set for final evaluation

- **Interpretability**: SHAP analysis to identify top predictive features

- **Final model: Logistic Regression** — selected for best CV performance and interpretability



## Model Comparison (5-Fold CV AUC-ROC)



| Model | AUC-ROC |
|---|---|
| Logistic Regression | 0.974 ± 0.010 |
| Random Forest | 0.973 ± 0.010 |
| XGBoost | 0.965 ± 0.013 |
| SVM | 0.964 ± 0.009 |



## Installation & Usage

```bash
pip install rdkit imbalanced-learn xgboost shap scikit-learn pandas numpy matplotlib seaborn
```


Open g4_ligand_classifier_final.ipynb and run cells in order. Requires the three ChEMBL activity CSV files in the same directory.



## Author

Agnidipa Sett M.Tech Bioinformatics, Delhi Technological University

