Sure Vishnu! Here's your entire content **restructured, formatted cleanly, and ready to paste directly into your `README.md`** file on GitHub. All code blocks, headings, lists, and tables are correctly formatted using GitHub Markdown standards.

---

```markdown
# 🚗 Vehicle Parking Space Detection System

This project is a smart parking space detection system that utilizes traditional machine learning techniques to determine whether a parking spot is **occupied** or **empty** using video input. It uses OpenCV for image processing, NumPy for array operations, and a pre-trained **SVM (Support Vector Machine)** model for classification.

---

## 📁 Folder Structure

```
vehicle-parking-space-detection/
│
├── data/
│   └── parking_1920_1080_loop.mp4       # Input video
├── model.p                              # Trained SVM model
├── mask_1920_1080.png                   # Binary mask for ROI
├── main.py                              # Main detection script
├── util.py                              # Utility functions
├── requirements.txt                     # Python dependencies
└── README.md                            # Project documentation
```

---

## ⚙️ System Configuration

| Specification     | Details                        |
|------------------|--------------------------------|
| 💻 Device         | MacBook                        |
| 🔧 Processor      | Apple Silicon / Intel          |
| 🧠 RAM            | 8 GB                           |
| 🖥 OS             | macOS (Sonoma / Ventura)       |
| 🐍 Python Version | 3.11+                          |
| 📦 Environment    | `venv` (virtual environment)   |

---

## 📦 Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/vehicle-parking-space-detection.git
cd vehicle-parking-space-detection
```

### 2. Create and Activate Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Required Packages

```bash
pip install -r requirements.txt
```

### 4. Download Required Assets

Download the following files from Google Drive:

- `model.p`
- `mask_1920_1080.png`
- `parking_1920_1080_loop.mp4`

📁 [Download Assets](https://drive.google.com/drive/folders/1OMYogGZsoFgQEL2Es6EP2o7ImuwV-xEO?usp=sharing)

Place them in the project root or respective folders.

---

## ▶️ How to Run

```bash
python main.py
```

> Press `q` to exit the video window.

---

## ⚙️ How It Works

### 🧭 Masking
A binary mask (`mask_1920_1080.png`) defines regions of interest (parking spots) using connected components.

### 🔄 Preprocessing
Each parking spot is:
- Cropped from the video frame
- Resized to `(15, 15, 3)`
- Flattened into a 1D array

### 🧠 Prediction
The pre-trained SVM model (`model.p`) classifies each spot:
- `0` → Empty
- `1` → Occupied

### 🎯 Real-Time Visualization
- 🟩 **Green box** → Empty spot
- 🟥 **Red box** → Occupied spot
- Displays live count of available vs total spots

---

## 📜 `requirements.txt`

```
opencv-python
numpy
matplotlib
scikit-learn
scikit-image
```

To generate or update this file:

```bash
pip freeze > requirements.txt
```

---

## 🧠 Model Details

| Property        | Details                             |
|----------------|-------------------------------------|
| Model Type      | Support Vector Machine (SVM)        |
| Input Size      | (15, 15, 3)                         |
| Format          | `.p` file (Pickle format)           |
| Training Data   | Cropped, labeled parking spot patches |
| Accuracy        | ~94%                                |

---

## 🔍 Inference Example

```python
from skimage.transform import resize
import numpy as np
import pickle

model = pickle.load(open("model.p", "rb"))
img_resized = resize(spot_bgr, (15, 15, 3)).flatten()
prediction = model.predict([img_resized])
```

---

## ✅ Output Examples

| Frame | Spot Status   | Box Color | Available Spots | Description                      |
|-------|---------------|-----------|------------------|----------------------------------|
| 001   | Empty         | 🟩 Green  | 15 / 20          | Correctly identified as empty    |
| 024   | Occupied      | 🟥 Red    | 12 / 20          | Detected vehicle entry           |
| 072   | All Occupied  | 🟥 Red    | 0 / 20           | Parking full                     |
| 096   | One Vacant    | 🟩 Green  | 1 / 20           | Vehicle exit detected            |

---

## 🚀 Future Enhancements

- ⚙️ Upgrade to **YOLOv5 / YOLOv8** for object detection
- 🌐 Build a **web dashboard** using Flask or Django
- ☁️ Integrate with **Firebase / MongoDB** for cloud storage
- 📊 Train on **larger datasets** for better accuracy

---

## 👨‍💻 Developed By

**Penuvarthi Guru Vishnu Sai**  
*MERN Stack Developer | AI/ML Enthusiast*  
🎓 CSVTU | Specialization: Data Science  
📫 [LinkedIn](https://linkedin.com/in/your-profile) | 💻 [GitHub](https://github.com/your-username)
```

---

Let me know if you'd like the same treatment for your **Fall Detection System README** too — I can give that a full makeover next!
