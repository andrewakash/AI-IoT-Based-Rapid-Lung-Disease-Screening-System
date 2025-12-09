🫁 AI + IoT Lung Disease Screening System

A hybrid, AI-powered screening system for COVID-19, COPD, Pneumonia, and Normal lungs, combining Deep Learning–based chest X-ray analysis with IoT spirometry data. The system delivers a diagnosis in under 1 minute, designed for hospitals, emergency care, and rural healthcare centers.

Features
Core Features

✅ Multimodal Diagnosis: Combines chest X-ray images (CNN) with spirometry metrics (FVC, FEV1, PEFR)

✅ 1-Minute Prediction: Fast inference suitable for triage and mass screening

✅ Disease Classification: Detects COVID-19, COPD, Pneumonia, and Normal cases

✅ Explainable AI: Generates Grad-CAM heatmaps to highlight affected lung regions

✅ Doctor Dashboard: Web-based interface to upload X-rays, enter spirometry values, and view results

✅ Portable & Scalable: Designed to work with low-cost IoT spirometers and standard X-ray images

✅ Rural-Friendly: Works in low-resource settings; can be adapted for partial offline usage

Technical Features

🧠 CNN + DNN Fusion Model: VGG16-based feature extraction fused with spirometry features using a deep neural network

📉 PCA-Based Dimensionality Reduction: Reduces high-dimensional CNN features while preserving essential information

🧪 Preprocessing Pipelines: X-ray normalization, resizing, and augmentation support

📊 Evaluation Tools: Confusion matrix, accuracy, precision/recall metrics

🧩 Modular Design: Separate modules for data loading, model training, inference, and IoT integration

🌐 REST API for Prediction: Exposes endpoints to integrate with other hospital systems

Tech Stack
Machine Learning & Data

Python 3.x – Core language

TensorFlow / Keras – CNN and DNN models (VGG16 + custom fusion network)

Scikit-Learn – PCA, metrics, and utilities

Pandas / NumPy – Data handling and numerical operations

OpenCV / Pillow – Image preprocessing

IoT & Hardware

Arduino / Microcontroller – Spirometer controller

Airflow / Pressure Sensor – Captures exhalation data

Serial / UART Communication – Sends spirometry data to host machine

Backend & API

Flask – RESTful API for prediction and dashboard backend

Flask-CORS – Cross-origin support for frontend integration

Frontend

HTML5 / CSS3 – UI structure and styling

JavaScript (Vanilla or React – optional) – Interactive dashboard

Chart.js (optional) – Visualizing trends & metrics

Project Structure
.
├── backend/
│   ├── app.py                # Flask API server (prediction endpoints & dashboard)
│   ├── models/
│   │   ├── vgg16_cnn.h5      # Trained CNN model for X-ray features
│   │   ├── pca.pkl           # PCA transformer for feature reduction
│   │   └── fusion_dnn.h5     # Fusion DNN model for final classification
│   ├── utils/
│   │   ├── preprocessing.py  # Image & spirometry preprocessing
│   │   ├── gradcam.py        # Grad-CAM generation utilities
│   │   └── inference.py      # Helper functions for prediction
│   ├── requirements.txt      # Python dependencies
│   ├── static/
│   │   └── heatmaps/         # Generated Grad-CAM images
│   └── templates/
│       └── dashboard.html    # Doctor dashboard UI (Jinja/HTML)
│
├── spirometer/
│   ├── firmware.ino          # Arduino code for airflow sensor
│   └── README.md             # Hardware setup & calibration guide
│
├── notebooks/
│   ├── training_cnn.ipynb    # X-ray CNN training notebook
│   ├── training_fusion.ipynb # Fusion model training notebook
│   └── evaluation.ipynb      # Model evaluation & plots
│
├── data/
│   ├── xray/                 # Sample X-ray images (anonymized)
│   └── spirometry/           # Sample spirometry records
│
└── README.md                 # Project documentation

Installation & Setup
Prerequisites

Python 3.8+

(Optional) Virtual environment (venv/conda)

Basic Arduino/IoT setup for spirometer (if testing hardware)

Backend Setup

Clone the repository

git clone https://github.com/your-username/lung-disease-screening.git
cd lung-disease-screening/backend


Create and activate virtual environment (recommended)

python -m venv venv
# Windows
venv\Scripts\activate
# Linux / macOS
source venv/bin/activate


Install dependencies

pip install -r requirements.txt


Start the Flask server

python app.py


By default, the backend runs at:
👉 http://localhost:5000

Spirometer (IoT) Setup (Optional but recommended)

Open spirometer/firmware.ino in the Arduino IDE

Configure the correct board and COM port

Upload the firmware to the microcontroller

