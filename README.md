# Klasifikasi Citra: CNN from Scratch vs Transfer Learning (Kucing vs Anjing)

[cite_start]Repository ini dibuat untuk memenuhi tugas individu mata kuliah Pembelajaran Mesin (Machine Learning)[cite: 1]. [cite_start]Proyek ini 
membandingkan dua pendekatan Deep Learning untuk klasifikasi citra dua kelas (binary classification): membangun arsitektur CNN sendiri dari nol (*from scratch*)
dan memanfaatkan teknik *Transfer Learning* menggunakan *pretrained model*[cite: 4, 5, 8].

## Deskripsi Proyek
[cite_start]Eksperimen ini bertujuan untuk menganalisis dan membandingkan performa model berdasarkan aspek akurasi, waktu training, kestabilan, serta efisiensi komputasi[cite: 11, 19]:
1. [cite_start]**Model 1 (CNN from Scratch):** Menggunakan dataset CIFAR-10 (terfilter untuk 2 kelas) dengan arsitektur buatan sendiri[cite: 22, 38, 39].
2. [cite_start]**Model 2 (Transfer Learning):** Menggunakan dataset Cats vs Dogs dengan memanfaatkan model pintar **MobileNetV2** yang telah dilatih pada ImageNet (Strategi *Feature Extraction*)[cite: 23, 56, 60, 65].

## Struktur Repository
[cite_start]Sesuai dengan ketentuan tugas, berikut adalah struktur folder dari project ini[cite: 155, 156, 157]:

## Dataset & Pembagian Data
Kedua eksperimen menggunakan skala data minimal 200 gambar (100 gambar per kelas) [cite: 25, 26, 27] dengan proporsi pembagian data **70% Training, 15% Validation, dan 15% Testing**[cite: 33, 34, 35, 36]:
* **Dataset CNN From Scratch:** Berasal dari **CIFAR-10** (Kelas Kucing dan Anjing)[cite: 22].
  * *Link Sumber:* [CIFAR-10 Dataset](https://www.cs.toronto.edu/~kriz/cifar.html) [cite: 29]
* **Dataset Transfer Learning:** Menggunakan kombinasi gambar terbuka **Cats vs Dogs**[cite: 23].
  * *Link Sumber:* [Placedog](https://placedog.net/) & [Placebear](https://placebear.com/) [cite: 29]

## Ringkasan Arsitektur Model

### 1. CNN from Scratch [cite: 38]
* **Convolutional Layers:** 3 Lapisan `Conv2D` untuk ekstraksi fitur bertahap[cite: 40].
* **Pooling Layers:** `MaxPooling2D` untuk reduksi dimensi spasial[cite: 41].
* **Regularization:** `Dropout(0.5)` untuk meminimalkan risiko overfitting[cite: 53].
* **Output Layer:** 1 Unit `Dense` dengan aktivasi `Sigmoid` (Klasifikasi Biner)[cite: 42, 45].

### 2. Transfer Learning [cite: 55]
* **Base Model:** **MobileNetV2** (Pretrained on ImageNet)[cite: 56, 60].
* **Strategi:** *Feature Extraction* (Seluruh layer bawaan dibekukan/`trainable = False`)[cite: 65, 66].
* **Top Classifier:** `GlobalAveragePooling2D` -> `Dropout(0.2)` -> `Dense(1, Activation='Sigmoid')`[cite: 43, 45, 53].

## Cara Menjalankan Proyek

1. **Clone Repository ini:**
   ```bash
   git clone [https://github.com/USERNAME_KAMU/project-cnn-vs-transfer-learning.git](https://github.com/USERNAME_KAMU/project-cnn-vs-transfer-learning.git)
   cd project-cnn-vs-transfer-learning

```text
tensorflow>=2.0.0
numpy
matplotlib
scikit-learn
seaborn
requests
