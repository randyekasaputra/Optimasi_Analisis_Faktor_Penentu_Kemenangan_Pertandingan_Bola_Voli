# Optimasi Analisis Faktor Penentu Kemenangan Pertandingan Bola Voli Menggunakan XGBoost dan Optuna

## 📋 Deskripsi Proyek

Penelitian ini bertujuan untuk menganalisis dan memprediksi faktor-faktor penentu kemenangan dalam pertandingan bola voli menggunakan metode machine learning. Penelitian ini menggunakan algoritma **XGBoost** yang dioptimasi dengan **Optuna** untuk hyperparameter tuning, serta memanfaatkan **SHAP (SHapley Additive exPlanations)** untuk interpretabilitas model.

## 🎯 Tujuan Penelitian

1. Mengidentifikasi faktor-faktor statistik yang paling berpengaruh terhadap kemenangan tim dalam pertandingan bola voli
2. Membangun model prediksi yang akurat untuk memprediksi hasil pertandingan
3. Mengoptimasi performa model menggunakan hyperparameter tuning dengan Optuna
4. Memberikan interpretasi yang jelas mengenai kontribusi setiap fitur menggunakan SHAP values

## ❓ Pertanyaan Penelitian

1. Apa saja faktor statistik yang paling signifikan mempengaruhi kemenangan dalam pertandingan bola voli?
2. Bagaimana performa model XGBoost dalam memprediksi hasil pertandingan bola voli?
3. Seberapa besar peningkatan akurasi yang diperoleh dengan menggunakan optimasi Optuna?
4. Bagaimana interpretasi model dalam menjelaskan keputusan prediksi menggunakan SHAP?

## 📊 Dataset

Dataset yang digunakan berasal dari **NCAA Women's Volleyball Division I** yang mencakup statistik pertandingan dari tahun 2020-2025.

### Sumber Data
- **Sumber**: NCAA Women's Volleyball Statistics
- **Periode**: 2020-2025
- **Jumlah File**: 6 file (satu file per musim)
- **Lokasi**: `data/raw/`

### Fitur Dataset
Dataset mencakup statistik pertandingan berikut:
- **Season**: Musim pertandingan
- **Date**: Tanggal pertandingan
- **Team**: Nama tim
- **Conference**: Konferensi tim
- **Opponent**: Tim lawan
- **Result**: Hasil pertandingan (Win/Loss)
- **S**: Jumlah set
- **Kills**: Jumlah serangan yang menghasilkan poin
- **Errors**: Jumlah kesalahan
- **Total Attacks**: Total serangan
- **Hit Pct**: Persentase keberhasilan serangan
- **Assists**: Jumlah assist
- **Aces**: Jumlah service ace
- **SErr**: Service error
- **Digs**: Jumlah dig
- **RErr**: Reception error
- **Block Solos**: Block tunggal
- **Block Assists**: Block assist
- **BErr**: Block error
- **TB**: Total block
- **PTS**: Total poin
- **BHE**: Ball handling error

## 🛠️ Teknologi dan Tools

### Programming Language
- **Python 3.x**

### Libraries Utama
- **pandas**: Manipulasi dan analisis data
- **numpy**: Komputasi numerik
- **scikit-learn**: Machine learning toolkit
- **xgboost**: Algoritma gradient boosting
- **optuna**: Hyperparameter optimization framework
- **shap**: Model interpretability
- **matplotlib & seaborn**: Visualisasi data
- **jupyter**: Interactive development environment

### Development Tools
- **VS Code / OpenCode**: IDE
- **Git & GitHub**: Version control
- **Virtual Environment**: Isolasi dependencies

## 📁 Struktur Proyek

```
Optimasi_Analisis_Faktor_Penentu_Kemenangan_Pertandingan_Bola_Voli/
│
├── data/
│   ├── raw/                          # Data mentah
│   │   ├── wvb_teammatch_div1_2020.csv
│   │   ├── wvb_teammatch_div1_2021.csv
│   │   ├── wvb_teammatch_div1_2022.csv
│   │   ├── wvb_teammatch_div1_2023.csv
│   │   ├── wvb_teammatch_div1_2024.csv
│   │   └── wvb_teammatch_div1_2025.csv
│   └── processed/                    # Data yang telah diproses
│
├── src/
│   ├── test_environment.py          # Testing environment setup
│   ├── data_preprocessing.py        # (To be created) Data preprocessing
│   ├── feature_engineering.py       # (To be created) Feature engineering
│   ├── model_training.py            # (To be created) Model training
│   ├── hyperparameter_tuning.py     # (To be created) Optuna optimization
│   └── model_evaluation.py          # (To be created) Model evaluation & SHAP
│
├── notebooks/                        # Jupyter notebooks untuk eksplorasi
│   └── exploratory_data_analysis.ipynb
│
├── models/                           # Trained models
│
├── results/                          # Hasil eksperimen dan visualisasi
│
├── state of the art.pdf             # Literature review dan penelitian terdahulu
├── requirements.txt                  # Python dependencies
├── README.md                         # Dokumentasi proyek
└── .gitignore                       # Git ignore file
```

## 🚀 Instalasi dan Setup

### 1. Clone Repository
```bash
git clone https://github.com/[username]/[repository-name].git
cd Optimasi_Analisis_Faktor_Penentu_Kemenangan_Pertandingan_Bola_Voli
```

### 2. Buat Virtual Environment
```bash
python -m venv .venv
```

### 3. Aktifkan Virtual Environment
**Windows:**
```bash
.venv\Scripts\activate
```

**Linux/Mac:**
```bash
source .venv/bin/activate
```

### 4. Install Dependencies
```bash
pip install -r requirements.txt
```

### 5. Test Environment
```bash
python src/test_environment.py
```

## 📈 Metodologi

### 1. Data Preprocessing
- Pembersihan data (handling missing values, outliers)
- Encoding variabel kategorikal
- Feature scaling/normalization
- Train-test split

### 2. Feature Engineering
- Pembuatan fitur baru dari statistik pertandingan
- Analisis korelasi antar fitur
- Feature selection

### 3. Model Development
- **Baseline Model**: Logistic Regression, Random Forest
- **Main Model**: XGBoost Classifier
- **Optimization**: Optuna untuk hyperparameter tuning

### 4. Model Evaluation
- Accuracy, Precision, Recall, F1-Score
- Confusion Matrix
- ROC-AUC Curve
- Cross-validation

### 5. Model Interpretability
- SHAP values untuk feature importance
- SHAP summary plots
- SHAP dependence plots
- Individual prediction explanation

## 📚 State of the Art

Penelitian ini didasarkan pada studi literatur dari 10 artikel ilmiah terkait:
- Machine learning dalam analisis olahraga
- Prediksi hasil pertandingan menggunakan XGBoost
- Hyperparameter optimization dengan Optuna
- Model interpretability dengan SHAP

Detail lengkap dapat dilihat di file: `state of the art.pdf`

## 👥 Kontributor

- **Nama Peneliti**: [Nama Anda]
- **Institusi**: [Nama Institusi]
- **Program Studi**: [Program Studi]

## 📄 Lisensi

[Tentukan lisensi yang sesuai, misalnya MIT License]

## 📧 Kontak

Untuk pertanyaan atau kolaborasi, hubungi:
- Email: [email@example.com]
- GitHub: [@username](https://github.com/username)

## 🙏 Acknowledgments

- NCAA untuk penyediaan data statistik bola voli
- Komunitas open-source untuk libraries yang digunakan
- [Tambahkan acknowledgments lainnya]

---

**Last Updated**: 7 Oktober 2026
