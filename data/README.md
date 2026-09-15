# Data

Attribution and metric outputs are currently hosted externally.

| File | Contents |
|---|---|
| `gin_attributions.pkl` | Per-atom Integrated Gradients scores, GIN, full test set (n=1,457) |
| `chemberta_attributions.pkl` | Per-atom aligned attribution scores + unassigned-mass diagnostics, ChemBERTa (n=1,457) |
| `gin_all_metrics_CORRECTED.pkl` | Final comprehensiveness/sufficiency/deletion/insertion scores, GIN |
| `chemberta_all_metrics_CORRECTED.pkl` | Same, ChemBERTa |
| `gin_toxicophore_recovery.pkl` | Toxicophore IoU recovery scores, GIN (n=479 primary subset) |
| `chemberta_toxicophore_recovery.pkl` | Same, ChemBERTa |

Ground-truth toxicophore masks (`attributions.npz`) are Rao et al. (2022)'s XAI Muagenicity data, of course not redistributed here.
