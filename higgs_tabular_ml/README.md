# Higgs Boson Classification (Tabular ML Pipeline)

## 📌 Problem Framing

This project addresses a binary classification problem from high-energy physics, where the goal is to distinguish:

- Signal events (Higgs boson)
- Background noise events

This simulates a real-world scientific detection problem involving high-dimensional structured data.

---

## 📊 Dataset

OpenML Higgs Dataset

- 1,000,000 samples
- 28 numerical features + 1 target variable
- Fully numerical dataset
- No missing values

### Target distribution:
- ~53% signal
- ~47% background

This is a near-balanced classification task.

---

## 🧹 Data Cleaning

- No missing values detected
- ~0.2% duplicate rows removed (simulation artifacts)
- Data assumed to be clean Monte Carlo simulation output

---

## 🔬 Exploratory Data Analysis

Key observations:
- Features are already normalized in scale
- Several variables are highly skewed with outliers
- Some features contain predictive signal only in extreme ranges
- Relationships are non-linear and interaction-driven

### Key insight:
Linear models are insufficient alone; tree-based models are more suitable.

---

## 🧠 Model Selection

### Baseline:
- Logistic Regression / Dummy classifier

### Final model:
- LightGBM (Gradient Boosting Trees)

### Why LightGBM:
- Efficient on large datasets (1M rows)
- Captures non-linear feature interactions
- Scales better than Random Forest

---

## 📈 Results

### Baseline
- ROC-AUC: 0.50
- Accuracy: ~0.50

### LightGBM Model
- ROC-AUC: 0.82
- Accuracy: 0.74

---

## 🧠 Interpretability (SHAP)

Most influential features:
- m_bb
- m_wwbb
- m_wbb
- m_jjj
- jet_1_pt

### Insights:
- Jet energy features strongly influence signal detection
- Some features push predictions toward background classification
- Model captures complex non-linear interactions

---

## 📌 Conclusion

The LightGBM model significantly outperforms the baseline and successfully captures complex patterns in high-dimensional physics data.

Key takeaways:
- Tree-based models are highly effective for structured scientific data
- Feature interactions are critical for prediction performance
- ROC-AUC is more informative than accuracy for this task