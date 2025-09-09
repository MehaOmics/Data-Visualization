## Data-Visualization
This folder contains R scripts for visualizing omics datasets. The scripts cover commonly used plots for differential expression analysis and downstream data exploration, including:
- PCA Plot
- Volcano Plot
- Heatmaps
- UpSet Plots
- Annotated Heatmaps
The plots are generated using ggplot2, ComplexHeatmap, and other widely-used R visualization packages.

## Input
1. For PCA plot:
2. | Plot    | Required Object                  | Columns/Info Needed                             |
| ------- | -------------------------------- | ----------------------------------------------- |
| PCA     | `dds`                            | `colData` with `condition` or grouping variable |
| Volcano | `resLFC_df`                      | `log2FoldChange`, `padj`, `transcript_id`       |
| Heatmap | `normalized_counts`, `sig_genes` | Normalized count matrix and vector of gene IDs  |

