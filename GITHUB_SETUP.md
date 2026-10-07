# 📦 Panduan Setup GitHub Repository

## 🚀 Langkah-langkah Push ke GitHub

### 1️⃣ Buat Repository Baru di GitHub

1. Buka [GitHub](https://github.com) dan login
2. Klik tombol **"New"** atau **"+"** → **"New repository"**
3. Isi detail repository:
   - **Repository name**: `Optimasi_Analisis_Faktor_Penentu_Kemenangan_Pertandingan_Bola_Voli`
   - **Description**: `Analisis dan prediksi faktor penentu kemenangan pertandingan bola voli menggunakan XGBoost dan Optuna`
   - **Visibility**: Public atau Private (sesuai kebutuhan)
   - **⚠️ JANGAN centang**: "Initialize this repository with a README" (karena kita sudah punya)
4. Klik **"Create repository"**

### 2️⃣ Hubungkan Local Repository dengan GitHub

Setelah repository GitHub dibuat, jalankan perintah berikut di terminal:

```bash
# Tambahkan remote GitHub
git remote add origin https://github.com/[USERNAME]/[REPOSITORY-NAME].git

# Contoh:
# git remote add origin https://github.com/johndoe/Optimasi_Analisis_Faktor_Penentu_Kemenangan_Pertandingan_Bola_Voli.git

# Verifikasi remote telah ditambahkan
git remote -v
```

### 3️⃣ Push ke GitHub

```bash
# Push ke branch main
git push -u origin main
```

Jika menggunakan SSH (lebih aman dan tidak perlu password setiap kali):
```bash
git remote add origin git@github.com:[USERNAME]/[REPOSITORY-NAME].git
git push -u origin main
```

### 4️⃣ Verifikasi

1. Buka repository Anda di GitHub
2. Refresh halaman
3. Pastikan semua file telah terupload

---

## 🔐 Setup SSH Key (Opsional tapi Direkomendasikan)

### Generate SSH Key

```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your_email@example.com"

# Tekan Enter untuk menerima lokasi default
# Masukkan passphrase (optional)

# Start SSH agent
eval "$(ssh-agent -s)"

# Add SSH key to agent
ssh-add ~/.ssh/id_ed25519
```

### Tambahkan SSH Key ke GitHub

1. Copy SSH public key:
   ```bash
   # Windows (PowerShell)
   Get-Content ~/.ssh/id_ed25519.pub | Set-Clipboard
   
   # Linux/Mac
   cat ~/.ssh/id_ed25519.pub
   ```

2. Buka GitHub → **Settings** → **SSH and GPG keys** → **New SSH key**
3. Paste key dan beri title (e.g., "Laptop Research")
4. Klik **Add SSH key**

### Test SSH Connection

```bash
ssh -T git@github.com
```

Jika berhasil, akan muncul:
```
Hi [username]! You've successfully authenticated...
```

---

## 📋 Command Summary

```bash
# Setup awal (sudah dilakukan)
git init
git add .
git commit -m "Initial commit: Setup project structure and documentation"

# Hubungkan dengan GitHub (sesuaikan USERNAME dan REPO)
git remote add origin https://github.com/[USERNAME]/[REPO-NAME].git

# Push pertama kali
git push -u origin main

# Push selanjutnya (setelah ada perubahan)
git add .
git commit -m "Your commit message"
git push
```

---

## 🔄 Workflow untuk Update Selanjutnya

### Setiap Ada Perubahan:

```bash
# 1. Check status
git status

# 2. Add changes
git add .
# atau add file spesifik
git add path/to/file.py

# 3. Commit dengan pesan yang jelas
git commit -m "Add data preprocessing module"

# 4. Push ke GitHub
git push
```

### Contoh Commit Messages:

```bash
# Feature baru
git commit -m "Add exploratory data analysis notebook"
git commit -m "Implement XGBoost model training module"
git commit -m "Add SHAP analysis visualization"

# Bug fix
git commit -m "Fix missing value handling in preprocessing"
git commit -m "Fix feature scaling bug"

# Update dokumentasi
git commit -m "Update README with installation instructions"
git commit -m "Add methodology documentation"

# Eksperimen
git commit -m "Experiment: Test different hyperparameter ranges"
git commit -m "Results: Optuna optimization with 200 trials"
```

---

## 🏷️ Branching Strategy (Opsional)

Untuk pengembangan yang lebih terstruktur:

```bash
# Buat branch untuk development
git checkout -b development

# Buat branch untuk fitur spesifik
git checkout -b feature/data-preprocessing
git checkout -b feature/model-training
git checkout -b feature/shap-analysis

# Setelah selesai, merge ke main
git checkout main
git merge feature/data-preprocessing
git push
```

---

## 📊 GitHub Repository Settings (Recommended)

### 1. Tambahkan Description dan Topics

Di halaman repository → **About** (gear icon):
- Description: "Volleyball match outcome prediction using XGBoost and Optuna"
- Topics: `machine-learning`, `xgboost`, `optuna`, `sports-analytics`, `volleyball`, `shap`, `python`, `data-science`

### 2. Aktifkan GitHub Pages (Opsional)

Untuk dokumentasi online:
- Settings → Pages
- Source: Deploy from a branch
- Branch: main, folder: /docs atau root

### 3. Add Repository Badges

Tambahkan ke README.md:

```markdown
![Python](https://img.shields.io/badge/python-3.8+-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Status](https://img.shields.io/badge/status-active-success.svg)
```

---

## 🔒 File Sensitive (PENTING!)

**JANGAN COMMIT** file yang mengandung:
- API keys
- Passwords
- Personal information
- Large model files (>100MB)

Gunakan `.gitignore` yang sudah disediakan.

---

## 📝 Best Practices

1. **Commit Often**: Small, frequent commits lebih baik daripada satu commit besar
2. **Clear Messages**: Gunakan commit message yang deskriptif
3. **Test Before Commit**: Pastikan code berjalan sebelum commit
4. **Document Changes**: Update README jika ada perubahan signifikan
5. **Use .gitignore**: Jangan commit file yang tidak perlu

---

## ❓ Troubleshooting

### Error: "fatal: remote origin already exists"
```bash
git remote remove origin
git remote add origin [URL]
```

### Error: "Updates were rejected"
```bash
# Jika ingin overwrite (hati-hati!)
git push -f origin main

# Atau pull dulu
git pull origin main --allow-unrelated-histories
git push origin main
```

### Error: "Permission denied (publickey)"
- Setup SSH key (lihat bagian SSH Setup di atas)
- Atau gunakan HTTPS dengan personal access token

---

## 📞 Support

Jika ada masalah:
1. Cek [GitHub Docs](https://docs.github.com)
2. Cek [Git Documentation](https://git-scm.com/doc)
3. Search di Stack Overflow

---

**Created**: 7 Oktober 2026  
**Last Updated**: 7 Oktober 2026
