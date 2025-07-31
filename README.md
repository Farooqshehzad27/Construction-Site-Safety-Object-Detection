# 🏗️ Construction Site Safety Object Detection

This project focuses on detecting safety-related objects at construction sites using the **YOLOv8-Mobilenet** model implemented with the **Ultralytics** library. The aim is to automate the monitoring of personal protective equipment (PPE) like hardhats, masks, and safety vests to improve workplace safety.

---

## 📌 Project Overview

- **Model:** YOLOv8-Mobilenet
- **Framework:** Ultralytics YOLOv8 (Python)
- **Dataset:** Construction Site Safety Image Dataset from RoboFlow
- **Objective:** Detect 10 object classes relevant to construction safety

---

## 🎯 Objectives

- ✅ Train a lightweight object detection model for construction site safety
- ✅ Evaluate the model’s performance using precision, recall, and mAP
- ✅ Handle dataset download and augmentation for robust learning
- ✅ Save the best-trained weights for future deployment

---

## 🗂️ Dataset Description

- **Classes (10):**
  - `Hardhat`
  - `Mask`
  - `NO-Hardhat`
  - `NO-Mask`
  - `NO-Safety Vest`
  - `Person`
  - `Safety Cone`
  - `Safety Vest`
  - `Machinery`
  - `Vehicle`
- **Validation Set:** 114 images with 697 annotated instances

---

## ⚙️ Methodology

### 🔄 Data Preprocessing

- Extracted and organized the dataset into train/val/test folders
- Applied augmentation strategies:
  - **Mosaic Augmentation** (until epoch 40)
  - **Post-mosaic Augmentations**: Blur, MedianBlur, CLAHE, ToGray

### 🧠 Model Architecture

- YOLOv8-Mobilenet (9.27M parameters, 26.4 GFLOPs)
- Configured using `yolov8-mobilenet.yaml`
- Loss Functions:
  - Bounding Box Loss
  - Classification Loss
  - Distribution Focal Loss (DFL)

### 🏋️ Training Details

- **Epochs:** 50
- **Image Size:** 640x640
- **Batch Size:** Inferred from 163 batches (~8–16)
- **Hardware:** Tesla T4 GPU
- **Outputs:** `best.pt` and `last.pt` saved for inference

---

## 📊 Results

| Metric     | Score     |
|------------|-----------|
| Precision  | 0.709     |
| Recall     | 0.481     |
| mAP@0.5    | 0.55      |
| mAP@0.5:0.95 | 0.254   |

### 🔍 Class-wise Performance (mAP@0.5)

| Class         | Score |
|---------------|-------|
| **Mask**          | 0.818 |
| **Safety Cone**   | 0.780 |
| **Hardhat**       | 0.656 |
| NO-Mask       | 0.391 |
| Vehicle        | 0.263 |

---

## 🧪 Example Detections

> 📷 See `images/` folder for sample input and output visualizations

---

## ❗ Challenges

- ⚠️ **Kaggle API failed** due to missing `kaggle.json`, so manual download used
- ⚠️ **Class imbalance** affected performance on certain classes like Vehicle and NO-Mask

---

## ✅ Future Work

- 🔧 Tune hyperparameters (batch size, learning rate)
- 📈 Balance underrepresented classes
- ☁️ Migrate training to cloud (for scalability)
- 🚀 Deploy model to edge devices (Jetson Nano, Raspberry Pi, etc.)

---

## 🧠 Author

- **Farooq Shehzad**  
  [GitHub](https://github.com/Farooqshehzad27)

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
