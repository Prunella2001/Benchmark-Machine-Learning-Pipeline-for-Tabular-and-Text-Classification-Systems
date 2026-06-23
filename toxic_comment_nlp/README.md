
---

# 🧠 1. TOXIC COMMENT NLP README (COPY THIS)

Save inside:
`toxic_comment_nlp/README.md`

```markdown
# Toxic Comment Classification (NLP Pipeline)

## 📌 Problem Framing

This project focuses on building a binary classification system to detect toxic comments in online platforms.

The objective is to support **content moderation systems** by distinguishing toxic vs non-toxic user-generated content.

A key challenge is balancing:
- Detection of harmful content (recall)
- Avoiding unnecessary censorship (precision)

---

## 📊 Dataset

HuggingFace Jigsaw Toxic Comment Classification dataset.

- Input: `comment_text`
- Target: `toxic` (binary classification)

### Key characteristics:
- Strong class imbalance (~90% non-toxic / 10% toxic)
- Short to medium-length comments
- Some empty or sparse samples

Since the official test set has no labels, a **stratified train-test split** was created for evaluation.

---

## ⚖️ Ethics & Safety

This dataset contains offensive and harmful language.

To ensure responsible use:
- No raw toxic comments are displayed
- Only aggregated statistics and sanitized representations are used
- The system is intended for educational purposes only

---

## 🔬 Methodology

The following pipeline was implemented:

- Text cleaning (URLs, punctuation, empty text removal)
- TF-IDF vectorization
- Dummy classifier (baseline)
- Logistic Regression model
- GridSearchCV for hyperparameter tuning
- Stratified evaluation split

Evaluation focuses on:
- Precision (control false positives)
- Recall (capture toxic content)
- F1-score (balance)

---

## 📈 Results

### Baseline (Dummy Classifier)
- Precision: 0.00
- Recall: 0.00
- F1-score: 0.00

### Logistic Regression (TF-IDF)

- Precision: 0.88
- Recall: 0.70
- F1-score: 0.78

---

## ⚖️ Threshold Analysis

| Threshold | Precision | Recall | F1 |
|----------|----------|--------|----|
| 0.3 | 0.81 | 0.78 | 0.79 |
| 0.5 | 0.88 | 0.70 | 0.78 |
| 0.7 | 0.94 | 0.62 | 0.75 |

### Insight:
Lower thresholds improve recall, while higher thresholds improve precision — highlighting the trade-off in moderation systems.

---

## 🧠 Interpretability

### Toxic indicators:
ass, bitch, asshole, stupid, bullshit, idiot, shit, fuck

### Non-toxic indicators:
thank, sorry, appreciate, cheers, agree, thanks

---

## 📌 Conclusion

The Logistic Regression model significantly improves over the baseline and demonstrates strong performance for toxic comment detection.

Key insights:
- TF-IDF + linear models are strong baselines for NLP classification
- Class imbalance strongly impacts evaluation strategy
- Threshold tuning is essential in real-world moderation systems