# Heart-Disease-Prediction-Logistic-Regression
# 🫀 Heart Disease Prediction using Logistic Regression

A binary classification project that predicts the presence of heart disease using patient clinical data and a Logistic Regression model.

---

## 📌 Project Overview

| Item | Details |
|------|---------|
| **Algorithm** | Logistic Regression |
| **Dataset** | Heart Disease UCI (`heart.csv`) |
| **Target** | `1` = Heart Disease Present, `0` = No Disease |
| **Language** | Python 3 |
| **Notebook** | `LogisticRegression.ipynb` |

---

## 📁 Repository Structure

```
heart-disease-prediction/
│
├── heart.csv                        # Dataset
├── LogisticRegression.ipynb         # Main notebook
├── README.md                        # Project documentation
└── requirements.txt                 # Dependencies
```

---

## 📊 Dataset

The dataset contains **302 unique patient records** (after removing 723 duplicates from the raw file) with **13 clinical features**.

| Feature | Description |
|---------|-------------|
| `age` | Age of the patient |
| `sex` | Sex (1 = male, 0 = female) |
| `cp` | Chest pain type (0–3) |
| `trestbps` | Resting blood pressure (mm Hg) |
| `chol` | Serum cholesterol (mg/dl) |
| `fbs` | Fasting blood sugar > 120 mg/dl (1 = true) |
| `restecg` | Resting ECG results (0–2) |
| `thalach` | Maximum heart rate achieved |
| `exang` | Exercise-induced angina (1 = yes) |
| `oldpeak` | ST depression induced by exercise |
| `slope` | Slope of peak exercise ST segment |
| `ca` | Number of major vessels (0–3) |
| `thal` | Thalassemia type |
| **`target`** | **1 = Disease, 0 = No Disease** |

---

## ⚙️ Workflow

```
Load Data → Clean (drop duplicates) → EDA → Split → Scale → Train → Evaluate → Cross-Validate
```

1. **Load & Clean** — Drop 723 duplicate rows to prevent inflated metrics
2. **EDA** — Target distribution, age histogram, correlation heatmap
3. **Train/Test Split** — 80/20 with `stratify=y` to preserve class ratios
4. **Feature Scaling** — `StandardScaler` fit on train only (no data leakage)
5. **Model Training** — `LogisticRegression(max_iter=1000)`
6. **Evaluation** — Accuracy, Recall, Classification Report, Confusion Matrix, ROC-AUC
7. **Cross-Validation** — 5-fold CV using a `Pipeline` to prevent leakage across folds
8. **Feature Importance** — Absolute coefficient values

---

## 📈 Results

> High recall for the Disease class (0.85) is the priority — minimizing false negatives in a medical setting is critical.

### Cross-Validation (5-Fold)

| Metric | Score |
|--------|-------|
| Mean CV Accuracy | **82.13%** |
| Std Dev | ± 6.06% |

### Top Features by Importance

| Rank | Feature | Description |
|------|---------|-------------|
| 1 | `cp` | Chest pain type |
| 2 | `sex` | Sex |
| 3 | `oldpeak` | ST depression |
| 4 | `ca` | Number of vessels |
| 5 | `trestbps` | Resting blood pressure |

---

## 🚀 Getting Started

### Prerequisites

```bash
pip install -r requirements.txt
```

**`requirements.txt`**
```
pandas
numpy
scikit-learn
matplotlib
seaborn
jupyter
```

### Run the Notebook

```bash
git clone https://github.com/bhupendra763/heart-disease-prediction.git
cd heart-disease-prediction
jupyter notebook LogisticRegression.ipynb
```

---

## 🔑 Key Design Decisions

- **Duplicates removed** before splitting to prevent test set contamination
- **`stratify=y`** in train/test split ensures balanced class representation
- **`max_iter=1000`** guarantees solver convergence
- **Pipeline used in CV** so the scaler is re-fit on each fold (no leakage)
- **ROC-AUC** included alongside accuracy for a complete evaluation picture

---

## 🛠️ Built With

- [scikit-learn](https://scikit-learn.org/) — ML model and evaluation
- [pandas](https://pandas.pydata.org/) — Data manipulation
- [matplotlib](https://matplotlib.org/) & [seaborn](https://seaborn.pydata.org/) — Visualization

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
