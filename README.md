# 🎵 Vision Transformer (ViT) for Music Genre Classification

This project explores how well a **Vision Transformer (ViT)** can classify music genres when given visual representations of audio — specifically, **Mel-Spectrograms** and **MFCCs**. We use the well-known **GTZAN dataset** and feed it to a pre-trained ViT model after transforming audio signals into images.

---

## 📁 Dataset: GTZAN

The GTZAN dataset contains:

- **1000 audio tracks**, each 30 seconds long
- **10 music genres**:
  - Blues
  - Classical
  - Country
  - Disco
  - Hiphop
  - Jazz
  - Metal
  - Pop
  - Reggae
  - Rock

---

## 🧠 Model: Vision Transformer (ViT)

We used a pre-trained [`vit_b_16`](https://pytorch.org/vision/stable/models/generated/torchvision.models.vit_b_16.html) model (trained on ImageNet) and fine-tuned it to classify audio genres.

---

## 🛠️ Approach

### 1. Convert Audio to Visuals

We converted each song into **two types of images**:

- **Mel-Spectrograms**: Time-frequency visualizations on a mel scale, mimicking human hearing.
- **MFCCs**: A compact representation of the power spectrum, often used in speech recognition.

### 2. Training Setup

- **Model**: Vision Transformer (`vit_b_16`)
- **Split**: 80% training / 20% testing
- **Optimization**:
  - Adam optimizer
  - Early stopping to avoid overfitting
- **Image Input Size**: Resized to fit ViT input (224x224)
- **Augmentations**: Optional (flip, brightness, etc.)

---

## 📊 Results

| Input Type     | Accuracy |
|----------------|----------|
| Mel-Spectrogram| **80.5%** |
| MFCC           | 72.5%    |

### 🔍 Confusion Matrices

| Mel-Spectrogram | MFCC |
|------------------|------|
| ![Mel CM](.image/CM-Mel-ViT.png) | ![MFCC CM](.image/CM-MFCC-ViT.png) |

> ✅ Metal and Classical were classified really well  
> ⚠️ Some confusion between Rock vs Country, and Pop vs Disco

---

### 📈 Training Curves
Accuracy & Loss 
| Mel-Spectrogram | MFCC |
|------------------|
| ![Training Graph](.image/Mel-ViT.png) | ![Training Graph](.image/Mel-ViT.png)|

