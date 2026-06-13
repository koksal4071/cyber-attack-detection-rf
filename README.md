# 🛡️ Cyber Attack Detection using Network Traffic (Intrusion Detection System)

This project is an end-to-end Machine Learning pipeline that analyzes Network Traffic data to distinguish between normal connections and cyber attacks (DDoS, BruteForce, PortScan).

## 📌 Project Overview
Manually detecting threats in cybersecurity data is nearly impossible. In this project, an Artificial Intelligence model was developed to monitor real-time data streams from a network and detect cyber attacks within milliseconds.

* **Dataset:** Kaggle (Cyber Attack Detection using Network Traffic) - 100,000 Rows
* **Algorithm:** Random Forest Classifier
* **Technologies Used:** Python, Pandas, Scikit-learn, Seaborn, Matplotlib

##  Project Pipeline
1. **Exploratory Data Analysis (EDA):** Analyzed the distribution of classes (Normal, DDoS, PortScan, BruteForce) and the underlying structure of network features.
2. **Data Preprocessing:** * Digitized the target variable using `LabelEncoding`.
   * Converted protocol types (TCP, UDP) into a machine-readable format via `One-Hot Encoding`.
   * Normalized variables with vastly different scales (such as duration and bytes) using `StandardScaler`.
3. **Model Training:** Trained the model using the Random Forest algorithm and evaluated its performance through classification metrics and a Confusion Matrix.

##  Model Performance & Feature Importance
The model achieved near-perfect accuracy on the test set. By analyzing the model's logic, the top 3 critical network features it relied on to predict an "attack" were identified as:
1. **`src_bytes` (~29%):** Data volume from the source (Critical for detecting DDoS).
2. **`failed_logins` (~24%):** Number of failed login attempts (Critical for detecting BruteForce).
3. **`packet_count` (~19%):** Total number of transmitted packets (Critical for detecting PortScan).

## Live Simulation Application
The trained model and scaler were exported in `.pkl` format. A live simulation script was built to instantly analyze newly inputted network traffic parameters (duration, bytes, protocols, etc.) and trigger either a **SAFE** or **CYBER ATTACK** alert. Details and test scenarios can be found in the final section of the source code.
