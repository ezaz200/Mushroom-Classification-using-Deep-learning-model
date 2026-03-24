# 🍄 Mushroom Classification using Deep Learning (CNN)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange?style=for-the-badge&logo=tensorflow)
![Keras](https://img.shields.io/badge/Keras-Deep%20Learning-red?style=for-the-badge&logo=keras)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

> A Convolutional Neural Network (CNN) based image classification model that identifies mushroom species from raw photographs — helping distinguish **edible** from **poisonous** mushrooms with high accuracy.

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Dataset](#-dataset)
- [Model Architecture](#-model-architecture)
- [Project Structure](#-project-structure)
- [Installation](#-installation)
- [Usage](#-usage)
- [Results](#-results)
- [Future Work](#-future-work)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🧠 Overview

Mushroom foraging is a popular but potentially **dangerous** activity — many poisonous species closely resemble edible ones. This project applies **deep learning** to automate mushroom species classification from raw images using a custom **Convolutional Neural Network (CNN)**.

**Key highlights:**
- Raw mushroom photographs used as input (no preprocessing required at inference)
- CNN trained from scratch for multi-class image classification
- Capable of distinguishing between edible and toxic species
- Designed for real-world deployment use cases

---

## 📂 Dataset

- **Source:** Raw mushroom images (collected/curated manually or from public datasets)
- **Format:** `.jpg` / `.png` images organized per class in folders
- **Classes:** Multiple mushroom species (e.g., *Amanita*, *Boletus*, *Chanterelle*, etc.)
- **Split:** Training / Validation / Test (e.g., 70% / 15% / 15%)

### Dataset Structure

```
dataset/
├── train/
│   ├── class_1/
│   ├── class_2/
│   └── ...
├── val/
│   ├── class_1/
│   └── ...
└── test/
    ├── class_1/
    └── ...
```

> **Note:** Dataset is not included in this repository due to size. See [Usage](#-usage) for how to set up your own dataset.

---

## 🏗 Model Architecture

The CNN model consists of the following layers:

| Layer | Details |
|-------|---------|
| Conv2D + ReLU | Feature extraction (32 filters, 3×3) |
| MaxPooling2D | Spatial downsampling (2×2) |
| Conv2D + ReLU | Deeper feature extraction (64 filters, 3×3) |
| MaxPooling2D | Spatial downsampling (2×2) |
| Conv2D + ReLU | High-level features (128 filters, 3×3) |
| MaxPooling2D | Spatial downsampling (2×2) |
| Flatten | Convert to 1D vector |
| Dense + ReLU | Fully connected (256 units) |
| Dropout (0.5) | Regularization |
| Dense + Softmax | Output layer (N classes) |

**Training Details:**
- Optimizer: `Adam`
- Loss: `Categorical Crossentropy`
- Metrics: `Accuracy`
- Image Size: `128×128` (or your configured size)
- Epochs: configurable (default: 30)
- Data Augmentation: Rotation, flip, zoom, shear

---

## 📁 Project Structure

```
mushroom-classification-cnn/
│
├── dataset/                  # Dataset directory (not tracked)
├── models/                   # Saved model files (.h5 / .keras)
├── notebooks/
│   └── mushroom_cnn.ipynb    # Main Jupyter Notebook
├── src/
│   ├── train.py              # Training script
│   ├── predict.py            # Inference / prediction script
│   └── model.py              # CNN model definition
├── static/                   # Sample images for testing
├── requirements.txt          # Python dependencies
└── README.md
```

---

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/your-username/mushroom-classification-cnn.git
cd mushroom-classification-cnn
```

### 2. Create a virtual environment (recommended)

```bash
python -m venv venv
source venv/bin/activate       # On Windows: venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### requirements.txt (example)

```
tensorflow>=2.10
numpy
matplotlib
scikit-learn
Pillow
opencv-python
```

---

## 🚀 Usage

### Train the model

```bash
python src/train.py --data_dir dataset/ --epochs 30 --batch_size 32
```

### Predict on a new image

```bash
python src/predict.py --image_path static/sample_mushroom.jpg --model_path models/mushroom_cnn.h5
```

### Run in Jupyter Notebook

```bash
jupyter notebook notebooks/mushroom_cnn.ipynb
```

---

## 📊 Results

| Metric | Value |
|--------|-------|
| Training Accuracy | ~70% |
| Validation Accuracy | ~69.66% |
| Test Accuracy | ~XX% |
| Loss (Test) | ~0.87 |

> *(Update with your actual results after training)*

### Training Curves

*(Add accuracy/loss plots here)*

---

## 🔮 Future Work

- [ ] Transfer learning using **MobileNetV2** / **EfficientNet** for higher accuracy
- [ ] Web or mobile app deployment using **Flask** / **TensorFlow Lite**
- [ ] Expand dataset with more mushroom species
- [ ] Add **Grad-CAM** visualization to explain model predictions
- [ ] Real-time classification via webcam

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/new-feature`
3. Commit your changes: `git commit -m 'Add new feature'`
4. Push to the branch: `git push origin feature/new-feature`
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Ezaz**  
ECE Student | Embedded Systems & Deep Learning Enthusiast  
📧 your-email@example.com  
🔗 [GitHub](https://github.com/ezaz200)

---

> ⚠️ **Disclaimer:** This model is for educational/research purposes only. Do **NOT** use it as the sole method to determine if a mushroom is safe to eat. Always consult an expert mycologist.
