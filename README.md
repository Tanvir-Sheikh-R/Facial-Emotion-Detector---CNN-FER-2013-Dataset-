# 😊 Facial Emotion Detector

A deep learning project for facial emotion recognition using the **FER-2013** dataset. Two models are implemented and compared:
- A custom **CNN built from scratch**
- **ResNet-18** with transfer learning (pretrained on ImageNet)

---

## 🗂️ Project Structure

```
├── Facial_emotion_detector.ipynb   # Main notebook
├── best_parameters.pth             # Saved best model weights
└── README.md
```

---

## 🎭 Emotions Detected

The model classifies facial expressions into **7 emotions**:

| Label | Emotion |
|-------|---------|
| 0 | Angry |
| 1 | Disgust |
| 2 | Fear |
| 3 | Happy |
| 4 | Sad |
| 5 | Surprise |
| 6 | Neutral |

---

## 📦 Dataset

This project uses the **FER-2013** dataset by [msambare](https://www.kaggle.com/datasets/msambare/fer2013) on Kaggle.

### Option 1 — Download via KaggleHub (Recommended)

```python
import kagglehub

# Download latest version
path = kagglehub.dataset_download("msambare/fer2013")
print("Path to dataset files:", path)
```

### Option 2 — Download Manually

1. Go to [https://www.kaggle.com/datasets/msambare/fer2013](https://www.kaggle.com/datasets/msambare/fer2013)
2. Download and extract the dataset
3. Place it in a `data/` folder with this structure:

```
data/
├── train/
│   ├── angry/
│   ├── disgust/
│   ├── fear/
│   ├── happy/
│   ├── sad/
│   ├── surprise/
│   └── neutral/
└── test/
    ├── angry/
    └── ...
```

> **Note:** A Kaggle account is required to download the dataset.

---

## 🛠️ Requirements

```bash
pip install torch torchvision tqdm pillow kagglehub
```

---

## 🧠 Models

### 1. Custom CNN
- 3 convolutional blocks (64 → 128 → 256 filters)
- BatchNorm + Dropout for regularization
- Trained from scratch on FER-2013

### 2. ResNet-18 (Transfer Learning)
- Pretrained ResNet-18 from ImageNet
- Final `fc` layer replaced with custom head for 7 emotions
- Fine-tuned on FER-2013 with ImageNet normalization

---

## 🚀 How to Run

1. Clone the repository
```bash
git clone https://github.com/your-username/facial-emotion-detector.git
cd facial-emotion-detector
```

2. Install dependencies
```bash
pip install torch torchvision tqdm pillow kagglehub
```

3. Download the dataset using the code above

4. Open and run `Facial_emotion_detector.ipynb`

---

## ⚙️ Training Details

| | Custom CNN | ResNet-18 |
|--|--|--|
| Input size | 48×48 | 224×224 |
| Epochs | 50 | 30 |
| Optimizer | Adam | Adam |
| Loss | CrossEntropyLoss | CrossEntropyLoss |
| Scheduler | ReduceLROnPlateau | ReduceLROnPlateau |
| Batch size | 64 | 64 |

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

The FER-2013 dataset is provided by Kaggle user [msambare](https://www.kaggle.com/datasets/msambare/fer2013).
