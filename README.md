# 🧠 Brain Tumor Detection Using Deep Features Concatenation

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.15+-orange.svg)](https://www.tensorflow.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yourusername/brain-tumor-detection)

> Replikasi dan implementasi paper IEEE Access:  
> **Judul Paper:** Brain Tumor Detection Based on Deep Features Concatenation and Machine Learning Classifiers With Genetic Selection
> **Penulis:** Mohamed Wageh, Khalid Amin, Abeer D. Algarni, Ahmed M. Hamad, dan Mina Ibrahim
> **Publikasi:** IEEE Access, Vol. 12, 2024
> **DOI:** [10.1109/ACCESS.2024.3446190](https://ieeexplore.ieee.org/document/10639386)

---

## 📋 Deskripsi

Proyek ini mereplikasi penelitian **deteksi dini tumor otak berbasis MRI** menggunakan pendekatan **hybrid deep learning + machine learning**.  
Pendekatan ini menggabungkan **deep features dari beberapa CNN (VGG-16, Inception V3, ResNet-101, DenseNet-201)** yang digabungkan melalui **feature concatenation**, diseleksi menggunakan **Genetic Algorithm**, lalu diklasifikasikan dengan **SVM, Random Forest, Decision Tree, dan XGBoost**.

### 🎯 Tujuan
Meningkatkan akurasi deteksi tumor otak menggunakan kombinasi fitur mendalam (deep features) dari berbagai arsitektur CNN serta optimasi seleksi fitur berbasis algoritma genetika.

## ⚙️ Metodologi
### 🧪 Preprocessing
Citra MRI diproses melalui **cropping** untuk menghapus area tidak relevan, **resizing** (224×224 untuk VGG/ResNet/DenseNet, 299×299 untuk InceptionV3), serta **augmentasi** berupa rotasi, flipping, dan shifting guna memperbanyak variasi data.  
Noise dihilangkan menggunakan **median filter** agar citra lebih bersih.

---

### 🧬 Feature Extraction (Transfer Learning)
Empat model CNN pra-latih dari **ImageNet** digunakan untuk mengekstraksi *deep features* dari citra MRI:

| Model | Input | Output Features |
|--------|--------|----------------|
| VGG-16 | 224×224×3 | 512 |
| Inception V3 | 299×299×3 | 2048 |
| ResNet-101 | 224×224×3 | 2048 |
| DenseNet-201 | 224×224×3 | 1920 |

---

### 🔗 Feature Concatenation
Fitur dari beberapa CNN digabung untuk memperkaya representasi:
1. VGG16 + InceptionV3 → **2,560 fitur**  
2. ResNet101 → **4,608 fitur**  
3. DenseNet201 → **6,528 fitur**

---

### 🧠 Feature Selection
**Genetic Algorithm (GA)** digunakan untuk menyeleksi ±500 fitur paling informatif dari hasil concatenation, meningkatkan efisiensi dan akurasi klasifikasi.

---

### 🤖 Machine Learning Classifiers
Empat algoritma diuji untuk klasifikasi akhir:
**SVM**, **Random Forest**, **Decision Tree**, dan **XGBoost**,  
dengan input berupa fitur hasil seleksi GA.


## 📊 Dataset yang digunakan

| Dataset        | Total Gambar | Tumor | Non-Tumor | Sumber                                                                                                                            |
| -------------- | ------------ | ----- | --------- | --------------------------------------------------------------------------------------------------------------------------------- |
| **Dataset I**  | 253          | 155   | 98        | [Brain MRI Images for Brain Tumor Detection](https://www.kaggle.com/datasets/navoneel/brain-mri-images-for-brain-tumor-detection) |
| **Dataset II** | 3000         | 1500  | 1500      | [Br35H - Brain Tumor Detection 2020](https://www.kaggle.com/datasets/ahmedhamada0/brain-tumor-detection)                          |

---

## 📈 Hasil dari Paper

### Dataset I – Brain MRI Images (Navoneel)

| Model             | Accuracy   | Precision | Recall | F1-Score |
| ----------------- | ---------- | --------- | ------ | -------- |
| **SVM**           | **99.74%** | 99.72     | 99.74  | 99.73    |
| **Decision Tree** | **99.74%** | 99.72     | 99.74  | 99.73    |
| Random Forest     | 98.76      | 98.74     | 98.76  | 98.75    |
| XGBoost           | 98.47      | 98.45     | 98.47  | 98.46    |

### Dataset II – Br35H Brain Tumor Detection

| Model             | Accuracy   | Precision | Recall | F1-Score |
| ----------------- | ---------- | --------- | ------ | -------- |
| **Decision Tree** | **99.87%** | 99.86     | 99.87  | 99.87    |
| SVM               | 99.57      | 99.56     | 99.57  | 99.57    |
| Random Forest     | 99.13      | 99.12     | 99.13  | 99.13    |
| XGBoost           | 99.10      | 99.09     | 99.10  | 99.10    |

📌 **Model terbaik:**
* Dataset I → SVM / Decision Tree (99.74%)
* Dataset II → Decision Tree (99.87%)

---

## 🚀 Quick Start

### Prerequisites
* Google Colab
* Kaggle API (untuk download dataset)

### Clone repository
`git clone https://github.com/nonUser00/Brain-Tumor-Detection.git`
`cd brain-tumor-detection`

### Setup Kaggle API
Buat file `.env` di root folder dan isi dengan:
KAGGLE_USERNAME=your_kaggle_username
KAGGLE_KEY=your_kaggle_api_key


## 📚 Referensi
> Wageh, M., Amin, K., Algarni, A. D., Hamad, A. M., & Ibrahim, M. (2024).
> *Brain Tumor Detection Based on Deep Features Concatenation and Machine Learning Classifiers With Genetic Selection.*
> **IEEE Access, Vol. 12**, 114923–114939.
> DOI: [10.1109/ACCESS.2024.3446190](https://doi.org/10.1109/ACCESS.2024.3446190)

---

## 👤 Author
**Yuka Wardana**
📧 [yukawardana587@gmail.com](mailto:yukawardana587@gmail.com)  
💻 [GitHub](https://github.com/nonUser00)


