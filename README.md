# TCGA miRNA Classifier: Distinguishing KIRC from KIRP Using Random Forest

This notebook presents an analysis of microRNA (miRNA) expression profiles from The Cancer Genome Atlas (TCGA) to distinguish between two major renal cell carcinoma subtypes:  
- Kidney Renal Clear Cell Carcinoma (KIRC)  
- Kidney Renal Papillary Cell Carcinoma (KIRP)

We perform differential expression analysis using **DESeq2** and develop a **Random Forest** model to classify tumor samples based on their miRNA expression patterns.

---

## Step 1: Load Required Packages

The analysis uses the following packages:

- `TCGAbiolinks` – download and query TCGA data  
- `SummarizedExperiment` – handle TCGA data structures  
- `DESeq2` – differential expression analysis  
- `edgeR` – differential expression analysis (alternative methods)  
- `dplyr`, `tidyr`, `stringr` – data wrangling and manipulation  
- `randomForest` – machine learning classifier  
- `pROC` – ROC curve analysis and AUC calculation  

---

## Step 2: Download and Prepare Data

- Query and download miRNA expression quantification data from TCGA for KIRC and KIRP.  
- Extract read counts, align common miRNAs, and merge into a unified expression matrix.  
- Generate metadata for each sample indicating its subtype.

---

## Step 3: Differential Expression Analysis

- Perform differential expression using **DESeq2**.  
- Filter results by adjusted p-value (`padj < 0.05`) and sort by significance.  
- Optional: Use **edgeR** for alternative differential expression analyses.

---

## Step 4: Model Training

- Log2-transform miRNA counts to normalize expression data.  
- Split dataset into training (70%) and testing (30%) sets.  
- Train a **Random Forest** classifier to predict tumor subtype (KIRC vs KIRP).

---

## Step 5: Model Evaluation

- Evaluate performance using **ROC curves** with the `pROC` package.  
- Compute AUC to quantify classification accuracy.

---

## Step 6: Save Trained Model

The trained Random Forest model is saved for future predictions:

```r
save(rf_model, file = "rf_kidney_model.RData")
