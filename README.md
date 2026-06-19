# Klasifikasi Citra: CNN from Scratch vs Transfer Learning (Kucing vs Anjing)

[cite_start]Repository ini dibuat untuk memenuhi tugas individu mata kuliah Pembelajaran Mesin (Machine Learning)[cite: 1]. [cite_start]Proyek ini membandingkan dua pendekatan Deep Learning untuk klasifikasi citra dua kelas (binary classification): membangun arsitektur CNN sendiri dari nol (*from scratch*) dan memanfaatkan teknik *Transfer Learning* menggunakan *pretrained model*[cite: 4, 5, 8].

##Deskripsi Proyek
[cite_start]Eksperimen ini bertujuan untuk menganalisis dan membandingkan performa model berdasarkan aspek akurasi, waktu training, kestabilan, serta efisiensi komputasi[cite: 11, 16, 19]:
1. [cite_start]**Model 1 (CNN from Scratch):** Menggunakan dataset CIFAR-10 (terfilter untuk 2 kelas) dengan arsitektur buatan sendiri[cite: 22, 39].
2. [cite_start]**Model 2 (Transfer Learning):** Menggunakan dataset Cats vs Dogs dengan memanfaatkan model pintar **MobileNetV2** yang telah dilatih pada ImageNet (Strategi *Feature Extraction*)[cite: 23, 60, 65, 111].

## Struktur Repository
[cite_start]Sesuai dengan ketentuan tugas, berikut adalah struktur folder dari project ini[cite: 157, 158, 159, 161, 163, 164]:

project-cnn-vs-transfer-learning/
│
├── dataset/
│   └── link_dataset.txt
│
├── notebook/
│   └── cnn_vs_transfer_learning.ipynb
│
├── report/
│   └── laporan.pdf
│
├── README.md
└── requirements.txt

## Dataset & Pembagian Data
Kedua eksperimen menggunakan skala data minimal 200 gambar (100 gambar per kelas) dengan proporsi pembagian data **70% Training, 15% Validation, dan 15% Testing**[cite: 25, 26, 27, 34, 35, 36]:
* **Dataset CNN From Scratch:** Berasal dari **CIFAR-10** (Kelas Kucing dan Anjing)[cite: 22].
  * *Link Sumber:* [CIFAR-10 Dataset](https://www.cs.toronto.edu/~kriz/cifar.html)
* **Dataset Transfer Learning:** Menggunakan kombinasi gambar terbuka **Cats vs Dogs**[cite: 23].
  * *Link Sumber:* [Placedog](https://placedog.net/) & [Placebear](https://placebear.com/)

## Ringkasan Arsitektur Model

### 1. CNN from Scratch
* **Convolutional Layers:** 3 Lapisan `Conv2D` untuk ekstraksi fitur bertahap[cite: 40].
* **Pooling Layers:** `MaxPooling2D` untuk reduksi dimensi spasial[cite: 41].
* **Regularization:** `Dropout(0.5)` untuk meminimalkan risiko overfitting[cite: 53].
* **Output Layer:** 1 Unit `Dense` dengan aktivasi `Sigmoid` (Klasifikasi Biner)[cite: 44, 45].

### 2. Transfer Learning
* **Base Model:** **MobileNetV2** (Pretrained on ImageNet)[cite: 60].
* **Strategi:** *Feature Extraction* (Seluruh layer bawaan dibekukan/`trainable = False`)[cite: 65].
* **Top Classifier:** `GlobalAveragePooling2D` -> `Dropout(0.2)` -> `Dense(1, Activation='Sigmoid')`[cite: 43, 45].

## Cara Menjalankan Proyek

1. **Clone Repository ini:**
   ```bash
   git clone [https://github.com/muhammad-alif-huda/MuhammadAlifHuda_MachineLearning_CNN_vs_TransferLearning_untuk_KlasifikasiCitra.git](https://github.com/muhammad-alif-huda/MuhammadAlifHuda_MachineLearning_CNN_vs_TransferLearning_untuk_KlasifikasiCitra.git)
   cd MuhammadAlifHuda_MachineLearning_CNN_vs_TransferLearning_untuk_KlasifikasiCitra

   Pastikan sudah mengunduh library yang diperlukan melalui file requirements.txt:
   pip install -r requirements.txt

   Buka Notebook:
Jalankan file notebook/cnn_vs_transfer_learning.ipynb di Google Colab atau Jupyter Notebook. Jalankan setiap cell secara berurutan untuk mengunduh data, melatih model, dan melihat visualisasi grafik evaluasi.

