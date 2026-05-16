# IoT Healthcare Security Intrusion Detection System

![Domain](https://img.shields.io/badge/Domain-IoT%20Security-red)
![ML](https://img.shields.io/badge/ML-Ensemble%20Learning-blue)
![XAI](https://img.shields.io/badge/Explainability-SHAP-green)
![Framework](https://img.shields.io/badge/Framework-Scikit--learn-orange)

## 📌 Overview

IoT devices in healthcare environments ICU monitors, patient tracking systems, MQTT-based sensors are increasingly vulnerable to cyber attacks. This project builds a **robust intrusion detection system (IDS)** for IoT healthcare networks using ensemble machine learning with SHAP-based explainability.

The system classifies network traffic as **normal or attack** using three ML models combined via a **soft voting ensemble**, with full transparency through SHAP feature importance analysis.

---

## 🎯 Problem Statement

- Healthcare IoT devices generate sensitive patient data transmitted over TCP/MQTT protocols
- Cyberattacks on medical IoT can have life-threatening consequences
- Black-box ML models are unacceptable in healthcare explainability is critical
- Goal: Build an accurate, transparent, and robust IDS for IoT healthcare networks

---

## 📊 Dataset

- **Source:** IoT Flock Tool real IoT network traffic simulation
- **Size:** 136,665 network traffic records
- **Features:** 52 TCP/MQTT network features (frame timing, packet size, flags, MQTT metadata)
- **Task:** Binary classification Attack (True) vs Normal (False)
- **Preprocessing:** Removed irrelevant columns, balanced class distribution, feature engineering

### Key Features Used
```
tcp.time_delta · mqtt.msgtype · mqtt.hdrflags · 
frame.time_delta · tcp.flags.push · mqtt.qos · tcp.flags.ack
```

---

## 🔬 Methodology

### Models Used
| Model | Purpose |
|---|---|
| K-Nearest Neighbors (KNN) | Non-parametric baseline |
| Logistic Regression (LR) | Linear interpretable model |
| Random Forest (RF) | Non-linear ensemble, feature importance |
| **Voting Classifier (Ensemble)** | **Final model soft voting combination** |

### Pipeline
1. **Data Loading** Merged Attack + Normal + Patient Monitoring datasets
2. **Preprocessing** Null removal, class balancing, feature selection
3. **Feature Engineering** Correlation analysis, Random Forest importance ranking
4. **Hyperparameter Tuning** GridSearchCV for optimal parameters
5. **Ensemble Learning** Soft voting across KNN, LR, RF
6. **Explainability** SHAP values for feature importance transparency
7. **Validation** Cross-validation, Confusion Matrix, ROC-AUC

### Regularization Techniques
- Gaussian noise injection on training features
- Cross-validation (3-fold) to prevent overfitting
- Class balancing to prevent majority-class bias

---

## 🔍 Explainability SHAP

SHAP (SHapley Additive Explanations) was used to provide transparency into model decisions:

- **Global feature importance** which features most influence attack detection
- **Per-prediction explanations** why a specific traffic sample was flagged
- Critical for **healthcare deployment** where model decisions must be auditable

Top SHAP features:
```
tcp.time_delta     → 0.38 (highest importance)
mqtt.msgtype       → 0.20
mqtt.hdrflags      → 0.16
frame.time_delta   → 0.15
tcp.flags.push     → 0.07
```

---

## 🛠️ Tech Stack

- **Language:** Python
- **ML Framework:** Scikit-learn
- **Explainability:** SHAP
- **Data Processing:** Pandas, NumPy
- **Visualization:** Matplotlib, Seaborn
- **Validation:** GridSearchCV, Cross-validation, ROC-AUC

---

## 📁 Repository Structure

```
├── IOT_Healthcare.ipynb    # Complete pipeline notebook
├── README.md               # Documentation
└── LICENSE                 # MIT License
```

---

## 🚀 How to Run

1. Open `IOT_Healthcare.ipynb` in Google Colab
2. Upload dataset to Google Drive
3. Update dataset paths in Cell 2
4. Run all cells sequentially

---

## 🔮 Future Work

- Deploy as real-time network monitoring API (FastAPI)
- Extend to multi-class attack classification
- Integrate with live IoT network traffic via packet capture
- Test on public IoT datasets (UNSW-NB15, TON_IoT)

---

## 👤 Author

**Hamza Maqsood**
BS Artificial Intelligence University of Management and Technology, Lahore
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin)](https://linkedin.com/in/hamza-maqsood1)
[![GitHub](https://img.shields.io/badge/GitHub-Profile-black?logo=github)](https://github.com/Hamza-Maqsood1)