Connect airflow/pressure sensor to the board as per wiring comments in the file

Spirometry data (FVC, FEV1, PEFR) will be sent via Serial to the host machine

If you don’t have hardware yet, you can use dummy spirometry JSON or values entered manually in the dashboard.

Usage
1. Doctor Dashboard Flow

Open the dashboard in a browser:
👉 http://localhost:5000

Upload a chest X-ray image (PNG/JPG)

Enter spirometry values:

FVC

FEV1

PEFR
(or let the page fetch them from serial if auto-integration is implemented)

Click “Predict”

View:

Predicted class: COVID-19 / COPD / Pneumonia / Normal

Confidence score

Grad-CAM heatmap of affected region

System Architecture
                 ┌───────────────────────────┐
                 │     Chest X-Ray Image     │
                 └──────────────┬────────────┘
                                │
                           CNN (VGG16)
                                │
                          Image Features
                                │
            ┌───────────────────┴───────────────────┐
            │                                       │
            ▼                                       ▼
      PCA (Dim Red.)                        Spirometry Input
                                                (FVC, FEV1, PEFR)
            └───────────────────┬──────────────────┘
                                ▼
                        Fusion DNN Model
                                │
                                ▼
                 ┌─────────────────────────────────┐
                 │  Prediction Output (4 Classes)  │
                 │ COVID | COPD | Pneumonia | Normal│
                 └─────────────────┬────────────────┘
                                   ▼
                           Grad-CAM Heatmap
                                   ▼
                           Doctor Dashboard

API Endpoints

All endpoints are prefixed with /api.

GET /api/health

Health check endpoint.
Response:

{ "status": "ok" }

POST /api/predict

Run a full multimodal prediction.

Request type: multipart/form-data

Fields:

xray – X-ray image file (PNG/JPG)

fvc – float

fev1 – float

pefr – float

Sample Response:

{
  "prediction": "COVID-19",
  "confidence": 0.96,
  "class_index": 0,
  "heatmap_path": "/static/heatmaps/covid_001.png"
}

POST /api/predict-json

Send X-ray (base64 or path) + spirometry values as JSON.

Request body example:

{
  "image_path": "data/xray/sample1.png",
  "fvc": 3.1,
  "fev1": 2.7,
  "pefr": 430
}

Data Format (Internal)
{
  "xray": "path_or_binary",
  "spirometry": {
    "fvc": 3.1,
    "fev1": 2.7,
    "pefr": 430
  }
}

Development
Model Training

notebooks/training_cnn.ipynb – Trains VGG16 on labeled X-ray dataset

notebooks/training_fusion.ipynb – Trains fusion DNN using:

Reduced CNN features (PCA)

Spirometry metrics

Evaluation

notebooks/evaluation.ipynb – Plots confusion matrices, ROC curves, and class-wise metrics

Experiments logged as:

Accuracy

F1-score

Per-class performance

Future Enhancements

 Integrate additional lung diseases and severity levels

 Add patient history and clinical parameters to the model

 Implement offline mode with queued sync for rural centers

 Add user authentication & role-based access for hospitals

 Support DICOM medical image formats

 Add full hardware calibration UI for spirometer

 Deploy using Docker + Cloud (AWS/GCP/Azure)

 Create a dedicated mobile app for field screening

Troubleshooting
Prediction Issues

Ensure the X-ray image is frontal chest view and properly exposed

Check that spirometry values are numeric and within realistic ranges

Confirm that all three models (vgg16_cnn.h5, pca.pkl, fusion_dnn.h5) exist in the models/ directory

Backend Issues

Verify Python version: python --version

Reinstall dependencies:

pip install --upgrade pip
pip install -r requirements.txt


Ensure port 5000 is free or update the port in app.py

IoT / Spirometer Issues

Check COM port / serial settings in the firmware and Python script

Ensure sensor wiring matches comments in firmware.ino

Calibrate the sensor in still air and test using sample breathing patterns

🤝 Contributors

Akash S – IoT Engineer & AI Model Integration

Thiyaanes V – Deep Learning Research & Model Training,IoT Engineer
Contributing

Contributions are welcome! 🎉
You can:

Open an issue for bugs or feature requests

Submit a pull request with improvements

Suggest datasets / clinical feedback for better validation

License

This project can be released under MIT License (or any license you choose).
Update this section according to your preferred license.

Acknowledgments

Inspired by the need for fast, accessible respiratory diagnosis

Based on concepts from:

Medical imaging research

Spirometry-based pulmonary diagnostics
📬 Contact

For queries or collaboration:
📧 andrewakash07@gmail.com

Thanks to mentors, faculty, and medical professionals who provided feedback.
