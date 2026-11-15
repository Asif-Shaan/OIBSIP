# 🌸 Iris Flower Species Classification
### *An End-to-End Machine Learning Pipeline*
> **Oasis Infobyte Data Science Internship — Task 3**

---

[![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python)](https://python.org)
[![Scikit-Learn](https://img.shields.io/badge/scikit--learn-1.5.2-orange?logo=scikit-learn)](https://scikit-learn.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)](https://jupyter.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green)](LICENSE)

---

## 🎯 Objective

Build a **production-ready machine learning classification pipeline** to identify the species of an Iris flower — *Iris setosa*, *Iris versicolor*, or *Iris virginica* — from four morphological measurements (sepal length, sepal width, petal length, petal width), using three distinct ML classifiers and a rigorous evaluation framework.

---

## 🧰 Tech Stack

| Tool / Library | Version | Role |
|----------------|---------|------|
| Python | 3.11.5 | Core language |
| pandas | 2.2.3 | Data manipulation & EDA |
| NumPy | 1.26.4 | Numerical operations |
| scikit-learn | 1.5.2 | ML models, preprocessing, evaluation |
| Matplotlib | 3.9.2 | Visualisation backend |
| Seaborn | 0.13.2 | Statistical visualisations |
| Jupyter | 1.1.1 | Interactive notebook environment |

---

## 📦 Dataset

> **No external download required!**

The Iris dataset is loaded directly from `sklearn.datasets.load_iris()` — it ships with scikit-learn out of the box.

**Dataset Profile:**

| Property | Value |
|----------|-------|
| Samples | 150 |
| Features | 4 (sepal length, sepal width, petal length, petal width) |
| Classes | 3 (Setosa, Versicolor, Virginica) |
| Class balance | Perfectly balanced (50 samples per class) |
| Missing values | None |

---

## 🗂️ Project Structure

```
OIBSIP_Iris_Project/
├── .venv/                          # Python virtual environment
├── visuals/                        # All generated plots
│   ├── pairplot.png                # Pairwise feature distributions
│   ├── boxplots.png                # Per-feature box plots by species
│   ├── confusion_matrix_lr.png     # Logistic Regression confusion matrix
│   ├── confusion_matrix_knn.png    # KNN confusion matrix
│   ├── confusion_matrix_rf.png     # Random Forest confusion matrix
│   ├── confusion_matrices_all.png  # Side-by-side comparison
│   └── model_comparison.png        # Accuracy bar chart
├── iris_classification.ipynb       # 📓 Main Jupyter Notebook
├── requirements.txt                # Pinned dependency list
└── README.md                       # This file
```

---

## 🔄 Workflow

### 1. 📊 Exploratory Data Analysis (EDA)

- Inspect data types, shape, and confirm **zero null values**
- Analyse class distribution (confirms balanced 50/50/50 split)
- Compute descriptive statistics (mean, std, quartiles) per feature
- **Pairplot:** Visualise all pairwise feature relationships coloured by species — reveals that petal dimensions create near-perfect cluster separation
- **Box plots:** Show per-feature distributions per class — highlights that Setosa is a statistical outlier for petal dimensions

### 2. 🎯 Feature Selection Discussion

Analysis of the pairplot reveals:

- **Petal Length** and **Petal Width** are the most discriminative features — Setosa is completely linearly separable in this space
- **Sepal Width** is the weakest discriminator, with overlapping distributions across all three classes
- Versicolor vs. Virginica requires all 4 features for optimal separation

### 3. ⚙️ Preprocessing

- **80/20 Train-Test Split** with `stratify=y` to preserve class ratios
- **StandardScaler** applied (fit on train only → transform applied to both) to prevent data leakage and ensure distance-based models behave correctly

### 4. 🤖 Model Training

Three classifiers from different algorithmic families:

| Model | Key Hyperparameters |
|-------|---------------------|
| Logistic Regression | `max_iter=200`, `C=1.0`, `solver=lbfgs` |
| K-Nearest Neighbours | `n_neighbors=5`, `metric=euclidean` |
| Random Forest | `n_estimators=100`, `max_features=sqrt` |

### 5. 📈 Evaluation

Each model is assessed on:
- **Accuracy Score**
- **Full Classification Report** (Precision, Recall, F1-Score per class)
- **Confusion Matrix Heatmap** (saved to `visuals/`)
- **Accuracy Comparison Bar Chart**

---

## 🏆 Results

| Model | Accuracy | Macro F1 |
|-------|----------|----------|
| **Logistic Regression** ★ | **93.33%** | **0.93** |
| K-Nearest Neighbours | 93.33% | 0.93 |
| Random Forest | 90.00% | 0.90 |

> **Winner: Logistic Regression** — Ties with KNN on accuracy but is preferred for its **balanced precision/recall trade-off** per class, **interpretable coefficients**, and **superior inference speed**.

**Common finding across all models:** *Iris setosa* achieves a perfect F1-score of **1.00**, confirming it is fully linearly separable from the other two species in petal feature space.

---

## 🚀 Setup & Run Instructions

Follow these steps to run the notebook on your local machine.

### Prerequisites
- Python 3.11+ installed ([python.org](https://www.python.org/downloads/))
- Git (optional, for cloning)

### Step 1 — Clone or Download the Repository

```bash
git clone https://github.com/<your-username>/OIBSIP_Iris_Project.git
cd OIBSIP_Iris_Project
```

### Step 2 — Create a Virtual Environment

**Windows (PowerShell):**
```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

**macOS / Linux:**
```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Step 3 — Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 4 — Launch Jupyter and Run the Notebook

```bash
jupyter notebook iris_classification.ipynb
```

Or with JupyterLab:
```bash
jupyter lab iris_classification.ipynb
```

**Then:** In the opened browser tab, go to **Kernel → Restart & Run All** to execute all cells from scratch.

> All plots will be saved to the `visuals/` directory and also rendered inline in the notebook.

---

## 📝 Notebook Sections

| # | Section | Description |
|---|---------|-------------|
| 1 | 📦 Setup & Imports | Library imports and global constants |
| 2 | 📊 Data Loading | Load from sklearn, map labels |
| 3 | 🔍 Advanced EDA | Stats, pairplot, box plots |
| 4 | 🎯 Feature Selection | Analysis of discriminative features |
| 5 | ⚙️ Preprocessing | Train-test split, StandardScaler |
| 6 | 🤖 Model Training | LR, KNN, Random Forest |
| 7 | 📈 Evaluation | Accuracy, F1, confusion matrices |
| 8 | 🏆 Conclusion | Best model declaration with justification |

---

## 👨‍💻 Author

**Asif Ahmad** — Data Science Intern @ Oasis Infobyte

---

*This project was developed as part of the Oasis Infobyte Data Science Internship programme.*
