Milk Theft Detection from CCTV (Computer Vision)
Overview
This project presents an AI-based computer vision system for detecting potential milk theft events from CCTV footage by combining YOLOv8 Segmentation, MediaPipe Pose Estimation, spatial interaction analysis, and rule-based temporal reasoning.
Unlike traditional object detection systems that only identify objects within individual frames, this project reasons about how a person interacts with a milk vessel and silo over time. The system detects the required objects, estimates human body landmarks, analyzes their spatial relationships across consecutive frames, and automatically captures evidence whenever a potential theft event is detected.
---
Problem Statement
Manual CCTV monitoring is time-consuming and needs separate person for continuously observing milk collection centers. A theft event is rarely represented by a single frame—it is a sequence of actions involving a person, a vessel, and a milk silo.
Objective
Develop an end-to-end computer vision pipeline capable of:
Detecting silos and milk vessels from CCTV footage.
Estimating human body landmarks.
Understanding spatial interaction between the person, vessel, and silo.
Applying temporal rule-based reasoning to detect suspicious behaviour.
Automatically saving evidence frames for later verification.
---
System Pipeline

CCTV Video
    │
    ▼
YOLOv8 Segmentation
(Silo & Vessel Detection)
    │
    ▼
MediaPipe Pose Estimation
(Human Landmark Detection)
    │
    ▼
Spatial Interaction Analysis
(Person ↔ Vessel ↔ Silo)
    │
    ▼
Temporal Rule Engine
    │
    ▼
Potential Theft Event
    │
    ▼
Evidence Frame Saved

---
Methodology
CCTV video frames are processed sequentially.
YOLOv8 Segmentation detects silos and vessels.
MediaPipe Pose estimates the operator's body landmarks.
Spatial relationships between detected objects and body landmarks are computed.
Custom rule-based logic evaluates interactions across consecutive frames.
If the interaction satisfies predefined theft conditions, the frame is stored as evidence.
---
Repository Structure

Milk-Theft-Detection-Computer-Vision/
│
├── train/
│   ├── images/
│   └── labels/
├── valid/
│   ├── images/
│   └── labels/
├── test/
│   ├── images/
│   └── labels/
├── runs/
│   └── segment/
│       ├── train/
│       │   └── weights/
│       │       ├── best.pt
│       └── val/
├── theft_frames/
├── data.yaml
├── milk_theft_detection_demo.mp4
├── silo_vessel_detection_yolov8n_training.ipynb
├── yolov8n-seg.pt
├── requirements.txt
├── .gitignore
└── README.md

Folder Description
Item	                    Purpose
train/, valid/, test/ :	YOLO segmentation dataset
runs/segment/: 	Training outputs and model weights
theft_frames/ : Automatically captured evidence images
data.yaml	: Dataset configuration
milk_theft_detection_demo.mp4	: Demonstration video
silo_vessel_detection_yolov8n_training.ipynb :	Complete training and inference workflow
yolov8n-seg.pt	: Pretrained YOLOv8 segmentation weights
---
Dataset
~720 annotated CCTV images
Annotated using Roboflow
Classes:
Silo
Vessel
The dataset is relatively small and environment-specific, making this project a proof of concept rather than a production-ready solution.
---
Technologies Used
Python
Ultralytics YOLOv8 Segmentation
MediaPipe Pose
OpenCV
NumPy
Roboflow
Jupyter Notebook
---
Results
The proposed pipeline can:
Detect silos and vessels using YOLOv8 Segmentation.
Estimate human pose using MediaPipe Pose.
Analyze spatial interaction between the operator, vessel, and silo.
Apply temporal rule-based reasoning.
Automatically capture evidence frames when suspicious events occur.
Sample detections are available in the theft_frames/ directory.
---
Limitations
Small custom dataset.
Rule thresholds may require tuning for different camera angles.
Tested under limited environmental conditions.
Not validated for production deployment.
---
Future Improvements
Object tracking for stronger temporal consistency.
Multi-person support.
Multi-camera integration.
Larger and more diverse datasets.
Real-time deployment optimization.
---
Installation

git clone https://github.com/Remi97-hub/Milk-Theft-Detection-Computer-vision.git
cd Milk-Theft-Detection-Computer-vision
pip install -r requirements.txt
jupyter notebook
```
Open:

silo_vessel_detection_yolov8n_training.ipynb
```
---
Acknowledgements
Ultralytics YOLOv8
Google MediaPipe
OpenCV
Roboflow
---
> This project demonstrates an end-to-end computer vision pipeline that combines object segmentation, human pose estimation, spatial interaction analysis, and temporal rule-based reasoning to detect potential milk theft events from CCTV footage.