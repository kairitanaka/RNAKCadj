Keratinocyte Adjustment Using RNA-Seq in Melanoma Samples
This project addresses keratinocyte (KC) contamination in melanoma bulk RNA-seq data. Keratinocytes, abundant in skin tissue, often dominate expression signals and obscure tumor-intrinsic biology. We implemented and compared several approaches to adjust for KC effects.
Cohort

97 melanoma samples across stages: Nevus, Intermediate, MIS, RGP, and VGP
RNA-seq counts integrated with QuPath imaging features (tumor, stroma, keratinocytes, immune cells)
Metadata included age, sex, solar elastosis, and chronic sun damage

Analysis Workflow
1. Preprocessing

Import raw counts
Remove outlier samples (e.g., ME-63, JJS-19)
Normalize with TMM
Filter low-expression genes
Build linear mixed models with covariates

2. Baseline Differential Expression

Model:

r  ~ tissue + sex + age + (1 | patient_id)

Fit mixed models per gene (voom + dream)
Identify DEGs (FDR < 0.05, |logFC| > 2)
Pathway analysis with Hallmark and Reactome gene sets

3. Problem Identification

KC genes (e.g., KRT1, KRT14, FLG) strongly influenced DEGs
Especially evident in RGP samples
Risk of false positives due to skin contamination

Keratinocyte Adjustment Approaches
Canonical KC Signature Adjustment

Defined canonical KC genes:
KRT1, KRT2, KRT5, KRT10, KRT14, IVL, FLG, LOR, TGM3, SPRR2A, DSC1, DSG1, PI3, DMKN
Computed GSVA enrichment score per sample
Added as covariate:

r  ~ tissue + sex + age + gsva_canonical_kc + (1 | patient_id)

Removed variance explained by canonical KC expression

xCell KC Adjustment

Used xCell-derived KC score as covariate
Captures a broader keratinocyte program
Added as covariate:

r  ~ tissue + sex + age + xcell_kc + (1 | patient_id)
Alternative KC Adjustment

Identified all genes correlated with KC scores (canonical and xCell)
Removed these genes from DEG analysis
Applied across RGP and VGP signatures to isolate tumor-specific expression

Signature Comparisons

Evaluated canonical vs xCell vs ssGSEA vs GSVA signatures
Compared DEG results, PCA clustering, QuPath imaging correlations, and pathway associations
Determined whether adjustments were too strong (removing true biology) or too weak (retaining KC bias)

ssGSEA vs GSVA for KC Scoring

ssGSEA: ranks genes within a sample; sensitive to outliers; driven by dominant genes
GSVA: compares gene distributions; robust to outliers; captures collective signal
Both used for KC scoring to provide complementary perspectives

Immune Deconvolution
To evaluate immune infiltration alongside KC effects, we applied multiple methods:

CIBERSORT
xCell
Custom immune signatures
Literature-based signatures (e.g., Danaher)

Results were benchmarked against QuPath immune features and KC-adjusted expression signatures.
