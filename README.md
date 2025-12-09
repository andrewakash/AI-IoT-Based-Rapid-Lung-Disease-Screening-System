<!-- PROJECT LOGO -->
<div align="center">
  <img src="https://i.imgur.com/5yqaj5m.png" width="240px" />
  <h2><strong>AI + IoT Lung Disease Screening System</strong></h2>
  <p><em>A 1-minute hybrid diagnostic system combining Deep Learning + IoT Spirometry for COVID-19, COPD & Pneumonia.</em></p>
</div>

---

<!-- WORKFLOW ANIMATION -->
<div align="center">
  <img src="https://i.imgur.com/4Zy5BJk.gif" width="850px" />
</div>

---





A 1-minute hybrid diagnostic system combining Deep Learning + IoT Spirometry for COVID-19, COPD & Pneumonia.
🚀 Project Overview

This project presents a portable, fast, and highly accurate lung disease screening system that uses a multimodal AI model.
It combines:

📸 Chest X-ray image analysis (CNN)

🔌 IoT Spirometer sensor readings (FVC, FEV1, PEFR)

🧠 Deep Neural Network fusion model

🌐 Cloud dashboard for doctors

The system is designed to deliver diagnosis under 1 minute, ideal for rural healthcare, emergencies, and rapid screening scenarios.

🛠️ Tech Stack
🧑‍💻 Programming Languages
Python • JavaScript • C • Java

🤖 Machine Learning & AI
TensorFlow • Keras • Scikit-Learn • Pandas • NumPy • OpenCV

🔌 IoT & Hardware
Arduino • Airflow Sensor • Microcontroller • Serial Communication

🌐 Web & Backend
Flask • HTML • CSS • JavaScript • REST API

⭐ Key Features
📸 CNN-Based X-ray Analysis

Uses a fine-tuned VGG16 model

Extracts high-level lung features

🔌 IoT Spirometer Integration

Measures:

FVC

FEV1

PEFR

🔗 Data Fusion (AI + IoT)

PCA for dimensionality reduction

Fusion DNN for accurate prediction

⚕️ Explainable AI (XAI)

Grad-CAM heatmaps highlight infected lung regions

🌐 Cloud-Based Doctor Dashboard

Upload X-rays

Enter spirometry values

View predictions + heatmaps

🧠 System Architecture
               +-------------------------+
               |  Chest X-Ray Image      |
               +-----------+-------------+
                           |
                        CNN (VGG16)
                           |
                     Image Features
                           |
+------------------+   PCA   +------------------------+
| Spirometry Input | ------->|   Fusion DNN Model     |
| FVC, FEV1, PEFR  |         +-----------+------------+
+------------------+                     |
                                 Prediction Output
                                 (COVID/COPD/Pneumonia/Normal)
                                         |
                                    Grad-CAM Heatmap
                                         |
                                   Doctor Dashboard

📊 Model Performance
Component	Accuracy
X-ray CNN Model	92–95%
Fusion Model (AI+IoT)	94%+
Spirometry Classifier	90%+
🧪 How the IoT Spirometer Works

User blows into airflow sensor

Microcontroller calculates flow rate

Computes FVC, FEV1, PEFR

Sends values via serial or wireless

AI model uses it for multimodal prediction


▶️ How to Run
1⃣ Clone the repo
git clone https://github.com/yourusername/lung-disease-screening.git
cd lung-disease-screening

2⃣ Install dependencies
pip install -r requirements.txt

3⃣ Start the Flask server
python app.py

4⃣ Upload X-ray + Enter Sensor Values

Get instant disease prediction.


