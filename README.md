# Data Mining – Kelompok 7  
**Implementasi Feature Selection dan PCA untuk Optimasi Model Klasifikasi pada Dataset Transaksi dan Dataset Gelombang**

Proyek ini mengimplementasikan teknik *preprocessing*, *feature selecetion*, dan *evaluasi model* berbasis metode yang umum digunakan dalam penelitian Data Mining. Dua dataset berbeda digunakan: data transaksi stok tahun 2021 dan data gelombang laut. Model diuji sebelum dan sesudah dilakukan *feature selection* serta *PCA* untuk melihat peningkatan performa.

---

## 👥 Anggota Kelompok  
Kelompok 7 – Data Mining  
1. Femmy Aprillia Putri  - 122140006
2. Kayla Chika Lathisya  - 122140009
3. Yohanna Anzelika Sitepu  - 122140010
4. Nasya Aulia Efendi  - 122140016

---

## 📁 Dataset  
Terdapat **dua dataset utama** yang diekstrak dari file ZIP:

### **1. Dataset Transaksi (2021.csv)**  
Berisi data keluar–masuk barang gudang selama tahun 2021.  
Target prediksi:
- `TIPE_TRANSAKSI`  
  - `1` → Barang Masuk (QTY_MSK > 0)  
  - `0` → Barang Keluar (QTY_KLR > 0)

### **2. Dataset Gelombang (Gelombang (1).xlsx)**  
Berisi data pengukuran tinggi gelombang laut.  
Target prediksi:
- `WAVE_CLASS`  
  - `1` → Gelombang tinggi di atas median  
  - `0` → Gelombang rendah di bawah atau sama dengan median  

---

## 🔧 Teknologi & Library  
Script menggunakan Python dengan library berikut:

- pandas  
- numpy  
- scikit-learn  
- Pipeline, ColumnTransformer  
- OneHotEncoder, StandardScaler  
- DecisionTreeClassifier  
- RandomForestClassifier  
- SelectFromModel (Feature Selection)  
- PCA (Principal Component Analysis)  
- train_test_split  
- accuracy_score, classification_report  

---

## ⚙️ Alur Proses

### **1. Ekstraksi ZIP Dataset**
Dataset diekstrak dari Google Drive ke folder `/content/dataset_tubes`.

### **2. Load Dataset**
- `2021.csv` dibaca dengan `pandas.read_csv`
- `Gelombang (1).xlsx` dibaca dengan `pandas.read_excel` menggunakan header tertentu (baris ke-4)

### **3. Preprocessing Dataset Transaksi**
- Menentukan target `TIPE_TRANSAKSI`  
  ```python
  df1['TIPE_TRANSAKSI'] = np.where(df1['QTY_MSK'] > 0, 1, 0)

## 4. Preprocessing Dataset Gelombang
- Mencari kolom **Hsig** (tinggi signifikan gelombang)  
- Membersihkan nilai **NaN**  
- Menghitung **median Hsig**  
- Membuat target **WAVE_CLASS**  
  - `1` → Gelombang tinggi  
  - `0` → Gelombang rendah  

---

## 5. Train–Test Split
- 80% data digunakan sebagai **training**  
- 20% data digunakan sebagai **testing**  
- Menggunakan **stratified split** untuk menjaga distribusi kelas  

---

## 6. Eksperimen Model
Untuk setiap dataset, model berikut dijalankan:

### a. Baseline Model
- Pipeline: **Preprocessing + Decision Tree**

### b. Feature Selection
- **Random Forest** → `SelectFromModel`  
- Dilanjutkan model **Decision Tree** sebagai classifier  

### c. PCA Only
- Menggunakan **PCA** dengan 5 komponen utama

### d. FS + PCA
- `SelectFromModel` (Random Forest) → **PCA** → Decision Tree  

---

## 📈 Hasil Evaluasi
Script menghasilkan tabel ringkasan akurasi model.

### Metode yang diuji:
- Baseline  
- Feature Selection  
- PCA Only  
- Feature Selection + PCA  

### Output akhir:
**Tabel Evaluasi Sebelum vs Sesudah Preprocessing (Metode Jurnal)**  
Dengan kolom berikut:
- Metode  
- Dataset 1 Accuracy  
- Dataset 2 Accuracy  

---

## ▶️ Cara Menjalankan Script
1. Upload file ZIP dataset ke Google Drive  
2. Sesuaikan path ZIP pada variabel `zip_path` di script  
3. Jalankan seluruh script `.py` atau notebook `.ipynb`  
4. Model otomatis dijalankan dan tabel akurasi tampil pada akhir proses  

---

## 📦 File Script
Script utama proyek ini:
- `datmin_kelompok_7.py`  
  Berisi seluruh pipeline: ekstraksi, preprocessing, pemodelan, dan evaluasi.  

---

## 📝 Lisensi
Proyek ini dibuat sebagai tugas akhir mata kuliah **Data Mining**.

---

## 🙌 Penutup
Proyek ini menunjukkan bagaimana *feature engineering* seperti **Feature Selection** dan **PCA** dapat meningkatkan performa model klasifikasi pada dataset dengan karakteristik yang berbeda. Pendekatan ini dapat dikembangkan lebih lanjut menggunakan model lain seperti **SVM**, **XGBoost**, atau **Deep Learning** untuk eksplorasi performa yang lebih tinggi.


