# Metodologi Penelitian

## 📐 Framework Penelitian

Penelitian ini menggunakan pendekatan **kuantitatif** dengan metode **supervised machine learning** untuk klasifikasi biner (Win/Loss).

---

## 🔄 Alur Penelitian

```
┌─────────────────────────────────────────────────────────────┐
│                   1. DATA COLLECTION                        │
│  ├─ NCAA Women's Volleyball Statistics (2020-2025)          │
│  ├─ 6 files CSV (multi-season data)                         │
│  └─ ~20 features statistik pertandingan                     │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│               2. DATA PREPROCESSING                          │
│  ├─ Data Cleaning                                           │
│  │   ├─ Missing values handling                             │
│  │   ├─ Duplicate removal                                   │
│  │   └─ Outlier detection & treatment                       │
│  ├─ Data Transformation                                     │
│  │   ├─ Label encoding (Result: Win=1, Loss=0)             │
│  │   ├─ One-hot encoding (Conference, Team)                │
│  │   └─ Feature scaling (StandardScaler/MinMaxScaler)      │
│  └─ Data Integration                                        │
│      └─ Merge multi-year datasets                           │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│           3. EXPLORATORY DATA ANALYSIS (EDA)                │
│  ├─ Descriptive Statistics                                  │
│  │   ├─ Mean, median, std, min, max                         │
│  │   └─ Win/Loss distribution                               │
│  ├─ Visualization                                           │
│  │   ├─ Distribution plots (histogram, boxplot)            │
│  │   ├─ Correlation heatmap                                │
│  │   └─ Feature vs Target scatter plots                    │
│  └─ Feature Analysis                                        │
│      ├─ Feature correlation with target                     │
│      └─ Feature importance preliminary analysis             │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│              4. FEATURE ENGINEERING                         │
│  ├─ Feature Creation                                        │
│  │   ├─ Attack efficiency = (Kills - Errors) / Total Att   │
│  │   ├─ Service ratio = Aces / (Aces + SErr)              │
│  │   ├─ Block efficiency = TB / (TB + BErr)               │
│  │   └─ Team performance metrics                           │
│  ├─ Feature Selection                                       │
│  │   ├─ Variance threshold                                 │
│  │   ├─ Correlation analysis (remove multicollinearity)    │
│  │   └─ Recursive feature elimination (RFE)               │
│  └─ Feature Scaling                                        │
│      └─ Normalization for model input                      │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│               5. DATA SPLITTING                             │
│  ├─ Train Set: 70%                                         │
│  ├─ Validation Set: 15%                                    │
│  ├─ Test Set: 15%                                          │
│  └─ Stratified split (maintain Win/Loss ratio)            │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│            6. BASELINE MODEL DEVELOPMENT                    │
│  ├─ Logistic Regression                                    │
│  │   └─ Simple linear model sebagai baseline              │
│  ├─ Random Forest                                          │
│  │   └─ Ensemble method untuk comparison                  │
│  └─ Evaluation Metrics                                     │
│      ├─ Accuracy, Precision, Recall, F1-Score             │
│      └─ ROC-AUC                                            │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│          7. XGBOOST MODEL (DEFAULT PARAMS)                  │
│  ├─ Model Architecture                                     │
│  │   ├─ Objective: binary:logistic                        │
│  │   ├─ Eval metric: logloss, auc                         │
│  │   └─ Default hyperparameters                           │
│  ├─ Training                                               │
│  │   ├─ Train on training set                             │
│  │   ├─ Validate on validation set                        │
│  │   └─ Early stopping (patience=50)                      │
│  └─ Evaluation                                             │
│      └─ Compare with baseline models                       │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│     8. HYPERPARAMETER OPTIMIZATION (OPTUNA)                 │
│  ├─ Define Search Space                                    │
│  │   ├─ max_depth: [3, 10]                                │
│  │   ├─ learning_rate: [0.01, 0.3]                        │
│  │   ├─ n_estimators: [100, 1000]                         │
│  │   ├─ subsample: [0.6, 1.0]                             │
│  │   ├─ colsample_bytree: [0.6, 1.0]                      │
│  │   ├─ min_child_weight: [1, 10]                         │
│  │   ├─ gamma: [0, 5]                                     │
│  │   └─ reg_alpha, reg_lambda: [0, 10]                   │
│  ├─ Optimization Strategy                                  │
│  │   ├─ Optimization algorithm: TPE (Tree-structured      │
│  │   │   Parzen Estimator)                                │
│  │   ├─ Number of trials: 100-200                         │
│  │   ├─ Objective: Maximize ROC-AUC                       │
│  │   └─ Cross-validation: 5-fold CV                       │
│  ├─ Pruning Strategy                                       │
│  │   └─ MedianPruner (early stopping bad trials)         │
│  └─ Best Model Selection                                   │
│      └─ Save best hyperparameters                          │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│         9. MODEL TRAINING (OPTIMIZED XGBOOST)               │
│  ├─ Train with best hyperparameters                        │
│  ├─ Full training set                                      │
│  ├─ Cross-validation (5-fold)                              │
│  └─ Save trained model                                     │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│              10. MODEL EVALUATION                           │
│  ├─ Test Set Performance                                   │
│  │   ├─ Accuracy                                           │
│  │   ├─ Precision (positive predictive value)             │
│  │   ├─ Recall (sensitivity)                              │
│  │   ├─ F1-Score (harmonic mean)                          │
│  │   ├─ ROC-AUC Score                                     │
│  │   └─ Confusion Matrix                                  │
│  ├─ Cross-Validation Results                               │
│  │   └─ Mean ± Std of CV scores                           │
│  ├─ Comparison                                             │
│  │   ├─ Default XGBoost vs Optimized XGBoost             │
│  │   └─ XGBoost vs Baseline models                       │
│  └─ Error Analysis                                         │
│      ├─ False positives analysis                          │
│      └─ False negatives analysis                          │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│         11. MODEL INTERPRETATION (SHAP)                     │
│  ├─ SHAP Values Calculation                                │
│  │   └─ TreeExplainer for XGBoost                         │
│  ├─ Global Interpretation                                  │
│  │   ├─ SHAP summary plot (feature importance)           │
│  │   ├─ SHAP bar plot (mean absolute SHAP values)        │
│  │   └─ Feature dependence plots                         │
│  ├─ Local Interpretation                                   │
│  │   ├─ Force plots (individual predictions)             │
│  │   ├─ Waterfall plots                                   │
│  │   └─ Decision plots                                    │
│  └─ Insights Extraction                                    │
│      ├─ Key features for winning                           │
│      ├─ Feature interactions                               │
│      └─ Threshold values                                   │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│          12. RESULTS & DISCUSSION                           │
│  ├─ Research Questions Answered                            │
│  ├─ Hypothesis Testing                                     │
│  ├─ Comparison with Literature                             │
│  └─ Limitations & Future Work                              │
└─────────────────────────────────────────────────────────────┘
```

