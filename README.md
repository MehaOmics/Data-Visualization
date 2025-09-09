## Data-Visualization

This folder contains R scripts for visualizing omics datasets. The scripts cover commonly used plots for differential expression analysis and downstream data exploration, including:
- PCA Plot: Visualizes sample clustering based on variance-stabilized counts to assess overall sample similarity
- Volcano Plot: Highlights significantly up- or down-regulated genes based on log2 fold change and adjusted p-values
- Heatmaps: Displays gene expression patterns for differentially expressed genes (DEGs) among different treatments
- UpSet Plots: Visualizes overlaps between multiple DEG sets or gene groups
- Annotated Heatmaps: Adds metadata or pathway information to heatmaps to better interpret DEGs or metabolites in the context of pathways

The plots are generated using ggplot2, ComplexHeatmap, and other widely-used R visualization packages
