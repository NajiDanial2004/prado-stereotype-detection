# Detecting Social Stereotypes in Prado Artworks

This repository contains the code and notebooks for the bachelor's thesis:

**"Detecting Social Stereotypes in Artworks from El Prado Museum"**
Naji Danial — IE University, School of Science & Technology, 2026

## Overview

This project proposes a computational framework for detecting social stereotypes
in classical paintings from the Museo Nacional del Prado. Visual embeddings are
extracted from artwork images using pre-trained Vision Transformer models (SigLIP
and DINOv2) and mapped onto the warmth and competence dimensions of the
Stereotype Content Model (Fiske et al., 2002) using regression-based probing.

## Notebooks

| # | Notebook | Description |
|---|----------|-------------|
| 01 | `database_and_dataset_construction` | Builds the dataset from the Prado SQLite database, applies SADCAT filtering, and exports strict and neutral-imputed versions |
| 02 | `visual_embeddings_siglip` | Extracts SigLIP embeddings for the strict dataset |
| 03 | `visual_embeddings_dinov2` | Extracts DINOv2 embeddings for the strict dataset |
| 04 | `modeling_siglip_strict` | Ridge and Random Forest regression on SigLIP embeddings (strict dataset) |
| 05 | `modeling_dinov2_strict` | Ridge and Random Forest regression on DINOv2 embeddings (strict dataset) |
| 06 | `visual_embeddings_siglip_neutral` | Extracts SigLIP embeddings for the neutral-imputed dataset |
| 07 | `modeling_siglip_neutral` | Regression on SigLIP embeddings (neutral dataset) |
| 08 | `visual_embeddings_dinov2_neutral` | Extracts DINOv2 embeddings for the neutral-imputed dataset |
| 09 | `modeling_dinov2_neutral` | Regression on DINOv2 embeddings (neutral dataset) |
| 10 | `finetuning_siglip_strict` | Neural regression head experiments on frozen SigLIP encoder |
| 11 | `additional_experiments` | Stronger filtering, PCA dimensionality reduction, combined embeddings |
| 12 | `hypothesis_testing` | Animal symbolism analysis — taxonomy and contextual role comparisons |
| 13 | `interface_image_prediction` | Gradio interface for uploading a painting and predicting SCM scores |

## Models Used

- **SigLIP** (`google/siglip-base-patch16-224`) — vision-language model
- **DINOv2** (`facebook/dinov2-base`) — self-supervised vision model
- Both used as frozen feature extractors via HuggingFace Transformers

## Key Results

| Configuration | Warmth R² |
|--------------|-----------|
| SigLIP + Random Forest (strict) | 0.112 |
| SigLIP + Random Forest (filtered n≥5) | 0.171 |
| SigLIP + Random Forest (filtered + PCA-50) | **0.181** |
| DINOv2 + Random Forest (strict) | 0.083 |

Competence was unpredictable in all configurations due to a severe ceiling
effect in the SADCAT-derived target distribution.

## Data

Raw data comes from the Museo Nacional del Prado's public catalogue.
See `data/README.md` for instructions on how to reconstruct the dataset.
The SQLite database and image files are not included due to size constraints.

## Requirements
```bash
pip install -r requirements.txt
```

Embedding extraction (notebooks 02, 03, 06, 08) requires a CUDA-compatible GPU.
All other notebooks can run on CPU.

## Citation

If you use this code, please cite:

Danial, N. (2026). *Detecting social stereotypes in artworks from El Prado Museum*
[Bachelor's thesis]. IE University.
