<div align="center">

   🫁 **AI + IoT Lung Disease Screening System**

### *A 1-minute hybrid diagnostic system combining Deep Learning + IoT Spirometry for COVID-19, COPD & Pneumonia.*

</div>

---

## 🚀 Project Overview

This project presents a **portable, fast, and highly accurate multimodal lung disease screening system**.  
It combines:

- 📸 **CNN-based Chest X-ray analysis**
- 🔌 **IoT Spirometer sensor readings** (FVC, FEV1, PEFR)
- 🧠 **Deep Neural Network (Fusion Model)**
- 🌐 **Cloud Dashboard** for doctors

Ideal for **rural healthcare, emergency diagnostics, and rapid screenings**.

---
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
---

# ⭐ Key Features

### 📸 CNN-based X-ray Analysis  
- Fine-tuned **VGG16** model  
- Extracts high-level deep features  

### 🔌 IoT Spirometer Integration  
Measures lung parameters:  
- **FVC**, **FEV1**, **PEFR**  

### 🔗 Fusion-based AI Model  
- PCA for dimensionality reduction  
- DNN fusion for improved accuracy  

### ⚕️ Explainable AI  
- **Grad-CAM heatmaps** highlight abnormal lung areas  

### 🌐 Cloud Dashboard  
- Upload X-rays  
- Enter spirometry values  
- View prediction + confidence + heatmap  

---

🧠 System Architecture (Perfect ASCII Diagram)

```''`text
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
                           Doctor Dashboard````'`

📊 Model Performance
Component	Accuracy
X-ray CNN Model	92–95%
Fusion Model (AI+IoT)	94%+
Spirometry Classifier	90%+


🧪 IoT Spirometer Workflow

User blows into airflow sensor

Microcontroller measures airflow + pressure

Calculates FVC, FEV1, PEFR

Sends readings to server

AI model fuses the values with image features

Final prediction generated

▶️ How to Run
1⃣ Clone the repo
git clone https://github.com/yourusername/lung-disease-screening.git
cd lung-disease-screening

2⃣ Install dependencies
pip install -r requirements.txt

3⃣ Start the server
python app.py

4⃣ Upload X-ray + enter spirometry values

→ Get prediction + heatmap instantly.

🤝 Contributors

Akash S – IoT Engineer & AI Model Integration

Thiyaanes V – Deep Learning Research & Model Training
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

Thanks to mentors, faculty, and medical professionals who provided feedback.

📬 Contact

For queries or collaboration:
📧 andrewakash07@gmail.com
