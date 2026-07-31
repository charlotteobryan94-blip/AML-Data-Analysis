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
---

## 🔬 Project 3: Immunology (Synthetic CAR-T Cell Therapy Proliferation Pipeline)

### 1. The Core Biology & Immunological Framework
In modern immuno-oncology, Chimeric Antigen Receptor (CAR) T-cell therapy represents a revolutionary "living drug." To understand this data pipeline, we must dissect the real-world biology of the human immune system:
* **The Patient's Native Army**: T-cells are the primary soldier cells of the adaptive immune system. In a cancer patient, these native cells fail to recognize tumor cells because cancer disguises itself. 
* **The Synthetic Radar (CAR)**: In a specialized facility, healthy T-cells are extracted from the patient's blood. Scientists use genetic engineering (often via a harmless virus vector) to insert a brand-new gene. This gene encodes a synthetic radar receptor called a Chimeric Antigen Receptor (CAR). This radar specifically binds to tumor markers (like CD19 on leukemia cells), allowing the engineered T-cells to track and destroy cancer.
* **The Cellular Phenotypes (CD4 vs. CD8)**: Our data tracks two completely distinct lineages of T-cells that must work in tandem:
  1. **CD8+ Cytotoxic T-Cells (The Killers)**: These are the heavy artillery soldiers. They physically bind to target cancer cells and inject toxic proteins (perforin and granzymes) to blow up the tumor cell from the inside.
  2. **CD4+ Helper T-Cells (The Generals)**: These cells do not kill cancer directly. Instead, they act as the coordination commanders. They release chemical signaling proteins called cytokines to stimulate, support, and keep the CD8 killers alive and fighting.
* **The Bioreactor Imbalance**: Once engineered, these healthy soldier cells are placed into a nutrient-rich, temperature-controlled glass jar called a bioreactor to multiply. However, inside this synthetic broth, **CD4 helper generals multiply significantly faster than CD8 killer soldiers**. Over a 10-day cycle, the generals can completely overrun the army, leaving very few actual killer soldiers behind.

### 2. Clinical Parameters & Quality Control Constraints
As a cellular engineer, harvesting the culture at an incorrect time can lead to catastrophic medical outcomes:
* **The Dosage Parameter (`Total_Count_M_mL`)**: The culture must grow until it crosses a high density threshold (>25 million cells/mL) to ensure a potent enough cell dose to clear a massive tumor burden. Harvesting too early (Days 1–6) results in an ineffective, weak treatment.
* **The Phenotypic Safety Parameter (`CD4_CD8_Ratio`)**: The culture must be harvested *before* the CD4 general-to-CD8 killer ratio swings past a critical boundary (>2.0). If a hyper-skewed helper culture (like Day 10's ratio of 2.5) is infused, the massive flood of helper cytokines triggers a systemic, lethal inflammatory response in the patient called a **Cytokine Storm**, while lacking the raw killer cells needed to wipe out the cancer.

### 3. Core Bioinformatics Architecture
* **Multi-Line Structural String Processing**: Implemented pythonic triple-quote strings (`"""`) to accurately map a 10-day vertical bioreactor telemetry stream entirely within in-memory space.
* **Vectorized Column-on-Column Interaction**: Utilized high-speed Pandas vector architecture to execute direct mathematical division across entire data arrays simultaneously (`CD4_Percentage / CD8_Percentage`), avoiding clunky, non-scalable looping commands.
* **Dual-Constraint Boolean Matrix Slicing**: Engineered an advanced diagnostic quality control sieve utilizing the bitwise AND operator (`&`). The filter automatically scans thousands of data intersections to isolate records satisfying clinical potency and physiological safety thresholds concurrently.
* **Dynamic Phenotype Verification Filtering**: The logical sieve automatically recognized and rejected early cultivation records (Days 1–6) for insufficient target dosage, while successfully catching and purging late-stage records (Day 10) for triggering phenotypic safety boundary violations.
* **Clean Stream Production Output**: Programmed a seamless `.to_csv()` file builder with structural row counters fully stripped (`index=False`) to export a validated, downstream-ready manufacturing spreadsheet (`approved_cart_harvest_days.csv`).

### 4. Key Concepts Mastered
* **Vectorized Mathematical Division**: Executing efficient mathematical transformations between separate tabular dimensions instantly.
* **Dual-Constraint Slicing Logic (`&`)**: Restraining structural subsets using multi-layered biological parameters simultaneously.
* **Immunological Manufacturing Dynamics**: Visualizing the proliferation imbalance between helper lymphocytes and cytotoxic effector populations inside a clinical bioreactor.

## 🧬 Project 4: Stem Cell Biology (Turning Stem Cells into Heart Cells)

### 1. The Science (The Lab Story)
Induced Pluripotent Stem Cells (iPSCs) are basically "blank canvas" master cells that have the power to turn into any cell type in the human body. In this project, I modeled a lab trial where we fed these blank cells 4 different chemical growth recipes to turn them into living, beating heart muscle cells. 

To test if our recipes actually worked, we used a cell counter to measure a master heart protein marker called **`MYH6`**. If a cell shows high levels of `MYH6`, it means it successfully transformed into a real heart cell. In clinical cell manufacturing, regulatory bodies like the FDA require a success rate of **greater than 80%** before the cells can ever be injected into a patient.

### 2. How the Code Works (Step-by-Step)
* **Built the Clipboard from Scratch**: Instead of loading an existing file, I used `pd.DataFrame()` to open up a completely blank spreadsheet page in Python's memory.
* **Added Data Columns**: Created text and number columns line-by-line using bracket assignments (`df_stem['Column_Name'] = [...]`) to log our growth recipes and raw lab percentages.
* **Mastered the Filter Stencil Engine**: Learned the real mechanics of how Python filters tables. The inside code (`df_stem['MYH6_Expression_Pct'] > 80.0`) creates a hidden list of True/False values for every row. The outer brackets act like a physical hole-punch stencil, stamping out the "False" failures and letting only the high-efficiency rows pass through.
* **Isolated the Certified Recipes**: Used the stencil filter to automatically sweep away the failing protocols (Recipes A and C) and isolate the clean, clinical-grade recipes (Recipes B and D) into a new table.

### 3. Core Takeaways
* **The Index Numbers**: Figured out that the 0, 1, 2, 3 row numbers on the left are called the Index. They act as automatic permanent addresses for every row, and Python always starts counting them at 0 instead of 1.
* **Boolean Slicing**: Truly grasped why we use double brackets and variable masks to filter data rows instead of just copying commands.
* **Translating Lab Rules to Code**: Learned how to take standard FDA lab benchmarks and turn them into simple logic filters to isolate safe, clinical-grade tissue batches.
""")

