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
