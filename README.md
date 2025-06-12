# Bengawan-Solo
Final Project Massive 
# ✨ Proyek Sistem Rekomendasi Tempat Wisata ✨

[![Python 3.x](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)](https://www.tensorflow.org/)
[![Keras](https://img.shields.io/badge/Keras-green)](https://keras.io/)
[![Pandas](https://img.shields.io/badge/Pandas-brightgreen)](https://pandas.pydata.org/)
[![Scikit-learn](https://img.shields.io/badge/scikit--learn-red)](https://scikit-learn.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

<br>

## 🚀 Teams

- Adyatma Kevin (Design Researcher)
- Keimaz Delan (Data Engineer)
- Fairah Almira (Data Engineer)
- Andhika Reihan H (Machine Learning Engineer)
- Handy Arfiano (Machine Learning Engineer)
- Farraheira (Scrum Master AI dan Machine Learning Ops)

Proyek ini mengembangkan sistem rekomendasi tempat wisata dengan pendekatan hybrid menggunakan kombinasi model Collaborative Filtering (berbasis NCF) dan Content-Based Filtering. Sistem ini dirancang untuk memberikan rekomendasi yang personalisasi baik untuk pengguna yang sudah memiliki riwayat interaksi maupun pengguna baru.

## 💡 Idea Background

### 1. Theme

**Tema: Personalisasi Pengalaman Pariwisata dan Rekomendasi Cerdas** 🗺️

Era digital telah mengubah cara orang mencari dan memilih destinasi wisata. Dengan semakin banyaknya pilihan tempat wisata yang tersedia, menemukan tempat yang benar-benar sesuai dengan minat dan preferensi individu menjadi tantangan tersendiri. Tema utama proyek ini adalah memanfaatkan data dan teknologi Machine Learning untuk menciptakan pengalaman pencarian dan penemuan tempat wisata yang lebih personal, relevan, dan efisien bagi pengguna. Ini mencakup pemahaman mendalam tentang apa yang disukai pengguna berdasarkan riwayat interaksi mereka, serta karakteristik unik dari setiap tempat wisata itu sendiri.

### 2. Problem

**Masalah: Overload Informasi dan Rekomendasi yang Tidak Relevan** 😔

Salah satu masalah utama yang dihadapi wisatawan modern adalah **overload informasi**. Ribuan tempat wisata, ulasan, artikel blog, dan iklan bersaing untuk menarik perhatian. Tanpa panduan yang efektif, pengguna bisa merasa kewalahan dan kesulitan menemukan 'permata tersembunyi' atau tempat yang paling cocok untuk mereka. Sistem rekomendasi tradisional yang hanya mengandalkan popularitas atau filter sederhana seringkali gagal menangkap nuansa preferensi individual. Ini mengakibatkan rekomendasi yang **tidak akurat atau kurang relevan**, membuang waktu pengguna dan berpotensi membuat mereka melewatkan pengalaman wisata yang ideal. Bagi pengguna baru tanpa riwayat interaksi, masalah 'dingin' (cold-start problem) juga menjadi tantangan besar dalam memberikan rekomendasi awal yang berarti.

### 3. Solution

**Solusi: Sistem Rekomendasi Hybrid Cerdas** 🧠✨

Untuk mengatasi masalah tersebut, kami mengusulkan dan membangun **Sistem Rekomendasi Hybrid Cerdas** menggunakan pendekatan Machine Learning. Solusi ini menggabungkan kekuatan dua metode rekomendasi utama:

*   **Collaborative Filtering (Berbasis NCF)**: Memanfaatkan pola interaksi (rating/ulasan) dari banyak pengguna untuk mengidentifikasi item yang disukai oleh pengguna dengan preferensi serupa. Ini membantu menangkap preferensi berdasarkan perilaku komunitas. Kami menggunakan Neural Collaborative Filtering (NCF) untuk pemodelan interaksi user-item yang lebih kompleks.
*   **Content-Based Filtering**: Menganalisis fitur-fitur intrinsik dari tempat wisata itu sendiri (seperti kategori, deskripsi, fasilitas, rating eksternal) untuk merekomendasikan item yang serupa dengan apa yang disukai pengguna di masa lalu atau yang sesuai dengan preferensi yang mereka berikan.

Dengan menggabungkan kedua pendekatan ini, model hybrid kami dapat memberikan rekomendasi yang lebih kaya dan akurat. Untuk pengguna yang sudah memiliki riwayat, model dapat memprediksi potensi minat mereka pada item baru. Untuk pengguna baru (cold-start), sistem dapat menggunakan fitur item dan informasi preferensi awal (misal: kategori yang disukai) untuk memberikan rekomendasi awal yang relevan, bahkan tanpa data interaksi sebelumnya. Kami juga mengintegrasikan data eksternal seperti rating Google Maps sebagai fitur tambahan untuk meningkatkan kualitas rekomendasi. Model ini dilatih dan dioptimalkan menggunakan TensorFlow/Keras dan KerasTuner untuk mencapai performa terbaik.

## 📂 Dataset
- Data Collection <br />
Kami mengumpulkan dataset sendiri. Untuk lebih detail nya dapat dilihat pada link github berikut ini:
https://github.com/KeimDel/my-data-projects/tree/main/recommendation-system-data-engineer

Poin soal dataset boleh ditambahkan sesuai kebutuhan.

## 🛠️ Algoritma dan Model

### 1. Framework

Kami menggunakan framework machine learning berikut:

-   **TensorFlow 2.x** 🔄: Platform end-to-end open source untuk machine learning.
-   **Keras** 🧠: API tingkat tinggi yang berjalan di atas TensorFlow, memudahkan pembangunan dan pelatihan model neural network.
-   **Pandas** 🐼: Untuk manipulasi dan analisis data.
-   **Scikit-learn** 📊: Untuk preprocessing data dan evaluasi metrik.
-   **Keras-Tuner** ⚙️: Untuk optimasi hyperparameter model Keras.

### 2. Pembangunan Model

Sistem rekomendasi ini menggunakan **Model Hybrid Neural Collaborative Filtering (NCF) dengan Feature Item Tambahan**.

Spesifikasi dan detail pelatihan model:

-   **Arsitektur Model**: Model Hybrid menggabungkan embeddings dari User dan Item (pendekatan Collaborative Filtering) dengan fitur-fitur deskriptif Item (seperti kategori, rating Google Maps, kategori umur) melalui jalur MLP terpisah, kemudian menggabungkannya untuk memprediksi rating yang dinormalisasi. Model menyertakan lapisan Batch Normalization dan Dropout untuk stabilisasi dan regularisasi, serta L2 Regularization pada embeddings dan Dense layer.
-   **Input Model**:
    -   `user_input`: ID User yang sudah di-encode (integer).
    -   `item_input`: ID Tempat Wisata yang sudah di-encode (integer).
    -   `features_input`: Fitur-fitur item yang sudah diproses (rating, kategori, umur), dinormalisasi.
-   **Output Model**: Prediksi rating yang dinormalisasi (nilai antara 0 dan 1).
-   **Fungsi Loss**: Mean Squared Error (MSE).
-   **Optimizer**: Adam.
-   **Metrik**: Mean Absolute Error (MAE).
-   **Hyperparameter Tuning**: Menggunakan KerasTuner (RandomSearch) untuk menemukan kombinasi hyperparameter terbaik (embedding_dim, mlp_units, dropout_rate, learning_rate, l2_reg_factor) berdasarkan `val_mae`.
-   **Pelatihan**:
    -   **Epochs**: Hingga 120 (dengan Early Stopping).
    -   **Batch Size**: 128.
    -   **Callbacks**: Early Stopping (monitor `val_mae`, patience 15, restore best weights).
    -   **Data Split**: 80% Training, 20% Testing.

Model terbaik dari proses tuning kemudian dilatih ulang dengan hyperparameter optimal pada data training dan dievaluasi pada data testing.

### 3. Rekomendasi

Sistem ini memiliki tiga skenario rekomendasi:

1.  **Untuk Pengguna yang Dikenal dengan Riwayat Review**: Menggunakan model NCF untuk memprediksi rating pada item yang belum dinilai, kemudian meningkatkan (boost) peringkat item kandidat teratas dengan skor kemiripan konten (Cosine Similarity) berdasarkan item-item yang disukai pengguna.
2.  **Untuk Pengguna Baru dengan Preferensi Kategori**: Menggunakan model NCF untuk menghitung 'daya tarik' rata-rata item (avg_ncf_appeal_score) dari perspektif sekelompok 'probe user' yang mewakili pola umum pengguna yang aktif, dikombinasikan dengan skor rating Google Maps. Hasil ini digabungkan dengan filter kategori yang dipilih pengguna.
3.  **Untuk Pengguna Baru Tanpa Riwayat/Probe (Fallback)**: Jika NCF Probe tidak memungkinkan, sistem akan memfilter item berdasarkan kategori yang dipilih pengguna dan mengurutkannya berdasarkan rating Google Maps dan jumlah ulasan.

### 4. Model Evaluation

Model terbaik dari proses tuning dievaluasi pada data testing untuk mengukur kinerjanya dalam memprediksi rating. Metrik utama yang digunakan adalah **Mean Absolute Error (MAE)** dan **Mean Squared Error (MSE)**.

Contoh hasil evaluasi model terbaik:
*(Catatan: Nilai aktual akan muncul saat kode dijalankan)*

MAE menunjukkan rata-rata selisih absolut antara rating yang diprediksi dan rating aktual, memberikan gambaran seberapa 'jauh' prediksi kita dari nilai sebenarnya dalam skala rating yang dinormalisasi (0-1). MSE memberikan bobot yang lebih besar pada kesalahan yang lebih besar.


