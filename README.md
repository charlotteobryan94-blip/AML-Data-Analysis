# AML-Data-Analysis
Practicing Python and Pandas fundamentals using public leukemia datasets for graduate school preparation
## Skills Practiced
- **Pandas DataFrames:** Creating structured tables from raw biological dictionaries.
- **Data Import:** Reading `.csv` files into Python data tracking structures.
- **Column Selection:** Isolating individual clinical variables (e.g., survival days).
- **Row Filtering:** Querying patient subsets based on numeric thresholds and clinical criteria.
- 
# PhD Bioinformatics & Clinical Data Portfolio

This repository documents my independent computational biology training as I prepare for a Ph.D. track in Cancer Biology, Genetics, and Immunology. It tracks my fluency in building data pipelines, handling high-throughput biological screens, and auditing clinical data frames using Python and Pandas.

---

## 🔬 Project 1: Cancer Biology (Tumor Heterogeneity & Mutation Tracking)

### 1. Biological Problem
Tumor architectures are highly heterogeneous. To model patient prognosis, researchers use Variant Allele Frequency (VAF) to monitor clone size and identify dangerous mutations dominating a biopsy. 

### 2. Core Bioinformatics Architecture
* Engineered a simulated 200-patient pipeline imitating live NIH Genomic Data Commons structures.
* Bypassed network connection blocks using `io.StringIO` to execute text matrix streams directly in local temporary memory.
* Built a multi-constraint boolean filter to extract high-risk patient profiles meeting simultaneous parameters (`Clinical_Significance == 'Pathogenic'` & `VAF_Percentage > 30.0`).
* Configured automated file parsing to output a clean, downstream-ready clinical spreadsheet (`high_risk_tumor_clones.csv`).

### 3. Key Concepts Learned
* **In-Memory File Streams**: Converting plain text to data buffers using the `io` toolkit.
* **Data Slicing**: Dropping noise and subclone data using vector bracket filtering.
* **Data Engineering Uniformity**: Padding indexes (`:03d`) and cleaning structural metrics (`index=False`) to make raw files production-grade.


---

## 🧬 Project 2: Genetics (CRISPR-Cas9 Gene Editing Screening Framework)

### 1. Biological Problem & Experimental Context
When attempting to treat genetic diseases or model oncology mutations via CRISPR-Cas9, scientists must rigorously audit their engineering benchmarks across distinct tissue types. This project screens the editing outcomes of **5 globally recognized biological cell-line models** targeted at key disease loci:
* **HEK293-T1 (Human Embryonic Kidney)**: The universal cellular workhorse used for baseline mechanical verification due to its high transfection capability.
* **HeLa-KO4 (Cervical Adenocarcinoma)**: The historic, immortal cancer model utilized to analyze the disruption of checkpoint pathways (`PDCD1`).
* **iPSC-Stem2 (induced Pluripotent Stem Cells)**: Reprogrammed master lineages used to evaluate core stemness preservation markers (`OCT4`).
* **Jurkat-T3 (T-Lymphocyte Leukemia)**: The absolute gold standard model for human immunology and synthetic CAR-T cell editing trials (`CTLA4`).
* **MCF7-C1 (Mammary Ductal Carcinoma)**: The premier model for analyzing hormone receptors and core tumor-suppressor integrity (`TP53`).

To deem a trial successful for downstream application, researchers must verify two parameters:
1. **Indel Efficiency (%)**: The definitive structural metric tracking the percentage of cells that successfully received an Insertion or Deletion mutation at the Cas9 double-strand break site.
2. **GC Content (%)**: The percentage of Guanine and Cytosine bases within the target site sequence. Skewed GC percentages cause hyper-stable or unstable target binding, sparking dangerous off-target mutations across the genome.

### 2. Core Bioinformatics Architecture
* **Tabular Matrix Instantiation**: Abandoned unstructured text streams to design a fully typed Python **Dictionary** framework mapped instantly into a structural Pandas DataFrame spreadsheet.
* **Custom Row Vectorization Algorithm**: Engineered an independent algorithmic function (`calculate_gc_percentage`) that dynamically reads evolving alphanumeric string indices, computes text characters via `.count()`, and scales string lengths via the vector `len()` tool.
* **Vectorized Data Mapping (`.apply`)**: Implemented high-performance `.apply()` mapping to pass the custom GC algorithm over millions of genomic data matrices simultaneously in memory, eliminating slow and computationally expensive looping structures.
* **Strict Quality-Control Sieve**: Implemented single-bracket Boolean extraction to evaluate the cohort and automatically isolate true high-efficiency lineages crossing a strict **>70% Indel threshold**, successfully catching stubborn lab failures (such as the notoriously difficult-to-transfect Jurkat T-cells).
* **Downstream Production Export**: Configured an automated output pipeline to generate a clean, standalone laboratory file (`successful_crispr_bench.csv`) with internal system indexes fully stripped (`index=False`).

### 3. Key Concepts Mastered
* **Algorithmic Vectorization**: Utilizing `.apply()` to broadcast complex user-defined logic uniformly across database structures.
* **String Parsing in Bioinformatics**: Interrogating and parsing raw nucleotide sequences directly into active data dimensions.
* **Cellular Transfection Disparities**: Understanding how realistic laboratory thresholds differ naturally between resilient models (HEK293) and resistant lines (Jurkat).
