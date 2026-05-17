# Beginner Machine Learning - Clustering & Classification

This project is the final submission for the course **Belajar Machine Learning Pemula (BMLP)**, focusing on bank transaction data analysis using **Clustering** and **Classification** techniques for fraud detection and anomaly identification.

---

## 📋 Table of Contents

- [Project Description](#project-description)
- [File Structure](#file-structure)
- [Dataset](#dataset)
- [Notebooks](#notebooks)
- [Generated Models](#generated-models)
- [Libraries Used](#libraries-used)
- [How to Use](#how-to-use)
- [Key Features](#key-features)
- [Analysis Results](#analysis-results)
- [Project Goals](#project-goals)
- [Important Notes](#important-notes)
- [Author](#author)
- [License](#license)

---

## 📝 Project Description

This project analyzes transaction behavior and financial activity patterns from over **2,512** bank transaction samples. The dataset includes various transaction attributes, customer demographics, and usage patterns, which make it suitable for:

- **Fraud Detection**
- **Anomaly Detection**
- **Customer Segmentation**

The project is divided into two main parts:
1. **Clustering** - Grouping transactions by similar patterns
2. **Classification** - Predicting classes/targets based on available features

---

## 📁 File Structure

```
Machine Learning Pemula/
│
├── [Clustering]_Submission_Akhir_BMLP_Your_Name.ipynb    # Notebook for clustering analysis
├── [Klasifikasi]_Submission_Akhir_BMLP_Your_Name.ipynb  # Notebook for classification
│
├── bank_transactions_data_edited.csv                    # Bank transactions dataset (raw)
├── bank_transactions_data_edited.xlsx                   # Dataset in Excel format
├── bank_transactions_data_edited - new data.csv         # Dataset with new data
├── data_clustering.csv                                  # Preprocessed clustering dataset (normalized)
├── data_clustering_inverse.csv                          # Clustering dataset (original values)
│
├── model_clustering.h5                                  # KMeans clustering model
├── PCA_model_clustering.h5                              # PCA + clustering model
├── decision_tree_model.h5                               # Decision Tree classifier model
├── explore_RandomForest_classification.h5               # Random Forest classifier model
└── tuning_classification.h5                             # Tuned Random Forest model
```

---

## 📊 Dataset

### Main Dataset: Bank Transactions Data

The dataset provides an in-depth view of transaction behavior with **16 main features**:

| Feature | Description |
|---------|-------------|
| `TransactionID` | Unique alphanumeric identifier for each transaction |
| `AccountID` | Unique identifier for each account |
| `TransactionAmount` | Transaction amount in currency |
| `TransactionDate` | Date and time of the transaction |
| `TransactionType` | Transaction type: `Credit` or `Debit` |
| `Location` | Geographical location of the transaction (US city) |
| `DeviceID` | ID of the device used |
| `IP Address` | IPv4 address used |
| `MerchantID` | Unique merchant identifier |
| `AccountBalance` | Account balance after the transaction |
| `PreviousTransactionDate` | Date of the previous transaction |
| `Channel` | Transaction channel: `Online`, `ATM`, or `Branch` |
| `CustomerAge` | Age of the account holder |
| `CustomerOccupation` | Occupation: `Doctor`, `Engineer`, `Student`, `Retired` |
| `TransactionDuration` | Transaction duration (in seconds) |
| `LoginAttempts` | Number of login attempts before the transaction |

### Clustering Output Dataset

Preprocessed dataset with additional fields:
- `AgeGroup` - Age group (Young/Old)
- `Target` - Target label for classification

---

## 📓 Notebooks

### 1. [Clustering]_Submission_Akhir_BMLP_Your_Name.ipynb

Notebook for clustering analysis with the following steps:

**A. Import Libraries**
- pandas, numpy, matplotlib, seaborn
- sklearn: LabelEncoder, StandardScaler, KMeans, PCA
- yellowbrick: KElbowVisualizer

**B. Data Loading & Exploration**
- Load dataset from Google Sheets
- Explore data structure (`head`, `info`, `describe`)

**C. Data Preprocessing**
- Handle missing values
- Remove duplicates
- Feature encoding using `LabelEncoder`
- Handle outliers using the IQR method
- Standardize features with `StandardScaler`

**D. Clustering Analysis**
- Elbow method to determine the optimal number of clusters
- KMeans clustering
- PCA for dimensionality reduction
- Evaluate with Silhouette Score

**E. Results Interpretation**
- Inverse transform to obtain original values
- Analyze characteristics of each cluster

### 2. [Klasifikasi]_Submission_Akhir_BMLP_Your_Name.ipynb

Notebook for classification with the following steps:

**A. Import Libraries**
- sklearn: `train_test_split`, `DecisionTreeClassifier`, `RandomForestClassifier`
- sklearn metrics: `accuracy_score`, `precision_score`, `recall_score`, `f1_score`
- `GridSearchCV`, `RandomizedSearchCV` for hyperparameter tuning

**B. Data Loading**
- Uses `data_clustering_inverse.csv`
- One-Hot Encoding for categorical features

**C. Data Splitting**
- Train-test split with 80:20 ratio
- Stratified split to preserve class proportions

**D. Model Building**
- Decision Tree Classifier
- Random Forest Classifier

**E. Model Evaluation**
- Classification report (precision, recall, f1-score)
- Compare performance between models

**F. Hyperparameter Tuning**
- `GridSearchCV` for Random Forest
- Parameters: `n_estimators`, `max_depth`, `min_samples_split`

---

## 🤖 Generated Models

| Model File | Algorithm | Description |
|------------|-----------|-------------|
| `model_clustering.h5` | KMeans | Base clustering model |
| `PCA_model_clustering.h5` | PCA + KMeans | Model with PCA dimensionality reduction |
| `decision_tree_model.h5` | Decision Tree | Baseline classification model |
| `explore_RandomForest_classification.h5` | Random Forest | Random Forest classifier |
| `tuning_classification.h5` | Random Forest (Tuned) | Model with optimized hyperparameters |

---

## 📚 Libraries Used

### For Clustering:
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.preprocessing import LabelEncoder, StandardScaler
from sklearn.cluster import KMeans
from sklearn.decomposition import PCA
from sklearn.metrics import silhouette_score
from yellowbrick.cluster import KElbowVisualizer
import joblib
```

### For Classification:
```python
import pandas as pd
from sklearn.model_selection import train_test_split, GridSearchCV
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score, classification_report
import joblib
```

---

## 🚀 How to Use

### 1. Setup Environment
```bash
# Install required libraries
pip install pandas numpy matplotlib seaborn scikit-learn yellowbrick joblib
```

### 2. Run the Clustering Notebook
```python
# Open the clustering notebook
jupyter notebook "[Clustering]_Submission_Akhir_BMLP_Your_Name.ipynb"

# Run all cells (Run All)
```

### 3. Run the Classification Notebook
```python
# Open the classification notebook
jupyter notebook "[Klasifikasi]_Submission_Akhir_BMLP_Your_Name.ipynb"

# Run all cells (Run All)
```

### 4. Use the Trained Models
```python
import joblib

# Load clustering model
clustering_model = joblib.load('model_clustering.h5')

# Load classification model
classifier_model = joblib.load('tuning_classification.h5')

# Predict
predictions = classifier_model.predict(X_new)
```

---

## ⭐ Key Features

### A. Clustering Features:
- ✅ **Elbow Method** - Determine the optimal number of clusters
- ✅ **KMeans Clustering** - Popular clustering algorithm
- ✅ **PCA** - Dimensionality reduction for visualization
- ✅ **Silhouette Score** - Cluster quality evaluation
- ✅ **Outlier Handling** - Using the IQR method

### B. Classification Features:
- ✅ **Decision Tree** - Interpretable baseline model
- ✅ **Random Forest** - Ensemble method for higher accuracy
- ✅ **Hyperparameter Tuning** - `GridSearchCV` for optimization
- ✅ **Cross-validation** - Robust model validation
- ✅ **Comprehensive Metrics** - Accuracy, Precision, Recall, F1-Score

---

## 📈 Analysis Results

### Clustering Results:
- The dataset with **16 features** was successfully clustered
- Outliers were handled using the IQR method
- Cluster visualizations were produced using PCA

### Classification Results:
| Model | Accuracy | Precision | Recall | F1-Score |
|-------|----------|-----------|--------|----------|
| Decision Tree | 100% | 100% | 100% | 100% |
| Random Forest | 100% | 100% | 100% | 100% |
| Random Forest (Tuned) | 100% | 100% | 100% | 100% |

*Note: 100% results may indicate a relatively clean dataset and highly predictive features for the target.*

---

## 🎯 Project Goals

This project aims to:
1. **Learn clustering techniques** for transaction data segmentation
2. **Implement classification** for target prediction
3. **Apply best practices** in data preprocessing
4. **Explore hyperparameter tuning** for model optimization
5. **Understand the end-to-end machine learning workflow**

---

## 📝 Important Notes

- The dataset is sourced from a public Google Sheets URL
- Use the variable `df` consistently across notebooks
- Make sure to **Run All** cells before submission
- Do not change the provided cell structure
- Expected outputs should match the provided examples

---

## 👨‍💻 Author

**Name:** Haikal Fairuzi Maulana 
**Course:** Belajar Machine Learning Pemula (BMLP)  
**Submission:** Newbie Machine Learning Engineer  

---

## 📄 License

This project was created for educational purposes as part of the Belajar Machine Learning Pemula course.

---

*This README was automatically generated based on analysis of files in the repository.*
