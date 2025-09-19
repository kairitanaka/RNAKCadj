# Lewis Original Scripts

These Lewis original files are the untouched scripts that were used before edited by Kairi.

## Overview

This folder contains all the scripts for the analysis of the melanoma RNA-seq data. If running from scratch, I recommend running in the following order.

## Analysis Workflow

### DEG analysis comparing tissue types [need to be ran in order]
1. **data_preperation_and_exploration**
2. **tissue_type_degs**

### Comparing signature scores between tissues [these can be ran in any order, script 1. needs to be ran first]
3. **ssgsea_gsva_on_davids_signatures**
4. **ssgsea_gsva_on_additional_signatures** [eg Canonical KC, Danaher, onco MAPK etc, I recommend you add new signatures here]
5. **preperation_analysis_cibersort**
6. **preperation_analysis_xcell**
7. **signatures_correlation**

### DEG analysis comparing tissue types, adjusting for keratinocyte scores [require 4. and 6.]
8. **tissue_type_degs_cononical_kc_adjust** [4. needs to be ran first]
9. **tissue_type_degs_xcell_kc_adjust** [6. needs to be ran first]

### Identify genes associated with keratinocyte signatures [can be any order]
10. **genes_associated_with_xcell_kc** [requires 6] eg ~4,000
11. **genes_associated_with_canonical_kc_gsva** [requires 4]
12. **genes_associated_with_canonical_kc_ssgsea** [requires 4]

### Exploring melanoma signatures
13. **exploring_melanoma_signatures** [requires 1,2, 4, 6, 7, 9-11]

### Bonus analysis [some are still a little messy]
14. **CSD**
15. **mean variance trend and outliers**
16. **Progression-type MIS vs NoMIS**

## Package Versions

```
R version 4.4.1 (2024-06-14 ucrt)
Platform: x86_64-w64-mingw32/x64
Running under: Windows 10 x64 (build 19045)

tidyverse: 2.0.0
tableone: 0.13.2
variancePartition: 1.34.0
msigdbr: 25.1.1
BiocParallel: 1.38.0
fgsea: 1.30.0
pheatmap: 1.0.13
RColorBrewer: 1.1.3
VennDiagram: 1.7.3
grid: 4.4.1
ggpubr: 0.6.1
lme4: 1.1.37
emmeans: 1.11.2
GSVA: 1.52.3
```

## Dependencies

Make sure to install all required packages before running the analysis scripts. The workflow is designed to be run sequentially, with some scripts having specific dependencies on earlier analyses.
