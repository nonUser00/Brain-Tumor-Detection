# 🧠 Brain Tumor Detection Using Deep Features Concatenation

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.15+-orange.svg)](https://www.tensorflow.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/nonUser00/Brain-Tumor-Detection)

> 🔬 **IEEE Access Paper Replication**  
> **Title:** Brain Tumor Detection Based on Deep Features Concatenation and Machine Learning Classifiers With Genetic Selection  
> **Authors:** Mohamed Wageh, Khalid Amin, Abeer D. Algarni, Ahmed M. Hamad, and Mina Ibrahim  
> **Publication:** IEEE Access, Vol. 12, 2024  
> **DOI:** [10.1109/ACCESS.2024.3446190](https://ieeexplore.ieee.org/document/10639386)

---

## 📖 Overview

This project replicates a state-of-the-art **MRI-based brain tumor detection** research using a **hybrid deep learning and machine learning approach**. The methodology combines **deep features from multiple CNNs** (VGG-16, Inception V3, ResNet-101, DenseNet-201) through **feature concatenation**, optimizes feature selection using **Genetic Algorithm**, and performs classification with **SVM, Random Forest, Decision Tree, and XGBoost**.

### 🎯 Objectives

- Enhance brain tumor detection accuracy using combined deep features from various CNN architectures
- Optimize feature selection through genetic algorithm-based approach
- Implement and evaluate multiple machine learning classifiers for robust tumor detection
- Provide reproducible implementation of the IEEE Access paper methodology

---

## 🔬 Methodology

### 1️⃣ Preprocessing Pipeline

MRI images undergo comprehensive preprocessing to improve quality and model performance:

- **Cropping:** Remove irrelevant regions from MRI scans
- **Resizing:** Standardize image dimensions
  - 224×224 pixels for VGG-16, ResNet-101, DenseNet-201
  - 299×299 pixels for Inception V3
- **Data Augmentation:** Enhance dataset diversity through:
  - Rotation (±20°)
  - Horizontal/vertical flipping
  - Position shifting (±20px)
- **Noise Reduction:** Apply 5×5 median filter for cleaner images

### 2️⃣ Feature Extraction (Transfer Learning)

Four pre-trained CNN models extract deep features from MRI images using ImageNet weights:

| Model | Input Size | Output Features | Pre-trained Weights |
|-------|------------|-----------------|---------------------|
| **VGG-16** | 224×224×3 | 512 | ImageNet |
| **Inception V3** | 299×299×3 | 2,048 | ImageNet |
| **ResNet-101** | 224×224×3 | 2,048 | ImageNet |
| **DenseNet-201** | 224×224×3 | 1,920 | ImageNet |

### 3️⃣ Feature Concatenation Strategy

Three concatenation scenarios combine features from multiple CNNs to enrich feature representation:

1. **VGG-16 + Inception V3** → 2,560 features
2. **VGG-16 + Inception V3 + ResNet-101** → 4,608 features
3. **VGG-16 + Inception V3 + ResNet-101 + DenseNet-201** → 6,528 features

### 4️⃣ Feature Selection

**Genetic Algorithm (GA)** selects approximately 500 most informative features from concatenated feature vectors, improving:
- Classification efficiency
- Model accuracy
- Computational performance

### 5️⃣ Machine Learning Classification

Four classifiers evaluate the selected features:

- **Support Vector Machine (SVM)**
- **Random Forest (RF)**
- **Decision Tree (DT)**
- **XGBoost (XGB)**

---

## 📊 Datasets

| Dataset | Total Images | Tumor | Non-Tumor | Source |
|---------|--------------|-------|-----------|--------|
| **Dataset I** | 253 | 155 | 98 | [Brain MRI Images for Brain Tumor Detection](https://www.kaggle.com/datasets/navoneel/brain-mri-images-for-brain-tumor-detection) |
| **Dataset II** | 3,000 | 1,500 | 1,500 | [Br35H - Brain Tumor Detection 2020](https://www.kaggle.com/datasets/ahmedhamada0/brain-tumor-detection) |

---

## 📈 Results from Original Paper

### Dataset I – Brain MRI Images (Navoneel)

| Model | Accuracy | Precision | Recall | F1-Score |
|-------|----------|-----------|--------|----------|
| **SVM** ⭐ | **99.74%** | 99.72 | 99.74 | 99.73 |
| **Decision Tree** ⭐ | **99.74%** | 99.72 | 99.74 | 99.73 |
| Random Forest | 98.76% | 98.74 | 98.76 | 98.75 |
| XGBoost | 98.47% | 98.45 | 98.47 | 98.46 |

### Dataset II – Br35H Brain Tumor Detection

| Model | Accuracy | Precision | Recall | F1-Score |
|-------|----------|-----------|--------|----------|
| **Decision Tree** ⭐ | **99.87%** | 99.86 | 99.87 | 99.87 |
| SVM | 99.57% | 99.56 | 99.57 | 99.57 |
| Random Forest | 99.13% | 99.12 | 99.13 | 99.13 |
| XGBoost | 99.10% | 99.09 | 99.10 | 99.10 |

### 🏆 Key Findings

- **Dataset I:** SVM and Decision Tree achieved the highest accuracy (99.74%)
- **Dataset II:** Decision Tree achieved the highest accuracy (99.87%)
- **Feature concatenation + genetic selection** significantly improves performance over single-model approaches

---

## 🚀 Quick Start

### Prerequisites

- Python 3.10 or higher
- Google Colab (recommended)
- Kaggle API credentials

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/nonUser00/Brain-Tumor-Detection.git
   cd Brain-Tumor-Detection
   ```

2. **Setup Kaggle API**
   
   Create a `.env` file in the root directory:
   ```env
   KAGGLE_USERNAME=your_kaggle_username
   KAGGLE_KEY=your_kaggle_api_key
   ```

3. **Run in Google Colab**
   
   Click the Colab badge at the top of this README to open the notebook directly in Google Colab.

---

## 📁 Project Structure

```
Brain-Tumor-Detection/
├── notebooks/          # Jupyter/Colab notebooks
├── data/              # Dataset directory
├── models/            # Saved models
├── utils/             # Helper functions
├── results/           # Experiment results
├── .env              # Kaggle API credentials
├── requirements.txt  # Python dependencies
└── README.md         # Project documentation
```

---

## 🔑 Key Features

- ✅ Complete implementation of IEEE Access paper methodology
- ✅ Multiple pre-trained CNN models for feature extraction
- ✅ Genetic algorithm-based feature selection
- ✅ Comprehensive evaluation with four ML classifiers
- ✅ Reproducible results with detailed documentation
- ✅ Easy-to-use Google Colab notebooks

---

## 📚 Citation

If you use this implementation in your research, please cite the original paper:

```bibtex
@article{wageh2024brain,
  title={Brain Tumor Detection Based on Deep Features Concatenation and Machine Learning Classifiers With Genetic Selection},
  author={Wageh, Mohamed and Amin, Khalid and Algarni, Abeer D and Hamad, Ahmed M and Ibrahim, Mina},
  journal={IEEE Access},
  volume={12},
  pages={114923--114939},
  year={2024},
  publisher={IEEE},
  doi={10.1109/ACCESS.2024.3446190}
}
```

---

## 👨‍💻 Author

**Yuka Wardana**  
📧 Email: [yukawardana587@gmail.com](mailto:yukawardana587@gmail.com)  
🎓 Student ID: P31.2025.02659  
🏛️ Universitas Dian Nuswantoro (UDINUS) Semarang  
💻 GitHub: [@nonUser00](https://github.com/nonUser00)

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- Original paper authors for their groundbreaking research
- Kaggle for providing open-access medical imaging datasets
- TensorFlow and scikit-learn communities for excellent ML tools

---

<div align="center">
  
**⭐ If you find this project helpful, please consider giving it a star!**

Made with ❤️ for advancing medical imaging research

</div>
