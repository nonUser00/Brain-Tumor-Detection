# Brain Tumor Detection Using Deep Features Concatenation

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.15+-orange.svg)](https://www.tensorflow.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yourusername/brain-tumor-detection)

Replikasi dan implementasi paper IEEE Access: **"Brain Tumor Detection Based on Deep Features Concatenation and Machine Learning Classifiers With Genetic Selection"** oleh Mohamed Wageh et al. (2024).

## 📋 Deskripsi

Proyek ini merupakan implementasi deep learning untuk deteksi tumor otak menggunakan MRI scan dengan pendekatan **feature concatenation** dari multiple pre-trained CNN models (VGG-16, Inception V3, ResNet-101) dan machine learning classifiers.

### Highlights
- 🧠 Binary classification (Tumor vs Non-Tumor)
- 🔗 Feature concatenation dari 3 pre-trained CNN models
- 🧬 Genetic Algorithm untuk feature selection
- 📊 4 machine learning classifiers (SVM, Random Forest, Decision Tree, XGBoost)
- 🎯 Akurasi: **91.13%** (Dataset 1)

## 🚀 Quick Start

### Prerequisites
- Google Colab
- Akun Kaggle (untuk download dataset)

### 1. Clone Repository
git clone https://github.com/yourusername/brain-tumor-detection.git
cd brain-tumor-detection

### 2. Setup Kaggle API Credentials

1. **Buat file `.env`** di root directory project:
touch .env

2. **Isi file `.env`** dengan kredensial Kaggle:
KAGGLE_USERNAME=your_kaggle_username
KAGGLE_KEY=your_kaggle_api_key

3. **Cara mendapatkan Kaggle API Key:**
- Login ke [Kaggle.com](https://www.kaggle.com)
- Klik profil Anda → **Account**
- Scroll ke bagian **API** → Klik **Create New API Token**
- File `kaggle.json` akan ter-download
- Buka file tersebut, copy `username` dan `key`
- Paste ke file `.env`

## 📊 Dataset
Proyek ini menggunakan 2 dataset publik dari Kaggle:

### Dataset 1: Navoneel Brain Tumor Dataset
- **Link:** [kaggle.com/navoneel/brain-mri-images-for-brain-tumor-detection](https://www.kaggle.com/datasets/navoneel/brain-mri-images-for-brain-tumor-detection)
- **Total:** 253 images
- **Kelas:** Tumor (155), Non-tumor (98)

### Dataset 2: Br35H Brain Tumor Detection Dataset
- **Link:** [kaggle.com/ahmedhamada0/brain-tumor-detection](https://www.kaggle.com/datasets/ahmedhamada0/brain-tumor-detection)
- **Total:** 3000 images
- **Kelas:** Tumor (1500), Non-tumor (1500)

## 📚 Reference
Wageh, M. et al. (2024). Brain Tumor Detection Based on Deep Features Concatenation and Machine Learning Classifiers With Genetic Selection. IEEE Access, 12, 114923-114939

##👤 Author
nonuser - yuka
