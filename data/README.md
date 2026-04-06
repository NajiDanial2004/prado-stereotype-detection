# Data

The raw dataset used in this project comes from the Museo Nacional del Prado's
public digital catalogue (https://www.museodelprado.es/coleccion).

Artwork metadata was retrieved by searching iconographic categories via the
museum's online search tool and exported as Excel files.

The SQLite database (agrupa.sqlite) and raw artwork images are not included
in this repository due to file size constraints.

To reproduce the dataset:
1. Download artwork metadata from the Prado catalogue for your target categories
2. Run notebook 01 to construct the SQLite database and filtered datasets
3. Run notebooks 02-03 to extract visual embeddings (requires a GPU)
4. Run notebooks 04-09 for modeling experiments
