# 🏗️ Construction Safety Monitoring using YOLO11

> 🚧 An AI-powered Computer Vision project for detecting construction-site objects using a custom dataset and **YOLO11s**.

---

## 📌 Project Overview

This project implements a custom **object detection pipeline** for construction safety monitoring using **YOLO11s**.

The dataset was obtained and prepared using **Roboflow**, exported in YOLO11 format, and trained using **Google Colab with GPU acceleration**.

The project covers the complete workflow:

**📦 Dataset → 🏷️ Annotation → 🧠 Training → 📊 Validation → 🔍 Detection → 🎥 Video Inference**

---

## 🎯 Objectives

The main objectives of this project are:

- 🏗️ Detect construction-related safety objects
- 🧠 Train a custom YOLO11s object detection model
- 📊 Evaluate the trained model
- 📈 Analyze training performance
- 🖼️ Perform detection on images
- 🎥 Perform detection on videos
- 💻 Build practical experience with a complete Computer Vision workflow

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| 🐍 **Python** | Programming language |
| 👁️ **YOLO11s** | Object detection model |
| ⚡ **Ultralytics** | YOLO framework |
| 🏷️ **Roboflow** | Dataset management and preparation |
| ☁️ **Google Colab** | GPU-based training environment |
| 🔥 **PyTorch** | Deep Learning framework |
| 🎯 **Supervision** | Computer Vision utilities |

---

## 🔄 Project Workflow

```text
🏷️ Roboflow Dataset
        ↓
📦 YOLO11 Dataset Format
        ↓
☁️ Google Colab + GPU
        ↓
🧠 YOLO11s Training
        ↓
📊 Model Validation
        ↓
📈 Performance Analysis
        ↓
🖼️ Image Detection
        ↓
🎥 Video Detection
````

---

## 📦 Dataset

The dataset was obtained from **Roboflow** and downloaded in **YOLO11 format**.

The dataset was loaded directly into the Google Colab environment using the Roboflow API.

```python
from roboflow import Roboflow

rf = Roboflow(api_key="YOUR_API_KEY")
project = rf.workspace("YOUR_WORKSPACE").project("YOUR_PROJECT")
version = project.version(1)
dataset = version.download("yolov11")
```

> 🔐 **Security Note:** Never upload your actual Roboflow API key to GitHub. Use an environment variable or replace it with `YOUR_API_KEY`.

---

## 🧠 Model Training

The project uses **YOLO11s (Small)** for custom object detection.

The model was trained for:

* 🔁 **Epochs:** 50
* 🖼️ **Image Size:** 640
* 📊 **Plots:** Enabled
* ⚡ **GPU:** Google Colab GPU

### Training Command

```bash
yolo task=detect mode=train \
model=yolo11s.pt \
data=data.yaml \
epochs=50 \
imgsz=640 \
plots=True
```

The trained model generates:

```text
runs/
└── detect/
    └── train/
        └── weights/
            ├── best.pt
            └── last.pt
```

⭐ `best.pt` is used for subsequent validation and inference.

---

## 📊 Model Validation

After training, the custom model was validated using the validation dataset.

```bash
yolo task=detect mode=val \
model=best.pt \
data=data.yaml
```

Validation helps evaluate how well the trained model performs on data that was not used directly for training.

---

## 📈 Training Performance Analysis

YOLO generates several useful visualizations during training.

### 🔹 Confusion Matrix

The confusion matrix helps analyze classification performance between the detected classes.

### 🔹 Label Distribution

The label visualization helps understand the distribution and positioning of annotated objects.

### 🔹 Training Results

The generated `results.png` provides training and validation performance information across epochs.

---

## 🔍 Inference on Test Dataset

The trained model was first tested on the dataset's test images.

```bash
yolo task=detect mode=predict \
model=best.pt \
conf=0.25 \
source=test/images \
save=True
```

The resulting images contain:

* 📦 Bounding boxes
* 🏷️ Predicted class labels
* 🎯 Confidence scores

---

## 🖼️ Custom Image Detection

The project also supports detection on an image uploaded directly from the user's computer.

```python
from google.colab import files

uploaded = files.upload()
```

Then YOLO11 performs inference:

```bash
yolo task=detect mode=predict \
model=best.pt \
conf=0.25 \
source=/content/image.jpg \
save=True
```

---

## 🎥 Video Detection

The trained model can also process uploaded videos.

```bash
yolo task=detect mode=predict \
model=best.pt \
conf=0.25 \
source="/content/construction_video.mp4" \
save=True
```

This allows the model to perform frame-by-frame object detection on construction-site videos.

---

## 📁 Project Structure

```text
construction-safety/
│
├── 📓 construction_safety.ipynb
├── 📄 README.md
├── 📄 requirements.txt
│
├── 🧠 models/
│   └── best.pt
│
├── 🖼️ results/
│   ├── detection_images/
│   └── detection_videos/
│
└── 📂 dataset/
    └── data.yaml
```

> ⚠️ Large datasets and model files may be excluded from GitHub. The README provides instructions for reproducing the project.

---

## 🚀 How to Run

### 1️⃣ Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/construction-safety.git
```

### 2️⃣ Install dependencies

```bash
pip install ultralytics supervision roboflow
```

### 3️⃣ Open the notebook

Open:

```text
construction_safety.ipynb
```

using:

* ☁️ Google Colab
* 📓 Jupyter Notebook

### 4️⃣ Configure your Roboflow dataset

Add your Roboflow credentials securely.

### 5️⃣ Train the model

Run the training section.

### 6️⃣ Perform inference

Test the trained model on:

* 🖼️ Images
* 🎥 Videos
* 📦 Test dataset

---

## 📌 Key Learning Outcomes

Through this project, I learned how to:

* 🏷️ Work with custom object-detection datasets
* 🔗 Integrate Roboflow with Google Colab
* 🧠 Train a YOLO11 model from a pretrained model
* 📊 Validate a custom-trained model
* 📈 Analyze model performance
* 🖼️ Perform image inference
* 🎥 Perform video inference
* ⚙️ Work with YOLO CLI commands
* ☁️ Use GPU acceleration with Google Colab

---



## 👨‍💻 Author

**Anik Datta**

B.Tech CSE — Artificial Intelligence

Interested in:

* 🤖 Artificial Intelligence
* 🧠 Machine Learning
* 👁️ Computer Vision
* 🚀 AI Engineering

---

## ⭐ If you find this project useful

Feel free to ⭐ star the repository and explore the notebook!

```


