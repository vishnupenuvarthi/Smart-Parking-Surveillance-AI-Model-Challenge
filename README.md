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

Absolutely! Here's the cleaned-up and consistently formatted version of your **VisiAge Fall Detection System** README, styled to match your Parking System one:

---

# 🧍‍♂️📉  Fall Detection System

The  Fall Detection System** is a real-time application that uses computer vision techniques and the YOLO pose estimation model to detect falls in a video stream. It integrates with **Azure Blob Storage** for storing fall incident data and notifies a cloud API endpoint upon fall detection.

---

## 🧠 Features

- ✅ **Real-time Fall Detection** using YOLO keypoint estimation.
- ☁️ **Azure Blob Storage Integration** for saving fall metadata and clips.
- 📡 **API Call to App Service** for alerting and analytics.
- 📈 Works with **webcams or pre-recorded videos**.

---

## 🧬 Keypoint Detection

The system identifies key body points to detect posture changes and fall incidents. Here's a visual of YOLO's keypoints:


---

## 📁 Folder Structure

```
visiage-fall-detection/
│
├── fall_detection.py
├── models/
│   └── yolov8n-pose.pt
├── images/
│   └── keypoints.png
│   └── caringminds.jpg
├── requirements.txt
└── README.md
```

---

## ⚙️ Setup Instructions

### 1. Install Dependencies

```bash
pip install -r requirements.txt
```

---

### 2. Azure Blob Storage Configuration

- Set up an Azure Storage account.
- Create a container to store fall-related data.
- Update the following variables in your code:

```python
AZURE_STORAGE_CONNECTION_STRING = "<your_connection_string>"
CONTAINER_NAME = "<your_container_name>"
```

---

### 3. Run the Code

```bash
python fall_detection.py
```

The system starts reading from your webcam (`source=0`). To use a video file instead, change the `source` variable in the code:

```python
source = "path/to/your/video.mp4"
```

---

## ⚙️ Configuration Details

### 📦 Model

| Item         | Description                             |
|--------------|-----------------------------------------|
| Model Name   | YOLOv8n Pose                            |
| Model Path   | `models/yolov8n-pose.pt`                |
| Task         | Keypoint Detection                      |
| FPS Default  | 10 FPS                                  |
| Source       | `0` (webcam) or video path              |

---

### 🔧 Threshold Parameters

You can tweak the following constants in the code under:

```python
# DEFINING VARIABLES AND CONSTANTS FOR FALLING/LAYING DOWN
MIN_ELAPSED_TIME_THRESHOLD = 2  # seconds
VIDEO_FPS = 10
```

### 📼 Frame Capturing Logic

- Video before fall = `10 sec x 10 FPS = 100 frames`
- Video after fall = `15 sec x 10 FPS = 150 frames`

> ⚠️ For 30 FPS videos, adjust:
> 
> ```python
> video_frames_before = 300
> video_frames_after = 450
> ```

---

## 🌐 API Integration

When a fall is detected, the following data is sent via POST request:

```json
{
  "incident_status": "Fall Detected",
  "video_blob_name": "fall_clip_2024_04_12.mp4",
  "timestamp": "2024-04-12T14:30:45Z"
}
```

Update the endpoint URL in:

```python
url = "<your_app_service_endpoint>"
```

---

## 🧪 Requirements

```text
ultralytics
opencv-python
azure-storage-blob
numpy
matplotlib
```

To generate this:

```bash
pip freeze > requirements.txt
```

---

## 🧾 Sample Output Behavior

| Scenario          | Result                                |
|-------------------|----------------------------------------|
| Normal Movement   | System continues monitoring            |
| Fall Detected     | Saves fall video, uploads to Azure, triggers API |
| Webcam Lost       | Displays an error or halts processing  |

---



## 👨‍💻 Developed By

**Penuvarthi Guru Vishnu Sai**  
_MERN Stack Developer | AI/ML Enthusiast_  
🎓 CSVTU | Specialization: Data Science  
📫 [LinkedIn](https://linkedin.com/in/your-link) • 💻 [GitHub](https://github.com/your-username)

---
