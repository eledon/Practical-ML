
# 💼 Real vs Fake Job Postings Classification

Classifying job postings as real or fraudulent using NLP techniques and machine learning models including **Logistic Regression**, **SVM**, and **XGBoost**.

<img src="pexels-ron-lach-9832718.jpg" width="500" height="300"/>

![Python](https://img.shields.io/badge/Python-TextProcessing-blue?logo=python)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Model](https://img.shields.io/badge/Model-Logistic%20Regression%20%7C%20SVM%20%7C%20XGBoost-yellowgreen)
![Data](https://img.shields.io/badge/Data-Kaggle-orange)

---

## 📘 Table of Contents
- [Overview](#-overview)
- [Technologies](#-technologies)
- [Research Question](#-research-question)
- [Dataset](#-dataset)
- [Exploratory Data Analysis](#-exploratory-data-analysis)
- [Text Preprocessing](#-text-preprocessing)
- [Modeling](#-modeling)
- [Model Evaluation](#-model-evaluation)
- [Explainability](#-explainability)
- [Conclusion](#-conclusion)

---

## 🧭 Overview

This project investigates the classification of job postings into **real vs. fake** categories using machine learning and natural language processing (NLP). The goal is to help platforms and users identify fraudulent job offers by leveraging structured and unstructured data from job listings.

---

## 🧪 Technologies

- **Language:** Python  
- **Libraries:** `pandas`, `numpy`, `scikit-learn`, `xgboost`, `matplotlib`, `seaborn`, `wordcloud`, `spacy`, `shap`  
- **Vectorization:** TF-IDF (unigrams and bigrams)  
- **Explainability:** SHAP for XGBoost and LinearSVC models

---

## ❓ Research Question

> Can we reliably identify fake job postings based on the job description and requirements using NLP features and machine learning classifiers?

---

## 📊 Dataset

- **Source:** [Kaggle - Fake Job Postings Dataset](https://www.kaggle.com/datasets/shivamb/real-or-fake-fake-jobposting-prediction)
- **Size:** 17,880 job postings
- **Label:** `fraudulent` (0 = Real, 1 = Fake)
- **Key Features Used:** `description`, `requirements`, `telecommuting`, `has_company_logo`, `has_questions`, `employment_type`, `industry`

---

## 🔍 Exploratory Data Analysis

- **Distribution:** Only 4.8% of postings are fraudulent (highly imbalanced).
- **Insights:**
  - Fake postings often have shorter descriptions and requirements.
  - Industry and employment type distribution varies by class.
  - Common words differ substantially (visualized via WordCloud).

---

## 🧹 Text Preprocessing

- **Steps:**
  - HTML unescaping, punctuation removal
  - Custom stopword handling (`full`, `part`, `no`, `any` preserved)
  - Lemmatization using spaCy
  - Word count features for `description` and `requirements`
  - TF-IDF vectorization with 1- and 2-grams (top 5,000 features)

---

## ⚙️ Modeling

Three models were trained and evaluated on the TF-IDF features:

### 🔹 Logistic Regression
- Hyperparameter tuned (`C` regularization)
- Accuracy ≈ 98%, F1-score for fake ≈ 0.77

### 🔹 Support Vector Machine (SVM)
- LinearSVC with `max_iter=5000`
- Accuracy ≈ 98%, F1-score for fake ≈ 0.74

### 🔹 XGBoost (tuned)
- Best AP score with parameters:  
  `n_estimators=300`, `max_depth=6`, `learning_rate=0.1`, `subsample=0.8`
- Accuracy ≈ 98%, F1-score for fake ≈ 0.71

---

## 📈 Model Evaluation

| Metric       | Logistic Regression | SVM (LinearSVC) | XGBoost |
|--------------|---------------------|------------------|---------|
| Accuracy     | 98%                 | 98%              | 98%     |
| Fake Precision | 98%               | 98%              | 100%    |
| Fake Recall  | 64%                 | 59%              | 55%     |
| Fake F1-score| 0.77                | 0.74             | 0.71    |
| Avg. Precision (Test) | 0.85       | —                | 0.85    |

---

## 🧠 Explainability

SHAP analysis was used to interpret predictions:

- **Logistic Regression & SVM:**  
  Used `shap.LinearExplainer` with dense TF-IDF input
- **XGBoost:**  
  Used `shap.TreeExplainer` to generate global feature importance and local explanations

> Common SHAP features: `ability`, `require`, `team`, `job`, `responsibility`, `detail`, `hiring`, `interview`

---

## ✅ Conclusion

✅ All three models deliver **high overall accuracy**, but **recall for fake postings remains challenging** due to class imbalance.

✅ The best-performing model in terms of interpretability and precision-recall tradeoff is **Logistic Regression**.

✅ Word count features and TF-IDF were highly effective for this task, and SHAP helped to uncover influential words in classification.

---

📄 For full notebook and SHAP visualizations, see the notebook: [`Real_Fake_Job_Postings_update.ipynb`](Real_Fake_Job_Postings_update.ipynb)
