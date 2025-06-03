# 🚦 Traffic Sign Classification

This project implements a convolutional neural network (CNN) to classify traffic signs using the German Traffic Sign Recognition Benchmark (GTSRB). The model is built and trained with TensorFlow.

---

## 🧠 Model Architectures & Results

| Model | Architecture                                                                                  | Dropout | Test Accuracy | Test Loss | Inference Time |
|-------|-----------------------------------------------------------------------------------------------|---------|---------------|-----------|----------------|
| **1** | `Conv(32) → Pool → Dense(128)`                                                               | ✅      | **97.02%**    | 0.1261    | ~2s            |
| **2** | `Conv(32) → Pool → Conv(64) → Pool → Dense(128)`                                             | ✅      | **98.84%**    | 0.0555    | ~2s            |
| **3** | `Conv(32) → Pool → Conv(64) → Pool → Dense(128) → Dropout(0.5) → Dense(128) → Dropout(0.5)` | ✅      | **97.30%**    | 0.1289    | ~2s            |
| **4** | `Conv(32) → Pool → Conv(64) → Pool → Conv(128) → Pool → Dense(128) → Dropout(0.5)`           | ✅      | **98.86%**    | 0.0466    | ~3s            |
| **5** | `Conv(32) → Pool → Conv(64) → Pool → Conv(128) → Pool → Dense(512) → Dropout(0.5)`           | ✅      | **98.97%**    | 0.0386    | ~3s            |
| **6** | `Conv(32) → Pool → Conv(64) → Pool → Conv(128) → Pool → Dense(512) → Dropout(0.5) → Dense(256) → Dropout(0.5)` | ✅      | **98.12%**    | 0.0765    | ~3s            |

---

## 🧪 Experiment Setup

- **Input shape:** 30 × 30 RGB images  
- **Dataset:** German Traffic Sign Recognition Benchmark (GTSRB), organized by category folders  
- **Train/Test split:** 60% train, 40% test  
- **Optimizer:** Adam (default parameters)  
- **Loss function:** Categorical Crossentropy  
- **Activation functions:** ReLU (hidden layers), Softmax (output layer)  
- **Normalization:** Pixel values scaled by `images / 255.0`  
- **Epochs:** 10  
- **Batch size:** Default  

---

## 📈 Observations

- Increasing network depth with additional Conv and Pool layers significantly improves accuracy.  
- Model 2 shows strong performance with just two Conv layers.  
- Dropout helps reduce overfitting, but excessive dropout (Model 3) can slightly hurt performance.  
- Best results achieved by Model 4, which uses 3 Conv + Pool layers and a Dense layer with dropout.

---

## 🗂️ Project Structure
```
traffic/
├── traffic.py # Main training/evaluation script
├── gtsrb/ # Dataset (0 to NUM_CATEGORIES-1)
├── requirements.txt # Python dependencies
└── README.md # Project documentation
```