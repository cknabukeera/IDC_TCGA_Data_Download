# IDC_TCGA_Data_Download
Entails effective ways of retrieving data more accurately and quicker while setting the desired filters or selection criteria
This forms part of my MSc. thesis project titled "Characterizing the Antigenicity of _MAGEA12_ in Invasive Ductal Carcinoma Breast Cancer Subtypes"
The ReadMe file to this project is available elsewhere yet to link it here, For this part I required data corresponding to Invasive Ductal Carcinoma, a breast cancer form in which the cancer has spread from its initial origin(the milk secreting ducts) and then to the rest of breast, and body.
TCGA provides open access data, that can downloaded and retrieved in someways, here I demonstrate how to download/retrieve data from TCGA (https://www.cancer.gov/ccg/research/genome-sequencing/tcga) using TCGAbiolinks package (Colaprico et al., 2016)

Required packages;
TCGAbiolinks(Colaprico et al., 2016), This package has various functions
Here is a breakdown of how i used particular functions within the TCGAbiolinks to download the data
TCGAbiolinks facilitates download of open access data from GDC, data pre-processing while providing a means to perform different analysis such as differential expression, network inference and overall survival analysis, and allows visualization of the obtained results and PAM50 classification. 

TCGAbiolinks constitutes 3 main functions: GDCquery which searches the data based on the built query and filters, then returns the results categorized based on the selected features., GDCdownload which downloads the query and stores the data in a directory and GDCprepare which transforms the downloaded data into a data frame and object subtype information such as the clinical and metadata as defined in TCGA using a summarized experiment function. Summarized Experiment (v1.24.0) for accessing the summarized transformed data frame was used. 
Data Feature selection and Download
Using the GDCquery, A query was built using filters;  project: TCGA-BRCA, data.category: Transcriptome Profiling, data.type: Gene Expression Quantification, experimental.strategy: RNA-Seq, workflow.type: STAR – Counts, data.format : TSV, and access: open and a list of sample barcodes for the data cohort manifest file.  A manifest file from TCGA was downloaded from the cohort built based on the filters above specifying Invasive Ductal carcinoma (infiltrating Ductal carcinoma) as the disease type.  

Retrieving counts data and Clinical Data
Using GDCprepare with the summarized experiment function, count data from the downloaded files and the corresponding genes, meta and clinical data were obtained. Additionally from the raw counts, TPM (transcripts per million) and FKPM (fragments per kilobase million) counts for unstranded contained in the summarized experiment, raw counts data were selected  using the assay function for the downstream analysis. Using GDCquery_clinic from the TCGAbiolinks package, clinical data was downloaded and then filtered using the sample ids of the study cohort to isolate their pertaining clinical data. This clinical data entailed information such as age, race, sex, ethnicity, pathological stages, tumor stages and tissue sources, sample ids and more.  

