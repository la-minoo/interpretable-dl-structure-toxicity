# Interpretable Deep Learning of Structure–Toxicity Relationships
### A Faithfulness-Based Comparison of Sequence and Graph Molecular Representations

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![Python](https://img.shields.io/badge/python-3.10%2B-blue.svg)
![Status](https://img.shields.io/badge/preprint-in%20progress-orange)
![src](https://img.shields.io/badge/src-under%20development-lightgrey)

## Overview

Chemical language models (sequence-based, e.g., SMILES transformers) and graph neural networks are both widely used for molecular property prediction, and both are routinely paired with post-hoc explanation methods. This project asks a question that, to our knowledge, no prior study directly tests: **when a sequence model and a graph model make the same prediction, do their explanations rely on the same causal chemistry — and if not, which one can you trust?**

We answer this with a pre-registered, causal (perturbation-based) faithfulness protocol applied identically to a fine-tuned chemical language model (ChemBERTa) and a graph neural network (GIN), on Ames mutagenicity prediction, validated against a curated toxicophore ground truth, and stress-tested for robustness to distribution shift and a second, independent endpoint (Tox21).

## Key Finding

Across four independent, causal faithfulness metrics (comprehensiveness, sufficiency, deletion AUC, insertion AUC) and a direct comparison against ground-truth structural alerts, **ChemBERTa's attributions are consistently, substantially, and overwhelmingly more faithful than GIN's** (all paired comparisons p < 10⁻⁸⁰ on the primary endpoint, n = 1,457). This advantage is stable under distribution shift and replicates on an independent, differently-imbalanced endpoint (Tox21/SR-ARE). GIN shows a distinct, architecture-specific fragility pattern — modest but genuine faithfulness under moderate interventions, complete collapse under extreme atom removal (traced to sum-pooling and float underflow) — that recurs across multiple, unrelated stress conditions throughout the study.

Full numerical results: [`results/`](./results) (publication-formatted tables and machine-readable CSVs).

## Repository Structure

```
├── README.md
├── LICENSE
├── requirements.txt
├── raw_notebooks/     # Original executed Kaggle notebooks (idl-project1/2/3)
├── src/                # Clean, phase-organized pipeline code — UNDER DEVELOPMENT
├── figures/            # Publication figure generation (matplotlib + RDKit)
├── results/            # Complete numerical results: docx tables + CSVs
└── data/               # Pointers to externally-hosted attributions/metrics (Kaggle)
```

**Note on `src/`:** the executed pipeline currently lives in `raw_notebooks/` (three notebooks covering Phases 1–7, with real outputs). Cleaned, reusable versions of this code, organized one file per phase, are planned for `src/` but not yet uploaded — check `raw_notebooks/README.md` for which notebook covers which phases in the meantime.

## Data and Models

- **Dataset:** PyTDC AMES mutagenicity benchmark (Xu et al. / Hansen et al.), scaffold-split.
- **Ground truth:** Atom-level toxicophore masks from Rao et al. (2022, *Patterns*) — not redistributed here; see their original repository.
- **Models:** GIN (trained from scratch, PyTorch Geometric) and ChemBERTa (`seyonec/ChemBERTa-zinc-base-v1`, fine-tuned). Fine-tuned ChemBERTa final model hosted on HF Models: *[minoola/chemberta-zinc-base-v1-ames-mutagenicity](https://huggingface.co/minoola/chemberta-zinc-base-v1-ames-mutagenicity/)*.
- **Second endpoint:** Tox21/SR-ARE (PyTDC), used for the robustness replication.
- **Attributions and metric outputs:** hosted on Kaggle Datasets — see [`data/README.md`](./data/README.md).

## Status

- ✅ Core study complete: protocol, training, attribution extraction, faithfulness metrics, toxicophore recovery, robustness checks (distribution shift + second endpoint).
- 🔶 Preprint: in progress.
- 🔶 `src/`: cleaned phase-organized code in progress — currently only raw executed notebooks are available.

## Authors

- **Minoo La** — Korea University Business School *(corresponding author)*
- **Sai Thet Hmuu** — School of Biosystems and Biomedical Sciences, Korea University

## Citation

Preprint in progress — citation details will be added here once available.

## License

Code released under the [MIT License](./LICENSE). Ground-truth toxicophore data and original pretrained models are subject to their original sources' terms.
