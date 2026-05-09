# Machine Learning Pemula - Clustering & Classification

Proyek ini merupakan submission akhir untuk kursus **Belajar Machine Learning Pemula (BMLP)** yang fokus pada analisis data transaksi bank menggunakan teknik **Clustering** dan **Classification** untuk deteksi penipuan (fraud detection) dan identifikasi anomali.

---

## 📋 Daftar Isi

- [Deskripsi Proyek](#deskripsi-proyek)
- [Struktur File](#struktur-file)
- [Dataset](#dataset)
- [Notebook](#notebook)
- [Model yang Dihasilkan](#model-yang-dihasilkan)
- [Library yang Digunakan](#library-yang-digunakan)
- [Cara Penggunaan](#cara-penggunaan)
- [Fitur Utama](#fitur-utama)
- [Hasil Analisis](#hasil-analisis)

---

## 📝 Deskripsi Proyek

Proyek ini menganalisis perilaku transaksi dan pola aktivitas keuangan dari **2.512+ sampel data transaksi bank**. Dataset mencakup berbagai atribut transaksi, demografi nasabah, dan pola penggunaan yang sangat ideal untuk:

- **Deteksi Penipuan (Fraud Detection)**
- **Identifikasi Anomali (Anomaly Detection)**
- **Segmentasi Nasabah (Customer Segmentation)**

Proyek ini terdiri dari dua bagian utama:
1. **Clustering** - Mengelompokkan transaksi berdasarkan pola serupa
2. **Classification** - Memprediksi kelas/target berdasarkan fitur yang ada

---

## 📁 Struktur File

```
Machine Learning Pemula/
│
├── [Clustering]_Submission_Akhir_BMLP_Your_Name.ipynb    # Notebook untuk analisis clustering
├── [Klasifikasi]_Submission_Akhir_BMLP_Your_Name.ipynb # Notebook untuk klasifikasi
│
├── bank_transactions_data_edited.csv                     # Dataset transaksi bank (raw)
├── bank_transactions_data_edited.xlsx                  # Dataset dalam format Excel
├── bank_transactions_data_edited - new data.csv          # Dataset dengan data baru
├── data_clustering.csv                                 # Dataset hasil clustering (normalized)
├── data_clustering_inverse.csv                         # Dataset hasil clustering (original values)
│
├── model_clustering.h5                                 # Model KMeans clustering
├── PCA_model_clustering.h5                             # Model PCA + Clustering
├── decision_tree_model.h5                              # Model Decision Tree classifier
├── explore_RandomForest_classification.h5              # Model Random Forest classifier
└── tuning_classification.h5                            # Model Random Forest dengan tuning
```

---

## 📊 Dataset

### Dataset Utama: Bank Transactions Data

Dataset ini menyajikan gambaran mendalam mengenai perilaku transaksi dengan **16 fitur utama**:

| Fitur | Deskripsi |
|-------|-----------|
| `TransactionID` | Pengidentifikasi unik alfanumerik untuk setiap transaksi |
| `AccountID` | ID unik untuk setiap akun |
| `TransactionAmount` | Nilai transaksi dalam mata uang |
| `TransactionDate` | Tanggal dan waktu transaksi |
| `TransactionType` | Tipe transaksi: `Credit` atau `Debit` |
| `Location` | Lokasi geografis transaksi (kota di Amerika Serikat) |
| `DeviceID` | ID perangkat yang digunakan |
| `IP Address` | Alamat IPv4 yang digunakan |
| `MerchantID` | ID unik merchant |
| `AccountBalance` | Saldo akun setelah transaksi |
| `PreviousTransactionDate` | Tanggal transaksi terakhir |
| `Channel` | Kanal transaksi: `Online`, `ATM`, atau `Branch` |
| `CustomerAge` | Usia pemilik akun |
| `CustomerOccupation` | Profesi: `Doctor`, `Engineer`, `Student`, `Retired` |
| `TransactionDuration` | Lama waktu transaksi (dalam detik) |
| `LoginAttempts` | Jumlah upaya login sebelum transaksi |

### Dataset Hasil Clustering

Dataset hasil preprocessing dengan fitur tambahan:
- `AgeGroup` - Kelompok usia (Muda/Tua)
- `Target` - Label target untuk klasifikasi

---

## 📓 Notebook

### 1. [Clustering]_Submission_Akhir_BMLP_Your_Name.ipynb

Notebook untuk analisis clustering dengan tahapan:

**A. Import Library**
- pandas, numpy, matplotlib, seaborn
- sklearn: LabelEncoder, StandardScaler, KMeans, PCA
- yellowbrick: KElbowVisualizer

**B. Data Loading & Exploration**
- Load dataset dari Google Sheets
- Eksplorasi struktur data (head, info, describe)

**C. Data Preprocessing**
- Handling missing values
- Removing duplicates
- Feature encoding dengan LabelEncoder
- Handling outliers menggunakan IQR method
- Standardization dengan StandardScaler

**D. Clustering Analysis**
- Elbow method untuk menentukan jumlah cluster optimal
- KMeans clustering
- PCA untuk dimensionality reduction
- Evaluasi dengan Silhouette Score

**E. Interpretasi Hasil**
- Inverse transform untuk mendapatkan nilai asli
- Analisis karakteristik setiap cluster

### 2. [Klasifikasi]_Submission_Akhir_BMLP_Your_Name.ipynb

Notebook untuk klasifikasi dengan tahapan:

**A. Import Library**
- sklearn: train_test_split, DecisionTree, RandomForest
- sklearn metrics: accuracy_score, precision_score, recall_score, f1_score
- GridSearchCV, RandomizedSearchCV untuk hyperparameter tuning

**B. Data Loading**
- Menggunakan `data_clustering_inverse.csv`
- One Hot Encoding untuk fitur kategorikal

**C. Data Splitting**
- Train-test split dengan proporsi 80:20
- Stratified split untuk menjaga proporsi kelas

**D. Model Building**
- Decision Tree Classifier
- Random Forest Classifier

**E. Model Evaluation**
- Classification report (precision, recall, f1-score)
- Perbandingan performa antar model

**F. Hyperparameter Tuning**
- GridSearchCV untuk Random Forest
- Parameter: `n_estimators`, `max_depth`, `min_samples_split`

---

## 🤖 Model yang Dihasilkan

| Model File | Algoritma | Deskripsi |
|------------|-----------|-----------|
| `model_clustering.h5` | KMeans | Model clustering dasar |
| `PCA_model_clustering.h5` | PCA + KMeans | Model dengan reduksi dimensi PCA |
| `decision_tree_model.h5` | Decision Tree | Model klasifikasi baseline |
| `explore_RandomForest_classification.h5` | Random Forest | Model klasifikasi Random Forest |
| `tuning_classification.h5` | Random Forest (Tuned) | Model dengan hyperparameter optimal |

---

## 📚 Library yang Digunakan

### Untuk Clustering:
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

### Untuk Klasifikasi:
```python
import pandas as pd
from sklearn.model_selection import train_test_split, GridSearchCV
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score, classification_report
import joblib
```

---

## 🚀 Cara Penggunaan

### 1. Setup Environment
```bash
# Install library yang diperlukan
pip install pandas numpy matplotlib seaborn scikit-learn yellowbrick joblib
```

### 2. Menjalankan Notebook Clustering
```python
# Buka notebook clustering
jupyter notebook "[Clustering]_Submission_Akhir_BMLP_Your_Name.ipynb"

# Jalankan seluruh cell (Run All)
```

### 3. Menjalankan Notebook Klasifikasi
```python
# Buka notebook klasifikasi
jupyter notebook "[Klasifikasi]_Submission_Akhir_BMLP_Your_Name.ipynb"

# Jalankan seluruh cell (Run All)
```

### 4. Menggunakan Model yang Sudah Dilatih
```python
import joblib

# Load model clustering
clustering_model = joblib.load('model_clustering.h5')

# Load model klasifikasi
classifier_model = joblib.load('tuning_classification.h5')

# Prediksi
predictions = classifier_model.predict(X_new)
```

---

## ⭐ Fitur Utama

### A. Clustering Features:
- ✅ **Elbow Method** - Menentukan jumlah cluster optimal
- ✅ **KMeans Clustering** - Algoritma clustering populer
- ✅ **PCA** - Reduksi dimensi untuk visualisasi
- ✅ **Silhouette Score** - Evaluasi kualitas cluster
- ✅ **Outlier Handling** - Menggunakan metode IQR

### B. Classification Features:
- ✅ **Decision Tree** - Model interpretable baseline
- ✅ **Random Forest** - Ensemble method untuk akurasi tinggi
- ✅ **Hyperparameter Tuning** - GridSearchCV untuk optimasi
- ✅ **Cross-validation** - Validasi model yang robust
- ✅ **Comprehensive Metrics** - Accuracy, Precision, Recall, F1-Score

---

## 📈 Hasil Analisis

### Clustering Results:
- Dataset dengan **16 fitur** berhasil diklusterkan
- Outlier berhasil ditangani menggunakan metode IQR
- Visualisasi cluster menggunakan PCA

### Classification Results:
| Model | Accuracy | Precision | Recall | F1-Score |
|-------|----------|-----------|--------|----------|
| Decision Tree | 100% | 100% | 100% | 100% |
| Random Forest | 100% | 100% | 100% | 100% |
| Random Forest (Tuned) | 100% | 100% | 100% | 100% |

*Note: Hasil 100% mengindikasikan dataset yang relatif bersih dan fitur yang sangat prediktif untuk target.*

---

## 🎯 Tujuan Proyek

Proyek ini bertujuan untuk:
1. **Mempelajari teknik clustering** untuk segmentasi data transaksi
2. **Mengimplementasikan klasifikasi** untuk prediksi target
3. **Menerapkan best practices** dalam preprocessing data
4. **Mengeksplorasi hyperparameter tuning** untuk optimasi model
5. **Memahami end-to-end workflow** machine learning

---

## 📝 Catatan Penting

- Dataset bersumber dari Google Sheets dengan URL publik
- Gunakan variabel `df` secara konsisten di seluruh notebook
- Pastikan untuk melakukan **Run All** sebelum submission
- Jangan mengubah struktur cell yang sudah disediakan
- Output yang diharapkan harus sesuai dengan contoh yang diberikan

---

## 👨‍💻 Author

**Nama:** Your Name  
**Kursus:** Belajar Machine Learning Pemula (BMLP)  
**Submission:** Akhir BMLP

---

## 📄 Lisensi

Proyek ini dibuat untuk tujuan edukasi sebagai bagian dari kursus Belajar Machine Learning Pemula.

---

*README ini dibuat secara otomatis berdasarkan analisis file-file dalam repository.*