---

## 🎯 Evaluation Metrics

### Classification Metrics

1. **Accuracy**
   ```
   Accuracy = (TP + TN) / (TP + TN + FP + FN)
   ```

2. **Precision**
   ```
   Precision = TP / (TP + FP)
   ```

3. **Recall (Sensitivity)**
   ```
   Recall = TP / (TP + FN)
   ```

4. **F1-Score**
   ```
   F1 = 2 × (Precision × Recall) / (Precision + Recall)
   ```

5. **ROC-AUC Score**
   - Area Under the Receiver Operating Characteristic Curve
   - Range: 0-1 (higher is better)
   - Measures model's ability to distinguish between classes

### Model Comparison Metrics

- **Baseline vs Optimized**: Percentage improvement
- **Training Time**: Computational efficiency
- **Cross-validation Consistency**: Standard deviation of CV scores

---

## 🧪 Experimental Design

### Dataset Split Strategy
```python
# Stratified split to maintain class balance
- Training: 70% (for model learning)
- Validation: 15% (for hyperparameter tuning)
- Test: 15% (for final evaluation)
```

### Cross-Validation
```python
# 5-Fold Stratified Cross-Validation
- Ensures robust performance estimation
- Reduces variance in performance metrics
- Used during hyperparameter optimization
```

### Random Seed
```python
RANDOM_STATE = 42  # For reproducibility
```

---

## 🔧 Hyperparameter Tuning Details

### Optuna Configuration

