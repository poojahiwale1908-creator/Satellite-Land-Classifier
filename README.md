# Satellite-Land-Classifier
# 🛰️ Satellite Land Classifier

**Deep learning pipeline for classifying agricultural vs. non-agricultural land from satellite imagery using CNNs and Vision Transformers.**

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-2.11-EE4C2C?logo=pytorch&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.21-FF6F00?logo=tensorflow&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green.svg)

---

## 📖 About

An end-to-end deep learning system that analyzes satellite imagery and classifies each tile as **agricultural** or **non-agricultural** terrain. The project implements and benchmarks four model architectures across two deep learning frameworks, comparing accuracy, training speed, and deployment characteristics.

This enables automated, large-scale farmland detection — a capability relevant to agriculture analytics, supply chain planning, and geospatial intelligence.

---

## 🎯 What It Does

Given satellite image tiles, the pipeline:

1. **Loads and augments** imagery using memory-efficient sequential loading
2. **Trains multiple architectures** — CNNs and CNN-ViT hybrids
3. **Evaluates** each model with accuracy, precision, recall, F1, and ROC-AUC
4. **Compares frameworks** — Keras/TensorFlow vs. PyTorch on identical tasks
5. **Outputs** trained models ready for inference on new satellite data

---

## 🧠 Models

| Model | Framework | Architecture |
|-------|-----------|--------------|
| **CNN-Base** | Keras | 4 Conv2D blocks + 5 Dense layers |
| **CNN-Base** | PyTorch | 4 Conv2D blocks (with BatchNorm) + 3 FC layers |
| **CNN-ViT Hybrid** | Keras | Pretrained CNN backbone → Transformer encoder |
| **CNN-ViT Hybrid** | PyTorch | Custom CNN → patch embedding → ViT blocks |

**Why hybrid?** CNNs excel at local feature extraction (edges, textures, field patterns). ViTs capture global context via self-attention. Combining them yields strong performance on satellite imagery where both local texture and spatial layout matter.

---

## 📊 Dataset

- **Total**: 600 labeled satellite tiles
- **Classes**: `class_0_non_agri`, `class_1_agri` (300 each)
- **Resolution**: 64 × 64 RGB
- **Split**: 80% train / 20% validation

Organized in `ImageFolder`-compatible structure for direct use with `torchvision.datasets.ImageFolder` and `keras.preprocessing.image.ImageDataGenerator`.

---

## 📈 Results

### Summary

| Model | Accuracy | Precision | Recall | F1 | ROC-AUC |
|-------|----------|-----------|--------|-----|---------|
| Keras CNN | 1.000 | 1.000 | 1.000 | 1.000 | 1.000 |
| PyTorch CNN | 1.000 | 1.000 | 1.000 | 1.000 | 1.000 |
| Keras CNN-ViT | 0.500 | 0.000 | 0.000 | 0.000 | 1.000 |
| PyTorch CNN-ViT | 1.000 | 1.000 | 1.000 | 1.000 | 1.000 |

### Sample Images
![Sample Images](images/sample_images.png)

### Training Curves
![Keras Training](images/keras_training.png)
![PyTorch Training](images/pytorch_training.png)

### ROC Curves
![ROC Curves](images/roc_curves.png)

### Confusion Matrices
![Confusion Matrices](images/confusion_matrices.png)

---

## 🚀 Getting Started

### Prerequisites

- Python 3.10+
- CUDA-capable GPU (recommended)

### Installation

```bash
git clone https://github.com/YOUR_USERNAME/satellite-land-classifier.git
cd satellite-land-classifier

python -m venv venv
source venv/bin/activate       # Windows: venv\Scripts\activate

pip install -r requirements.txt
