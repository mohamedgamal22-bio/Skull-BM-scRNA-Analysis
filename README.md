Single-Cell Profiling of Skull Bone Marrow T Cell Heterogeneity
​Biological Hypothesis and Overview
​The central nervous system was long considered an immunologically privileged site. However, recent discoveries show vascular connections between the skull bone marrow and the dural meninges.
​This project explores whether the skull bone marrow acts as a specialized immune microenvironment for local surveillance, distinct from systemic long bones like the sternum and downstream tissues like the dura.
​Using scRNA-seq, we mapped T cell diversity across these three niches to examine local priming and helper T cell specialization.
​Key Biological Findings
​Skull BM as a Distinct Specialized Niche: High-resolution single-cell clustering revealed conserved and tissue-specific T cell states across Dura (216 cells), Skull BM (1,177 cells), and Sternum BM (857 cells).
​Identification of Follicular Helper T Cells (Tfh): We identified a cluster of Tfh+ cells defined by markers like Bcl6, Cxcr5, Tgfb1, and Gata3. This supports the hypothesis of localized germinal center-like activity near the CNS border.
​Subpopulation Annotation:
​Naive T Cells (Naive1, Naive2): High expression of Sell and Ccr7.
​T Helper and Transitioning Lineages (Th, Transitioning, Activated): Upregulation of Cd44 and Cd69.
​Regulatory T Cells (Cd25lo Treg, Cd25hi Treg): Expression of Foxp3 and Tgfb1.
​Interferon-Stimulated Subsets (ISG+): Enriched for interferon response genes.
​Visualizations
​Comparative Anatomical UMAP Dynamics
​Dura (216 cells): Sparse effector T cell representation.
​Skull BM (1,177 cells): Rich diversity of Tfh+, Tregs, and effector subsets.
​Sternum BM (857 cells): Standard baseline immune repertoire.
​Lineage Expression Matrix
​Naive: Sell, Ccr7
​Treg: Foxp3, Tgfb1
​Tfh: Bcl6, Cxcr5, Tgfb1, Gata3
​Automated Processing Pipeline
​The analysis pipeline is built using Nextflow DSL2 for full reproducibility:
​CREATE_AND_QC: Quality control filtering, mitochondrial percentage calculation, and marker-based cell selection.
​MERGE_SAMPLES: Merging datasets and handling layers.
​NORM_PCA: Normalization and dimensionality reduction via PCA.
​CLUSTERING_UMAP: UMAP generation, cell clustering, and expression plot export.
​How to Run
​Execute the pipeline in WSL or Terminal using Nextflow:
​nextflow run workflows/single.nf --data_dir "./raw_data" --outdir "./results" --cell_selection "CD3E > 0 & CD4 > 0 & CD8A == 0 & ITGAM == 0" -resume
​Repository Structure
​workflows/single.nf: Nextflow pipeline script
​data/raw_data/: Input 10x Genomics HDF5 files (.h5)
​results/: Pipeline outputs including plots and Seurat RDS files
​.gitignore: File exclusions for large data files
