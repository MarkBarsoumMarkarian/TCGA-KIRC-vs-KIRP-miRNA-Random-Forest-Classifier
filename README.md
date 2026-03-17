# TCGA KIRC vs KIRP miRNA Random Forest Classifier

**Kidney cancer subtype discrimination using miRNA expression — Random Forest pipeline in R**

> Clear cell (KIRC) and papillary (KIRP) renal cell carcinoma share clinical overlap but have distinct biology, prognosis, and treatment sensitivity. This pipeline uses TCGA miRNA expression data to build a classifier that separates them — and identifies which miRNAs drive the difference.

---

## What it does

1. Downloads TCGA-KIRC and TCGA-KIRP miRNA expression data via TCGAbiolinks
2. Preprocesses and normalizes counts
3. Runs differential expression analysis (DESeq2 / limma)
4. Trains a Random Forest classifier on top differentially expressed miRNAs
5. Evaluates with ROC-AUC, confusion matrix, and feature importance
6. Reports candidate discriminatory miRNAs

---

## How to run

```r
install.packages(c("randomForest", "pROC", "ggplot2", "dplyr", "caret"))
BiocManager::install(c("TCGAbiolinks", "DESeq2"))

# Then run the notebook:
# classifier.ipynb (Jupyter with R kernel) or source the R scripts
```

Data is downloaded automatically from GDC on first run via TCGAbiolinks.

---

## Results

- Random Forest classifier distinguishing KIRC from KIRP on held-out test set
- Top discriminatory miRNAs by Gini importance
- ROC-AUC evaluation

---

## Stack

R · TCGAbiolinks · DESeq2 · randomForest · caret · pROC · ggplot2

**License:** MIT
