Siap ✅ Berikut ini adalah versi akhir **`README.md`** dalam format Markdown yang **siap langsung kamu upload ke GitHub**.
Versi ini sudah profesional, lengkap, dan disusun agar tampil rapi di tampilan GitHub — termasuk badge, tabel hasil, diagram pipeline, dan metadata penulis.

---

````markdown
# 🧠 Brain Tumor Detection Using Deep Features Concatenation

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.15+-orange.svg)](https://www.tensorflow.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yourusername/brain-tumor-detection)

> Replikasi dan implementasi paper IEEE Access:  
> **"Brain Tumor Detection Based on Deep Features Concatenation and Machine Learning Classifiers With Genetic Selection"**  
> oleh **Mohamed Wageh et al. (2024), IEEE Access Vol. 12, DOI: 10.1109/ACCESS.2024.3446190**

---

## 📋 Deskripsi

Proyek ini mereplikasi penelitian **deteksi dini tumor otak berbasis MRI** menggunakan pendekatan **hybrid deep learning + machine learning**.  
Pendekatan ini menggabungkan **deep features dari beberapa CNN (VGG-16, Inception V3, ResNet-101, DenseNet-201)** yang digabungkan melalui **feature concatenation**, diseleksi menggunakan **Genetic Algorithm**, lalu diklasifikasikan dengan **SVM, Random Forest, Decision Tree, dan XGBoost**.

### 🎯 Tujuan
Meningkatkan akurasi deteksi tumor otak menggunakan kombinasi fitur mendalam (deep features) dari berbagai arsitektur CNN serta optimasi seleksi fitur berbasis algoritma genetika.

## ⚙️ Metodologi

### 🧪 1. Preprocessing

* **Cropping:** Menghapus area tidak relevan.
* **Resizing:**

  * 224×224 px → VGG16, ResNet101, DenseNet201
  * 299×299 px → InceptionV3
* **Augmentation:** Flipping, rotation (−20°–20°), shifting (±20 px).
* **Filtering:** Median filter untuk reduksi noise.

### 🧬 2. Feature Extraction (Transfer Learning)

Empat model CNN pra-latih digunakan sebagai *feature extractor*:

| Model        | Input Size | Output Features | Pre-trained Weight |
| ------------ | ---------- | --------------- | ------------------ |
| VGG-16       | 224×224×3  | 512             | ImageNet           |
| Inception V3 | 299×299×3  | 2048            | ImageNet           |
| ResNet-101   | 224×224×3  | 2048            | ImageNet           |
| DenseNet-201 | 224×224×3  | 1920            | ImageNet           |

### 🔗 3. Feature Concatenation

Tiga level penggabungan fitur diuji:

1. **VGG-16 + InceptionV3 → 2,560 fitur**
2. **VGG-16 + InceptionV3 + ResNet101 → 4,608 fitur**
3. **VGG-16 + InceptionV3 + ResNet101 + DenseNet201 → 6,528 fitur**

### 🧠 4. Feature Selection

Menggunakan **Genetic Algorithm (GA)** untuk memilih ±500 fitur terbaik berdasarkan *fitness score* tertinggi.
Tujuannya meningkatkan efisiensi komputasi dan akurasi klasifikasi.

### 🤖 5. Machine Learning Classifiers

Empat model digunakan untuk klasifikasi akhir:

* Support Vector Machine (**SVM**)
* Random Forest (**RF**)
* Decision Tree (**DT**)
* Extreme Gradient Boosting (**XGB**)

---

## 📊 Dataset

| Dataset        | Total Gambar | Tumor | Non-Tumor | Sumber                                                                                                                            |
| -------------- | ------------ | ----- | --------- | --------------------------------------------------------------------------------------------------------------------------------- |
| **Dataset I**  | 253          | 155   | 98        | [Brain MRI Images for Brain Tumor Detection](https://www.kaggle.com/datasets/navoneel/brain-mri-images-for-brain-tumor-detection) |
| **Dataset II** | 3000         | 1500  | 1500      | [Br35H - Brain Tumor Detection 2020](https://www.kaggle.com/datasets/ahmedhamada0/brain-tumor-detection)                          |

---

## 📈 Hasil Eksperimen

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

### Instalasi

```bash
# Clone repository
git clone https://github.com/nonUser00/Brain-Tumor-Detection.git
cd brain-tumor-detection

### Setup Kaggle API

Buat file `.env` di root folder dan isi dengan:

```
KAGGLE_USERNAME=your_kaggle_username
KAGGLE_KEY=your_kaggle_api_key
```

---

## 📁 Struktur Proyek

```
brain-tumor-detection/
├── data/                  
├── models/ 
├── notebooks/
│   ├── feature_extraction.ipynb
│   ├── concatenation_genetic.ipynb
│   └── classification.ipynb
├── results/
│   ├── confusion_matrices/
│   └── metrics_summary.csv
├── utils/
│   ├── preprocessing.py
│   ├── genetic_selection.py
│   └── visualization.py
├── requirements.txt
└── README.md
```

---

## 🧪 Visualisasi Hasil

| Tahapan                | Visualisasi                                              |
| ---------------------- | -------------------------------------------------------- |
| **Preprocessing**      | ![Preprocessing Sample](assets/sample_preprocessing.png) |
| **Feature Extraction** | ![Feature Map](assets/feature_map.png)                   |
| **Confusion Matrix**   | ![Confusion Matrix](assets/confusion_matrix.png)         |

> *Note: Contoh gambar dapat diganti sesuai hasil eksperimenmu di folder `results/`.*

---

## 📚 Referensi

> Wageh, M., Amin, K., Algarni, A. D., Hamad, A. M., & Ibrahim, M. (2024).
> *Brain Tumor Detection Based on Deep Features Concatenation and Machine Learning Classifiers With Genetic Selection.*
> **IEEE Access, Vol. 12**, 114923–114939.
> DOI: [10.1109/ACCESS.2024.3446190](https://doi.org/10.1109/ACCESS.2024.3446190)

---

## 👤 Author

**Yuka Wardana**
Universitas Dian Nuswantoro (UDINUS), Semarang
📧 [p31202502659@mhs.dinus.ac.id](mailto:p31202502659@mhs.dinus.ac.id)
💻 [GitHub](https://github.com/nonUser00)

---

## 🧾 License

This project is licensed under the [MIT License](LICENSE).
