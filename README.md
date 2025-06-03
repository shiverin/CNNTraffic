# 🚦 Traffic Sign Classification with CNN

![CNN Architecture](https://img.shields.io/badge/Architecture-CNN-blue) 
![TensorFlow](https://img.shields.io/badge/Framework-TensorFlow%2FKeras-orange)
![Accuracy](https://img.shields.io/badge/Best_Accuracy-98.97%25-brightgreen)

A convolutional neural network (CNN) implementation for classifying traffic signs using the German Traffic Sign Recognition Benchmark (GTSRB) dataset.

## 📊 Performance Summary

**Best Model Achieved:**
- ✅ **98.97%** Test Accuracy
- ⚡ **0.0386** Test Loss 
- ⏱️ **~3s** Inference Time

## � Model Architectures & Results

| Model | Architecture | Dropout | Accuracy | Loss | Inference |
|-------|--------------|---------|----------|------|-----------|
| **1** | `Conv(32)→Pool→Dense(128)` | Yes | 97.02% | 0.1261 | ~2s |
| **2** | `Conv(32)→Pool→Conv(64)→Pool→Dense(128)` | Yes | 98.84% | 0.0555 | ~2s |
| **3** | `Conv(32)→Pool→Conv(64)→Pool→Dense(128)→Dropout→Dense(128)→Dropout` | Yes | 97.30% | 0.1289 | ~2s |
| **4** | `Conv(32)→Pool→Conv(64)→Pool→Conv(128)→Pool→Dense(128)→Dropout` | Yes | 98.86% | 0.0466 | ~3s |
| **5** | `Conv(32)→Pool→Conv(64)→Pool→Conv(128)→Pool→Dense(512)→Dropout` | Yes | **98.97%** | **0.0386** | ~3s |
| **6** | `Conv(32)→Pool→Conv(64)→Pool→Conv(128)→Pool→Dense(512)→Dropout→Dense(256)→Dropout` | Yes | 98.12% | 0.0765 | ~3s |

## 🛠 Implementation Details

### 🧪 Experiment Setup
| Parameter | Value |
|-----------|-------|
| Input Shape | 30×30 RGB |
| Data Source | GTSRB (category folders) |
| Train/Test Split | 60%/40% |
| Optimizer | Adam (default) |
| Loss Function | Categorical Crossentropy |
| Activations | ReLU (hidden), Softmax (output) |
| Normalization | `images / 255.0` |
| Epochs | 10 |
| Batch Size | Default |

### 📈 Key Observations
- **Depth Matters**: Adding Conv+Pool layers significantly boosted accuracy
- **Dropout Balance**: Effective but excessive use can hurt performance (Model 3)
- **Efficiency**: Model 2 offers excellent accuracy (98.84%) with faster inference
- **Top Performer**: Model 5 achieves best balance (98.97% accuracy)

## 🗂 Project Structure
```
traffic/
├── traffic.py # Main training/evaluation script
├── gtsrb/ # Dataset (0 to NUM_CATEGORIES-1)
├── requirements.txt # Python dependencies
└── README.md # Project documentation
```