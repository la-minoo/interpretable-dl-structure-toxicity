# Results

- **`results_tables.docx`** — writeup-formatted tables.
- **`*.csv`** — the same numbers, machine-readable, one file per table (or sub-table) for direct load.

| CSV file | Contents |
|---|---|
| `table1_dataset_groundtruth.csv` | Dataset composition, split sizes, ground-truth coverage |
| `table2_model_performance.csv` | AUROC / AUPRC / accuracy, both models, Ames test set |
| `table3_attribution_diagnostics.csv` | Completeness-check errors, extraction success, unassigned attribution mass |
| `table4_faithfulness_metrics.csv` | **Core result.** Comprehensiveness, sufficiency, deletion AUC, insertion AUC — means, SDs, paired t and Wilcoxon p-values |
| `table5a_toxicophore_subsets.csv` | Subset construction for toxicophore-recovery analysis |
| `table5b_toxicophore_iou.csv` | IoU recovery of ground-truth toxicophore atoms |
| `table6_distribution_shift.csv` | Faithfulness stratified by train-set similarity (robustness check) |
| `table7a_tox21_setup.csv` | Second-endpoint (Tox21/SR-ARE) dataset and split |
| `table7b_tox21_performance.csv` | Tox21 model performance and calibration |
| `table7c_tox21_comprehensiveness.csv` | Tox21 comprehensiveness replication result |

All values verified against the executed notebook outputs (`raw_notebooks/`) before being tabulated. 
P-values are reported as Python-style scientific notation (e.g., `5.84e-88`) for direct parsing.
