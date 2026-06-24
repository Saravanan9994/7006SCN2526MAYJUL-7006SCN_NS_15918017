# 7006SCN — Machine Learning and Big Data Coursework

**Amazon review sentiment classification at scale with PySpark (NLP)**

Repository: `7006SCN2526MAYJUL/7006SCN_<Initials>_<SID>`

## Problem
Binary **sentiment classification** from unstructured review **text**: positive (rating 4–5) vs negative (rating 1–2), neutral (3) dropped. Data: Amazon Reviews 2023 (McAuley Lab), **Cell_Phones_and_Accessories** category (~20M reviews).

## Big Data compliance
| Requirement | Status |
|---|---|
| ≥10 million rows | ✅ ~20M reviews |
| ≥10 columns | ✅ 9 raw fields + engineered features + 20k TF-IDF terms |
| Classification/regression/clustering | ✅ binary classification |
| Entire pipeline in PySpark | ✅ |
| NOT from Kaggle | ✅ McAuley Lab / amazon-reviews-2023.github.io |
| NOT a teaching dataset | ✅ |
| Unstructured data (higher marks) | ✅ free-text NLP |
| Ethical/licensing | ✅ CC BY-SA 4.0; user_id dropped (data minimisation) |

## Notebooks
| File | Week | Content |
|---|---|---|
| `Task1.ipynb` | 1–2 | SparkSession, jsonl.gz ingestion, schema, 5 V's, licensing/ethics |
| `Task2.ipynb` | 2 | Label + text cleaning, feature engineering, NLP `Pipeline` (Tokenizer→StopWords→CountVectorizer→IDF→Assembler→Scaler) |
| `Task3.ipynb` | 3 | 4 classifiers (LogReg, NaiveBayes, LinearSVC, RandomForest) + `CrossValidator` |
| `Task4.ipynb` | 4 | Spark UI, caching/persist, resource config, repartition, class-imbalance weighting |
| `Task5.ipynb` | 5 | Metrics, confusion matrices, ROC/PR, stability, top sentiment-word explainability |
| `Task6.ipynb` | 6 | Tableau exports + 4 dashboards |

## How to run (Google Colab)
1. Open each notebook; run the **bootstrap** cell (installs `pyspark==3.5.1`) and the **Drive mount** cell.
2. Run Task1 first (downloads the category `.jsonl.gz` → Parquet). Later notebooks reuse the saved Parquet/models/vocabulary from Drive.
3. Task3: if free Colab times out, set `TRAIN_FRAC < 1.0` to train on a stratified sample (ingestion/counts still use the full ≥20M for the Big Data requirement).
4. Task4 Spark UI: add a free [ngrok](https://dashboard.ngrok.com) token.

## Tableau
One Tableau Public workbook, four dashboards: Data Quality & Pipeline Monitoring · Model Performance & Feature Importance (top sentiment words) · Business Insights · Scalability & Cost Analysis. Public link goes in the report.

## Licensing & citation
CC BY-SA 4.0. Cite: Hou, Y. et al. (2024) *Bridging Language and Items for Retrieval and Recommendation*, arXiv:2403.03952.

## Version control
≥3 meaningful commits per task, timestamped in the correct weeks; README maintained; branch-per-model encouraged in Task3.
