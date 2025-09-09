library(DESeq2)
library(pheatmap)
library(viridis)
library(dplyr)

# ------------------------------
# Load normalized counts
# ------------------------------
norm_counts <- counts(dds, normalized = TRUE)

# Load BLAST hits
blast_hits <- read.csv("BLAST_Hits_Ids.csv", stringsAsFactors = FALSE)

# Extract transcript IDs of interest
transcripts_of_interest <- blast_hits$transcript_id

# Subset counts to BLAST-annotated transcripts
norm_counts_subset <- norm_counts[rownames(norm_counts) %in% transcripts_of_interest, ]

# Remove zero variance rows
norm_counts_subset <- norm_counts_subset[apply(norm_counts_subset, 1, var) != 0, ]

# ------------------------------
# Compute mean per tissue (average replicates automatically)
# ------------------------------
tissue_map <- sub("[0-9]+$", "", colnames(norm_counts_subset))  # extract tissue names
unique_tissues <- unique(tissue_map)

norm_counts_mean <- sapply(unique_tissues, function(t) {
  rowMeans(norm_counts_subset[, tissue_map == t, drop = FALSE], na.rm = TRUE)
})
rownames(norm_counts_mean) <- rownames(norm_counts_subset)

# ------------------------------
# Keep tissues in natural order
# ------------------------------
norm_counts_mean <- norm_counts_mean[, unique_tissues]

# ------------------------------
# Row-wise Z-score normalization
# ------------------------------
norm_counts_scaled <- t(scale(t(norm_counts_mean)))
norm_counts_scaled[is.na(norm_counts_scaled)] <- 0
norm_counts_scaled[is.infinite(norm_counts_scaled)] <- 0

# ------------------------------
# Plot heatmap
# ------------------------------
palette <- viridis(100)

png("heatmap_with_annotation.png",
    width = 4000, height = 3000, res = 600,
    )

pheatmap(norm_counts_scaled,
         cluster_rows = TRUE,
         color = palette,
         border_color = NA,
         cellwidth = 20,
         cellheight = 10,
         fontsize_row = 6,
         fontsize_col = 6,
         show_rownames = TRUE,
         show_colnames = TRUE,
         name = "Z-score")

dev.off()
