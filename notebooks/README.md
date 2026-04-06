# Notebooks

This folder contains all Jupyter notebooks for the project, numbered in execution order.

| # | Notebook | Description |
|---|----------|-------------|
| 01 | `01_database_and_dataset_construction` | Builds the dataset from the Prado SQLite database, applies SADCAT filtering, exports strict and neutral-imputed versions |
| 02 | `02_visual_embeddings_siglip` | Extracts SigLIP embeddings for the strict dataset |
| 03 | `03_visual_embeddings_dinov2` | Extracts DINOv2 embeddings for the strict dataset |
| 04 | `04_modeling_siglip_strict` | Ridge and Random Forest regression on SigLIP embeddings (strict dataset) |
| 05 | `05_modeling_dinov2_strict` | Ridge and Random Forest regression on DINOv2 embeddings (strict dataset) |
| 06 | `06_visual_embeddings_siglip_neutral` | Extracts SigLIP embeddings for the neutral-imputed dataset |
| 07 | `07_modeling_siglip_neutral` | Ridge and Random Forest regression on SigLIP embeddings (neutral dataset) |
| 08 | `08_visual_embeddings_dinov2_neutral` | Extracts DINOv2 embeddings for the neutral-imputed dataset |
| 09 | `09_modeling_dinov2_neutral` | Ridge and Random Forest regression on DINOv2 embeddings (neutral dataset) |
| 10 | `10_finetuning_siglip_strict` | Neural regression head experiments on frozen SigLIP encoder, two architectures |
| 11 | `11_additional_experiments` | Stronger filtering, PCA dimensionality reduction, combined SigLIP+DINOv2 embeddings |
| 12 | `12_hypothesis_testing` | Animal symbolism analysis — taxonomy categories and contextual role comparisons |
| 13 | `13_interface_image_prediction` | Gradio interface for uploading a painting and predicting warmth and competence scores |

## Notes

- Notebooks 02, 03, 06, and 08 (embedding extraction) require a CUDA-compatible GPU and will be slow on CPU.
- All other notebooks can run on CPU.
- Run notebooks in numerical order — each one depends on outputs from the previous.
- The database path (`agrupa.sqlite`) and raw image paths are specific to the original server environment and will need to be updated to match your local setup.
