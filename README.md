---

# 🚗 Parking Space Detection System

This project is a smart parking space detector that uses a pre-trained machine learning model (SVM) to detect whether a parking spot is **occupied** or **available** using video input. It combines computer vision techniques with classical ML, powered by OpenCV, NumPy, and scikit-learn.

---

## 📁 Folder Structure

```
vehicle-parking-space-detection/
│
├── main.py
├── util.py
├── model.p
├── mask_1920_1080.png
├── requirements.txt
├── README.md
└── data/
    └── parking_1920_1080_loop.mp4
```

---

## ⚙️ System Configuration

### 💻 Laptop Specs (Development Environment)

| Specification    | Details                                   |
|------------------|-------------------------------------------|
| Device           | MacBook                                    |
| Processor        | Apple Silicon / Intel                     |
| RAM              | 8 GB                                       |
| OS               | macOS (e.g., Sonoma or Ventura)           |
| Python Version   | 3.11+                                      |
| Virtual Env      | `venv` used for isolation                 |

---

## 📦 Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/parking-space-counter.git
cd parking-space-counter
```

### 2. Create Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the Detector

```bash
python main.py
```

### 5. Exit the App

> Press `q` while the video window is open.

---

## ⚙️ Working Mechanism

### 🧩 Masking

- The binary `mask_1920_1080.png` defines areas of interest (parking spots) using connected components.

### ⚙️ Preprocessing

- Each parking region is extracted, resized to `(15x15x3)`, and flattened.

### 🧠 Prediction

A pre-trained SVM model (`model.p`) classifies each spot as:

- `0`: Empty  
- `1`: Occupied  

### 🔁 Real-Time Feedback

- Frame-by-frame detection overlays:
  - 🟩 **Green box** — Available
  - 🟥 **Red box** — Occupied
- Displays real-time count of free vs total spots.

---

## 📜 `requirements.txt`

```text
opencv-python
numpy
matplotlib
scikit-learn
scikit-image
```

To create it yourself:

```bash
pip freeze > requirements.txt
```

---

## 🧪 Model Details

- **Type**: Support Vector Machine (SVM)
- **Input Shape**: `(15, 15, 3)`
- **Trained On**: Manually labeled cropped parking spot patches
- **Accuracy**: ~94%
- **File**: `model.p` (stored via Pickle)

### 🔍 Inference Example

```python
from skimage.transform import resize
import numpy as np
import pickle

model = pickle.load(open("model.p", "rb"))
img_resized = resize(spot_bgr, (15, 15, 3)).flatten()
prediction = model.predict([img_resized])
```

---

## ✅ Output Example

| Frame | Parking Spot Status | Bounding Box Color | Live Count Display | Notes                                |
|-------|----------------------|--------------------|---------------------|--------------------------------------|
| 001   | Empty                | 🟩 Green            | Available: 15 / 20   | Spot correctly detected as empty     |
| 024   | Occupied             | 🟥 Red              | Available: 12 / 20   | Spot marked as occupied after entry  |
| 048   | Mixed                | Green & Red        | Available: 10 / 20   | Multiple spots updated in real-time  |
| 072   | All Occupied         | 🟥 Red              | Available: 0 / 20    | All spots taken — full parking       |
| 096   | Vehicle Left         | 🟩 Green            | Available: 2 / 20    | Spot marked empty after exit         |

---

## 🚀 Future Enhancements

- 🔍 Upgrade to YOLOv5/YOLOv8 for object detection
- 🌐 Add Flask/Django-based web UI
- ☁️ Integrate cloud-based updates (Firebase, MongoDB)
- 📊 Train on larger datasets for better generalization

---

## 🔗 Google Drive Link for Model & Data

[📂 Click here to download `model.p`, `mask_1920_1080.png`, and `parking_1920_1080_loop.mp4`](https://drive.google.com/drive/folders/1OMYogGZsoFgQEL2Es6EP2o7ImuwV-xEO?usp=sharing)

---

## 👨‍💻 Developed By

**Penuvarthi Guru Vishnu Sai**  
_MERN Stack Developer | AI/ML Enthusiast_  
🎓 CSVTU | Specialization: Data Science  
📫 [LinkedIn](https://linkedin.com/in/your-link) • 💻 [GitHub](https://github.com/your-username)

---

Let me know if you'd like a version for `README.md` file export or for your second project (`VisiAge Fall Detection System`) cleaned up in the same style!
