# sc-leiden-umap

Single-cell RNA-seq downstream analysis pipeline using Scanpy. Performs preprocessing, Leiden clustering, UMAP visualization, DEG analysis, and volcano plot generation from an h5ad input file.

## Inputs
- `.h5ad` file (AnnData format) containing raw or preprocessed single-cell RNA-seq data

## Outputs
- `preprocessed.h5ad` — Normalized, HVG-selected, PCA-reduced data
- `clustered.h5ad` — Data with Leiden cluster assignments
- `leiden_clusters.csv` — Cluster assignments per cell
- `processed.h5ad` — Data with UMAP embedding
- `umap_leiden.png` — UMAP plot colored by Leiden clusters
- `deg_analysis.h5ad` — Data with DEG results stored in `.uns`
- `deg_markers.csv` — Top DEG markers per cluster (gene, score, logFC, p-value)
- `deg_dotplot.png` — Dotplot of top marker genes per cluster
- `volcano_plot.png` — Volcano plots per cluster (log2FC vs -log10 adjusted p-value)

## How to Run

```bash
# Build Docker image
docker build -t sc-leiden-umap .

# Run pipeline
docker run --rm \
  -v /path/to/input:/input:ro \
  -v /path/to/output:/output \
  sc-leiden-umap
```

## Configuration (config.yaml)

| Parameter | Default | Description |
|-----------|---------|-------------|
| `run_preprocessing` | `true` | Run normalization, HVG, PCA |
| `n_top_genes` | `2000` | Number of highly variable genes |
| `n_pcs` | `50` | Number of principal components |
| `n_neighbors` | `15` | Neighbors for graph construction |
| `leiden_resolution` | `1.0` | Leiden clustering resolution |
| `umap_min_dist` | `0.5` | UMAP minimum distance |
| `deg_groupby` | `leiden` | Grouping column for DEG |
| `deg_method` | `wilcoxon` | DEG statistical test method |
| `deg_n_genes` | `25` | Top DEGs per cluster |
| `volcano_logfc_threshold` | `1.0` | Log2FC threshold for volcano plot |
| `volcano_pval_threshold` | `0.05` | Adjusted p-value threshold |
| `volcano_top_n_label` | `5` | Top genes to label on volcano |