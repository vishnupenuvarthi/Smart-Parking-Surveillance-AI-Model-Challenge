
## data and models google drive link  
https://drive.google.com/drive/folders/1OMYogGZsoFgQEL2Es6EP2o7ImuwV-xEO?usp=sharing

# Parking Space Detection System

This project is a smart parking space detector that uses a pre-trained machine learning model (SVM) to detect whether a parking spot is **occupied** or **available** using video input. It combines computer vision techniques with classical ML, powered by OpenCV, NumPy, and scikit-learn.

## 🔧 Project Folder Structure


---

## ⚙️ System Configuration

### 💻 Laptop Specs (Development Environment)

| Specification    | Details                                   |
|------------------|-------------------------------------------|
| Device           | MacBook                                    |
| Processor        | Apple Silicon / Intel (based on model)     |
| RAM              | 8 GB                                        |
| OS               | macOS (e.g., Sonoma or Ventura)            |
| Python Version   | 3.11+                                       |
| Virtual Env      | `venv` used for isolation                  |

---

## 📦 Installation & Setup

1. **Clone the Repository**
   ```bash
   git clone https://github.com/your-username/parking-space-counter.git
   cd parking-space-counter

2.Create Virtual Environment

python3 -m venv venv
source venv/bin/activate

3.Install Dependencies
pip install -r requirements.txt

4.Run the Detector
python main.py

5.Exit the App

Press q key while the video window is open.


1. **Working Mechanism**
Masking:

The binary mask_1920_1080.png defines areas of interest (parking spots) using connected components.

Preprocessing:

Each parking region is extracted, resized to (15x15x3), and flattened.

Prediction:

A pre-trained SVM model (model.p) classifies each spot as:

0: Empty

1: Occupied

Real-Time Feedback:

Frame-by-frame detection overlays:

🟩 Green box — Available

🟥 Red box — Occupied

Displays real-time count of free vs total spots.

📦 requirements.txt
opencv-python
numpy
matplotlib
scikit-learn
scikit-image

Create it using:
pip freeze > requirements.txt


🧪 Model Details
Type: Support Vector Machine (SVM)

Input Shape: (15, 15, 3)

Trained On: Cropped parking spot patches (manually labeled)

Accuracy: ~94%

File: model.p (stored via Pickle)

Inference Example:

from skimage.transform import resize
import numpy as np
import pickle

model = pickle.load(open("model.p", "rb"))
img_resized = resize(spot_bgr, (15, 15, 3)).flatten()
prediction = model.predict([img_resized])


## ✅ Output Example

| Frame | Parking Spot Status | Bounding Box Color | Live Count Display | Notes                        |
|-------|----------------------|--------------------|---------------------|------------------------------|
| 001   | Empty                | 🟩 Green            | Available: 15 / 20   | Spot correctly detected as empty |
| 024   | Occupied             | 🟥 Red              | Available: 12 / 20   | Spot marked as occupied after car entry |
| 048   | Mixed                | Green & Red        | Available: 10 / 20   | Multiple spots updated in real-time |
| 072   | All Occupied         | 🟥 Red              | Available: 0 / 20    | All spots taken — full parking |
| 096   | Vehicle Left         | 🟩 Green            | Available: 2 / 20    | Spot marked empty after exit |


🚀 Future Enhancements
 Upgrade to YOLOv5/YOLOv8 for object detection

 Add Flask/Django-based web UI

 Integrate cloud-based updates (Firebase, MongoDB)

 Train on large datasets for higher generalization



# VisiAge Fall Detection System

<img src="images/caringminds.jpg" alt=" ogo" width="50%"/>

This project is a Fall Detection System that utilizes computer vision techniques to detect falls in a video feed. The system integrates with Azure Blob Storage to store relevant information about the detected falls.

## Features

- **Real-time Fall Detection:** Utilizes the YOLO (You Only Look Once) model to analyze video frames and identify key points of a person, enabling real-time fall detection. The possible key points are as shown in the image below:
  
  <img src="images/keypoints.png" alt="YOLOv8 Keypoints" width="50%"/>
  
- **Azure Blob Storage Integration:** Stores information about detected falls, including timestamp, video blob name, and incident status, in Azure Blob Storage.
- **API Call to App Service:** Triggers an API call to an app service endpoint when a fall is detected, providing relevant information for further alerting and analysis.

## Setup

1. **Install Dependencies:**
   - Ensure you have Python installed.
   - Install required Python packages using `pip install -r requirements.txt`.

2. **Azure Blob Storage Configuration:**
   - Set up an Azure Storage account and create a container for storing fall information and video clips.
   - Update the `AZURE_STORAGE_CONNECTION_STRING` and `CONTAINER_NAME` variables in the code with your Azure Storage account details.

3. **Run the Code:**
   - Execute the code file `fall_detection.py` to start the fall detection system.
   - The system will process the video feed, detect falls, and upload relevant information to Azure Blob Storage.

## Configuration

- **Yolo Model:**
  - The YOLO model file (`yolov8n-pose.pt`) is expected to be in the `yolo models/` directory.
  - You can replace the model file or adjust its location as needed.

- **Thresholds and Parameters:**
  - Adjust falling thresholds, time thresholds, and other parameters as needed for your specific use case. These are defined in the code under the "DEFINING VARIABLES AND CONSTANTS FOR FALLING/LAYING DOWN" section. Only adjust the following variables:
    - `MIN_ELAPSED_TIME_THRESHOLD`
    - `VIDEO_FPS`

- **Frames Per Second (FPS):**
  - The current FPS is 10. This is what worked best with the webcam. The number of frames in the before and after clip is calculated as follows: number of seconds x FPS
  - Since the saved footage is a maximum of 10 seconds before the fall, it is 100 frames. And 15 seconds after (150 frames). This value is subject to change as you change the FPS.
  - The code uses `source=0` which is the webcam. To apply the model to a video or image, you can change the source to the path of the file in quotes. Be aware though, you would have to change the FPS and the before/after lengths to match your desired speed for the capturing of the video footage. It was tested with a 30 FPS video and worked when the value of `video_frames_before` was 300, and `video_frames_after` was 450.

## Important Notes

- Make sure to customize the API endpoint (`url` variable in the `send_api_call` function) to match the endpoint of your app service.


 Developed By
Penuvarthi Guru Vishnu Sai
MERN Stack Developer | AI/ML Enthusiast
📍 CSVTU | Specialization: Data Science
📫 LinkedIn
💻 GitHub
