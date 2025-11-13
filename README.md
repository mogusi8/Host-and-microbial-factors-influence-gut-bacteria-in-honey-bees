## Host-and-microbial-factors-influence-gut-bacteria-in-honey-bees
This repository contains all analysis code and R Markdown reports for the study Host and microbial factors influence gut bacteria in honey bees. It covers colonization load (qPCR), host immune gene expression (RT-qPCR), genomic functional profiling (KEGG), phylogenetic signal testing, and AMP-sensitivity assays.

#What each script does & required inputs

01_qPCR_abundance.Rmd — Colonization loads
Purpose: quantify bacterial load and % colonized in mono vs. synthetic community (SC).
Inputs (place under data/): 5_Data_qPCR_CopyNum_all_combined_LOD.csv
Metadata.csv
Outputs: tables of median normalized load and % colonized; per-strain Wilcoxon (Mono vs SC); figures saved to output/figures/ and output/tables/.

02_functional_profiling.Rmd — KEGG modules ↔ colonization
Purpose: test associations between KEGG module completeness and % colonized / abundance.
Inputs (data/functional_profiling/)

03_ModuleCompleteness/all_genomes_module_completeness.tab
config/genomes_metadata.csv, config/genome_sources.csv
qPCR summaries from data/qPCR/plot_qPCR/
Outputs: correlation tables, mixed-model results, PCA and heatmaps in output/functional_profiling/.

03_Phylogenetic_signal.Rmd — Do traits follow the tree?
Purpose: quantify phylogenetic signal (e.g., Blomberg’s K) for colonization traits.
Inputs: data/phylogeny/SpeciesTree_rooted_node_labels_renamed.nexus
qPCR trait tables (e.g., data/qPCR/plot_qPCR/08_Median_abundance_and_FC.csv)
Outputs: signal metrics, pairwise distances, distance–trait plots in output/phylogenetic_distances/.

04_qRT_PCR_analysis.Rmd — Host immune gene expression
Purpose: measure 7 immune-related genes (Apidaecin1, Abaecin, Defensin1/2, Hymenoptaecin, IRP30, Lysozyme) 7 dpi in mono-associated bees; compute ΔCt/ΔΔCt and relative expression vs MD.
Inputs (data/qrtpcr/ + data/metadata/ as referenced inside)
RT-qPCR raw exports
sample metadata (e.g., conditions, strain labels)
Outputs: tidy ΔCt/ΔΔCt tables and expression plots in output/plot_qPCR/.

05_AMP_Sensitivity_analysis_Strains_comparison.Rmd — AMP sensitivity
Purpose: estimate strain sensitivity to host AMPs (Apidaecin1a/b, Abaecin, Defensin1/2, Hymenoptaecin) from in-vitro growth inhibition; compute AUC, growth parameters, LL.4 IC50, ranks.
Inputs (data/amp_sensitivity/)
metadata/plate_map.csv (Well, Strain, AMP, Concentration_uM, Replicate, PlateID)
raw/ plate reader exports (CSV, long or wide)
Outputs: well/summary metrics, IC50 tables and figures in output/amp_sensitivity/.

#Dependencies (major R packages)

tidyverse, here, ggplot2, ggpubr, ggrepel,
growthcurver, drc, pracma, broom, scales,
ComplexHeatmap, circlize, gplots, RColorBrewer,
ape, picante, phylobase.
