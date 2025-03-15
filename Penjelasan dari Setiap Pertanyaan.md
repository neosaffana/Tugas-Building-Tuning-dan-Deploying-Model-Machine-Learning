# Tugas Building, Tuning, dan Deploying Model Machine Learning

Nama : Neo Saffana Farhalik

NIM : 4112322008

Prodi : Statistika Terapan dan Komputasi

## Dataset
Dataset berisi informasi mengenai pengajuan pinjaman oleh individu, dengan beberapa fitur :

Age : Usia pemohon

Income : Pendapatan pemohon

Education_Level : Tingkat pendidikan pemohon

Credit_Score : Skor kredit pemohon

Loan_Amount : Jumlah pinjaman yang diajukan

Loan_Purpose : Tujuan pinjaman

Loan_Approval : Label target (1 = Disetujui, 0 = Ditolak)


## Langkah-Langkah Analisis : 
### 1. Eksplorasi Data

1.1 Identifikasi apakah terdapat missing values dalam dataset.

Informasi Dataset :

- Terdiri dari 500 entri dan 7 kolom.

- Tidak ada missing values dalam dataset.

- Ada 5 fitur numerik (Age, Income, Credit_Score, Loan_Amount, Loan_Approval) dan 2 fitur kategorikal (Education_Level, Loan_Purpose).

1.2 Visualisasikan data tersebut

Grafik di kode menunjukkan distribusi variabel numerik dalam dataset. Berikut beberapa insight awal :

- Usia cenderung terdistribusi normal dengan puncak di sekitar usia 30-50 tahun.

- Pendapatan memiliki distribusi yang sedikit skewed ke kanan, menunjukkan ada beberapa individu dengan pendapatan sangat tinggi.

- Skor Kredit memiliki distribusi yang lebih merata dengan beberapa puncak.

- Jumlah Pinjaman juga memiliki distribusi skewed ke kanan, yang berarti mayoritas pinjaman bernilai lebih rendah.

### 2. Pemrosesan Data

2.1 Lakukan encoding pada fitur kategorikal

Education_Level dan Loan_Purpose telah diubah menjadi nilai numerik menggunakan Label Encoding.

2.2 Lakukan feature scaling pada fitur numerik

Fitur numerik (Age, Income, Credit_Score, Loan_Amount) telah dinormalisasi menggunakan StandardScaler agar memiliki distribusi dengan mean = 0 dan standar deviasi = 1.

2.3 Bagi dataset menjadi training set (80%) dan testing set (20%).

Membagi dataset menjadi training set 400 data (80%) dan testing set 100 data (20%).

### 3. Pemilihan dan Training Model

3.1 Pilih minimal dua algoritma Machine Learning yang berbeda. Jelaskan alasan
pemilihan tersebut.

Saya memilih dua algoritma Machine Learning yang berbeda untuk dibandingkan :

1. Random Forest Classifier

Algoritma berbasis pohon keputusan yang kuat terhadap outlier dan tidak memerlukan banyak preprocessing data.
Cocok untuk data dengan kombinasi fitur numerik dan kategorikal.

2. Logistic Regression

Model linear yang sederhana dan cepat untuk klasifikasi biner.
Cocok untuk memahami hubungan linier antara fitur dan target.

3.2 Lakukan training model menggunakan dataset yang telah diproses.

Hasil Training Model : 

1. Random Forest Classifier

Akurasi training : 100% (model kemungkinan overfitting).

2. Logistic Regression

Akurasi training : 59% (masih bisa ditingkatkan dengan tuning).

### 4. Evaluasi Model

4.1 Hitung dan bandingkan metric evaluasi dari kedua model yang dipilih.

Hasil Evaluasi Model : 

1. Random Forest Classifier

Accuracy : 57%

Precision : 60.2%

Recall : 83.3%

F1-Score : 69.9%

2. Logistic Regression

Accuracy : 58%

Precision : 59.4%

Recall : 95%

F1-Score : 73.1%

4.2 Pilih model dengan performa terbaik untuk tahap tuning.

Saya memilih model terbaik yaitu Logistic Regression untuk ke tahap tuning, karena : 

- Logistic Regression memiliki performa yang lebih baik berdasarkan Accuracy **(58%)** dan F1-Score **(73.1%)**.

- Recall Logistic Regression lebih tinggi **(95%)**, artinya model lebih baik dalam menangkap pengajuan yang disetujui.

- Random Forest mungkin mengalami overfitting, karena memiliki akurasi training 100% tetapi testing hanya **57%**. 

### 5. Tuning Model dengan Grid Search

5.1 Gunakan Grid Search atau Random Search untuk mencari kombinasi hyperparameter
terbaik.

Menggunakan Grid Search untuk mencari kombinasi hyperparameter terbaik.

5.2 Tampilkan kombinasi hyperparameter terbaik yang diperoleh.

Hyperparameter terbaik yang diperoleh untuk Logistic Regression :

C : 0.01

Solver : liblinear

LogisticRegression(C=0.01, max_iter=1000, random_state=42, solver='liblinear')

### 6. Perbandingan Performa Sebelum dan Sesudah Tuning

6.1 Bandingkan hasil evaluasi model sebelum dan sesudah tuning.

- Sebelum Tuning (Logistic Regression)

Accuracy : 58%

Precision : 59.4%

Recall : 95%

F1-Score : 73.1%

- Setelah Tuning (Logistic Regression dengan C=0.01, solver=liblinear)

Accuracy : 60%

Precision : 60%

Recall : 100%

F1-Score : 75%

6.2 Jelaskan apakah tuning berhasil meningkatkan performa model.

Tuning terbukti berhasil meningkatkan performa model, karena : 

• Setelah tuning, **Accuracy meningkat** dari **58%** ke **60%**.

• **Recall meningkat** menjadi **100%**, artinya model menangkap semua pengajuan yang disetujui.

• **F1-Score meningkat** dari **73.1%** ke **75%**, menunjukkan keseimbangan lebih baik antara Precision dan Recall.
