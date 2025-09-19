
This folder contains all the scripts for the analysis of the melanoma RNA-seq data.

If running from scratch, I recommend running in the following order.

DEG analysis comparing tissue types [need to be ran in order]
1. data_preperation_and_exploration
2. tissue_type_degs 

Comparing signature scores between tissues [these can be ran in any order, script 1. needs to be ran first]
3. ssgsea_gsva_on_davids_signatures
4. ssgsea_gsva_on_additional_signatures [eg Canonical KC, Danaher, onco MAPK etc, I recommend you add new signatures here]
5. preperation_analysis_cibersort
6. preperation_analysis_xcell
7. signatures_correlation

DEG analysis comparing tissue types, adjusting for keratinocyte scores [require 4. and 6.]
8. tissue_type_degs_cononical_kc_adjust [4. needs to be ran first]
9. tissue_type_degs_xcell_kc_adjust  [6. needs to be ran first]

Identify genes assocaited with keratinocyte signatures. [can be any order]
10. genes_associated_with_xcell_kc [requires 6] eg ~4,000
11. genes_associated_with_canonical_kc_gsva [requires 4]
12. genes_associated_with_canonical_kc_ssgsea [requires 4]

Exploring melanoma signatures
13. exploring_melanoma_signatures [requires 1,2, 4, 6, 7, 9-11]

Bonus analysis [some are still a little messy]
14. CSD 
15. mean variance trend and outliers 
16. Progression-type MIS vs NoMIS
 

Package versions.

R version 4.4.1 (2024-06-14 ucrt)
Platform: x86_64-w64-mingw32/x64
Running under: Windows 10 x64 (build 19045)

> packageVersion("tidyverse")
[1] ‘2.0.0’

> packageVersion("tableone")
[1] ‘0.13.2’

> packageVersion("variancePartition")
[1] ‘1.34.0’

> packageVersion("msigdbr")
[1] ‘25.1.1’

> packageVersion("BiocParallel")
[1] ‘1.38.0’

> packageVersion("fgsea")
[1] ‘1.30.0’

> packageVersion("pheatmap")
[1] ‘1.0.13’

> packageVersion("RColorBrewer")
[1] ‘1.1.3’

> packageVersion("VennDiagram")
[1] ‘1.7.3’

> packageVersion("grid")
[1] ‘4.4.1’

> packageVersion("ggpubr")
[1] ‘0.6.1’

> packageVersion("lme4")
[1] ‘1.1.37’

> packageVersion("emmeans")
[1] ‘1.11.2’

> packageVersion("GSVA")
[1] ‘1.52.3’



