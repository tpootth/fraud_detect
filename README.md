# Credit Card Fraud Detection with PySpark

Big Data project: detecting fraudulent credit card transactions in 24.4M rows of the
IBM TabFormer synthetic dataset using Spark ML on Google Cloud.

**Presentation:** https://tpootth.github.io/fraud_detect/

## Results (test set, fraud class, threshold 0.56)

| Precision | Recall | F1 |
|---|---|---|
| 64.2% | 47.3% | 54.5% |

Random Forest (120 trees, depth 16) on 84 features — including leakage-safe behavioral
window features per user and per card — trained on a 40% non-fraud undersample with
sqrt class weights. Validation and test keep the real 0.12% fraud rate.

## Repository layout

```
docs/                     GitHub Pages site (deployed by .github/workflows/pages.yml)
  index.html              presentation
  reports/                exported notebooks (EDA, model training, interpretation)
notebooks/
  feature_engineering.ipynb      user / card / transaction feature tables (Spark windows)
  fraud_model_traning_V2.ipynb   final Random Forest training on the GCP cluster
  rada.ipynb                     end-to-end local workflow and baseline experiments
requirements.txt
```

## Data

Download `credit_card_transactions-ibm_v2.csv`, `sd254_cards.csv` and `sd254_users.csv` from
[Kaggle: ealtman2019/credit-card-transactions](https://www.kaggle.com/datasets/ealtman2019/credit-card-transactions)
into `data/raw/`. Raw data is not committed (2.35 GB).
