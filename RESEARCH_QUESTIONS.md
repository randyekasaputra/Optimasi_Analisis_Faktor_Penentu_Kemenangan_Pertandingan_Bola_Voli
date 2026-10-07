# Pertanyaan Penelitian (Research Questions)

## Judul Penelitian
**Optimasi Analisis Faktor Penentu Kemenangan Pertandingan Bola Voli Menggunakan XGBoost dan Optuna**

---

## 🎯 Pertanyaan Penelitian Utama

### RQ1: Identifikasi Faktor Penentu Kemenangan
**Apa saja faktor statistik yang paling signifikan mempengaruhi kemenangan dalam pertandingan bola voli?**

**Sub-pertanyaan:**
- RQ1.1: Apakah serangan (kills, hit percentage) memiliki pengaruh lebih besar dibanding pertahanan (digs, blocks)?
- RQ1.2: Bagaimana pengaruh service (aces vs service errors) terhadap hasil pertandingan?
- RQ1.3: Apakah terdapat perbedaan faktor penentu kemenangan antar konferensi yang berbeda?
- RQ1.4: Bagaimana interaksi antar fitur (misalnya kills × hit percentage) mempengaruhi prediksi?

**Metrik Evaluasi:**
- SHAP feature importance values
- Correlation analysis
- Feature importance dari XGBoost

---

### RQ2: Performa Model Prediksi
**Bagaimana performa model XGBoost dalam memprediksi hasil pertandingan bola voli dibandingkan dengan baseline models?**

**Sub-pertanyaan:**
- RQ2.1: Berapa akurasi prediksi model XGBoost pada data test set?
- RQ2.2: Bagaimana perbandingan performa XGBoost dengan Logistic Regression dan Random Forest?
- RQ2.3: Apakah model mengalami overfitting atau underfitting?
- RQ2.4: Bagaimana konsistensi performa model pada cross-validation?

**Metrik Evaluasi:**
- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC Score
- Confusion Matrix
- 5-fold Cross-Validation Score

---

### RQ3: Efektivitas Optimasi Hyperparameter
**Seberapa besar peningkatan performa yang diperoleh dengan menggunakan optimasi Optuna dibandingkan dengan default hyperparameters?**

**Sub-pertanyaan:**
- RQ3.1: Berapa peningkatan akurasi setelah hyperparameter tuning?
- RQ3.2: Hyperparameter mana yang paling berpengaruh terhadap performa model?
- RQ3.3: Berapa jumlah trial optimal yang diperlukan untuk konvergensi?
- RQ3.4: Bagaimana trade-off antara computational cost dan improvement performance?

**Metrik Evaluasi:**
- Accuracy improvement (%)
- Training time comparison
- Number of trials to convergence
- Best hyperparameters configuration
- Optimization history visualization

---

### RQ4: Interpretabilitas Model
**Bagaimana model menjelaskan keputusan prediksi dan apa insight yang dapat diperoleh menggunakan SHAP analysis?**

**Sub-pertanyaan:**
- RQ4.1: Fitur mana yang memberikan kontribusi positif/negatif terbesar terhadap prediksi kemenangan?
- RQ4.2: Bagaimana pola kontribusi fitur berubah untuk prediksi yang berbeda?
- RQ4.3: Apakah terdapat threshold value tertentu pada fitur kunci yang menentukan kemenangan?
- RQ4.4: Bagaimana model dapat membantu coach dalam strategi pertandingan?

**Metrik Evaluasi:**
- SHAP summary plots
- SHAP dependence plots
- Individual prediction explanations
- Force plots untuk case studies

---

## 🔬 Hipotesis Penelitian

### H1: Feature Importance
**Hipotesis**: Serangan (kills dan hit percentage) memiliki pengaruh paling signifikan terhadap kemenangan dibandingkan faktor lainnya.

### H2: Model Performance
**Hipotesis**: XGBoost dengan Optuna optimization akan menghasilkan akurasi ≥85% dalam memprediksi hasil pertandingan.

### H3: Optimization Impact
**Hipotesis**: Hyperparameter tuning dengan Optuna akan meningkatkan akurasi minimal 5% dibandingkan default hyperparameters.

### H4: Model Interpretability
**Hipotesis**: SHAP analysis akan mengungkapkan threshold values yang jelas untuk fitur-fitur kunci yang memisahkan tim pemenang dan pecundang.

---

## 📊 Rencana Analisis

### Fase 1: Exploratory Data Analysis (EDA)
- Descriptive statistics
- Distribution analysis
- Correlation analysis
- Win/loss ratio analysis per feature

### Fase 2: Model Development
- Baseline models (Logistic Regression, Random Forest)
- XGBoost with default parameters
- Performance comparison

### Fase 3: Hyperparameter Optimization
- Define search space
- Optuna optimization (100-200 trials)
- Best model selection

### Fase 4: Model Evaluation
- Test set evaluation
- Cross-validation
- Performance metrics calculation
- Error analysis

### Fase 5: Model Interpretation
- SHAP values calculation
- Feature importance ranking
- Dependency analysis
- Case studies

---

## 📝 Expected Contributions

### Theoretical Contributions
1. Pemahaman mendalam tentang faktor-faktor kunci kemenangan dalam bola voli
2. Validasi penerapan XGBoost untuk prediksi hasil pertandingan olahraga
3. Demonstrasi efektivitas Optuna untuk hyperparameter optimization

### Practical Contributions
1. Model prediksi yang dapat digunakan untuk analisis pertandingan
2. Tool interpretable untuk membantu keputusan strategis coach
3. Framework yang dapat diadaptasi untuk olahraga lain

---

## 📅 Timeline Penelitian

| Fase | Aktivitas | Estimasi Waktu |
|------|-----------|----------------|
| 1 | Literature Review | 2 minggu |
| 2 | Data Collection & Preprocessing | 1 minggu |
| 3 | Exploratory Data Analysis | 1 minggu |
| 4 | Baseline Model Development | 1 minggu |
| 5 | XGBoost Implementation | 1 minggu |
| 6 | Hyperparameter Optimization | 1 minggu |
| 7 | Model Evaluation | 1 minggu |
| 8 | SHAP Analysis & Interpretation | 1 minggu |
| 9 | Documentation & Report Writing | 2 minggu |

**Total**: ~11 minggu

---

**Tanggal Penyusunan**: 7 Oktober 2026  
**Status**: Draft - Menunggu Review
