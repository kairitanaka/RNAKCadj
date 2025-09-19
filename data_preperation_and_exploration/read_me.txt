data_preparation_and_exploration_clean

This script requires the following data.

* 'data/May_2025_Analysis/UCSF_RNAseq_2025_June_SampleInfo_Lewis.csv'
* 'data/patient_information_ver2_September_2025.csv'
* 'data/May_2025_Analysis/UCSF_RNAseq.Sample99.raw.csv'
* 'data/Homo_sapiens.gene_info'
* 'data/QuPath_Annotations_Lewis.csv'

and saves the master gene-expression data

* 'data/processed/DGE_final_samples.rda'

that is required for most subsequent scripts.

This script also makes tables for patient and sample numbers.

NOTE: The first chunk needs to be ran manually before knitting.

NOTE: knit from the project directory 'lewis_analysis_scripts_and_data_original'