```python
study = optuna.create_study(
    study_name='xgboost_volleyball_optimization',
    direction='maximize',  # Maximize ROC-AUC
    sampler=optuna.samplers.TPESampler(seed=42),
    pruner=optuna.pruners.MedianPruner(
        n_startup_trials=10,
        n_warmup_steps=20
    )
)

study.optimize(
    objective_function,
    n_trials=200,
    timeout=3600,  # 1 hour max
    show_progress_bar=True
)
```

### XGBoost Parameters Search Space

| Parameter | Type | Range | Description |
|-----------|------|-------|-------------|
| max_depth | int | [3, 10] | Maximum tree depth |
| learning_rate | float | [0.01, 0.3] | Step size shrinkage |
| n_estimators | int | [100, 1000] | Number of boosting rounds |
| subsample | float | [0.6, 1.0] | Subsample ratio of training instances |
| colsample_bytree | float | [0.6, 1.0] | Subsample ratio of columns |
| min_child_weight | int | [1, 10] | Minimum sum of instance weight |
| gamma | float | [0, 5] | Minimum loss reduction |
| reg_alpha | float | [0, 10] | L1 regularization term |
| reg_lambda | float | [0, 10] | L2 regularization term |

---

## 📊 SHAP Analysis Strategy

### Global Interpretation

1. **Feature Importance Ranking**
   - Mean absolute SHAP values per feature
   - Identifies most influential features

2. **Summary Plot**
   - Distribution of SHAP values for each feature
   - Shows positive/negative impact
   - Reveals feature value effects

3. **Dependence Plots**
   - Relationship between feature value and SHAP value
   - Shows feature interactions
   - Identifies threshold effects

### Local Interpretation

1. **Force Plots**
   - Individual prediction explanation
   - Shows feature contributions
   - Base value → prediction path

2. **Waterfall Plots**
   - Step-by-step feature contributions
   - Clear visualization of additive nature

3. **Decision Plots**
   - Multiple predictions comparison
   - Shows decision paths

---

## 📈 Success Criteria

### Minimum Performance Targets

| Metric | Baseline | Target | Excellent |
|--------|----------|--------|-----------|
| Accuracy | 65% | 80% | 90% |
| Precision | 60% | 75% | 85% |
| Recall | 60% | 75% | 85% |
| F1-Score | 60% | 75% | 85% |
| ROC-AUC | 0.70 | 0.85 | 0.95 |

### Optimization Success

- Minimum 5% improvement from default XGBoost
- Convergence within 200 trials
- Consistent CV performance (std < 5%)

---

## 🔬 Statistical Testing

### Performance Comparison

1. **Paired t-test**
   - Compare baseline vs optimized model
   - Significance level: α = 0.05

2. **Cross-validation Variance**
   - Assess model stability
   - Lower variance = more reliable

---

## 💾 Model Persistence

### Saving Strategy

```python
# Save best model
import joblib
joblib.dump(best_model, 'models/xgboost_optimized.pkl')

# Save hyperparameters
import json
with open('models/best_hyperparameters.json', 'w') as f:
    json.dump(best_params, f, indent=4)

# Save SHAP explainer
joblib.dump(explainer, 'models/shap_explainer.pkl')
```

---

## 📝 Reproducibility

### Ensuring Reproducible Results

```python
import random
import numpy as np
import tensorflow as tf

SEED = 42

# Set seeds
random.seed(SEED)
np.random.seed(SEED)

# XGBoost random state
xgb_params['random_state'] = SEED

# Train-test split
train_test_split(random_state=SEED)
```

---

## ⚠️ Assumptions & Limitations

### Assumptions
1. Dataset representatif untuk populasi NCAA Women's Volleyball
2. Statistik pertandingan akurat dan konsisten
3. Fitur yang tersedia cukup untuk prediksi
4. Independence of observations (setiap pertandingan independen)

### Limitations
1. Model terbatas pada fitur yang tersedia dalam dataset
2. Tidak memperhitungkan faktor external (injuries, home advantage detail)
3. Temporal dependencies mungkin diabaikan
4. Generalisasi ke level lain (non-NCAA) belum diuji

---

## 🎓 Ethical Considerations

1. **Data Privacy**: Dataset publik, tidak ada informasi personal
2. **Fair Use**: Hasil penelitian untuk tujuan akademik
3. **Transparency**: Model interpretable dengan SHAP
4. **Limitations Disclosure**: Keterbatasan model dijelaskan dengan jelas

---

**Prepared by**: Research Team  
**Date**: 7 Oktober 2026  
**Version**: 1.0
