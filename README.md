# FAV-ASTCL: Real-Time Urban Traffic Prediction Framework

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-ee4c2c.svg)](https://pytorch.org/)
[![Flask](https://img.shields.io/badge/Flask-2.3+-black.svg)](https://flask.palletsprojects.com/)

**FAV-ASTCL** (*Forecasting-Aware Versatile Adaptive Spatio-Temporal Context Learning*) is an advanced Spatio-Temporal Graph Neural Network (ST-GNN) architecture designed for multi-horizon traffic speed forecasting in high-volatility urban environments.

---

## Key Highlights & Performance

* **Cross-Domain Adaptability:** Trained on the **METR-LA** benchmark dataset (207 sensors in Los Angeles) and evaluated across **five major traffic hubs in Hyderabad, India**.
* **Dynamic Spatial Modeling:** Replaces static road-distance matrices with a **Learnable Context Selector** using dynamic similarity search to model evolving spatial relationships.
* **Exogenous Fusion:** Integrates 6 external features (live weather, precipitation, time-of-day encodings) via exogenous gating mechanisms to handle non-recurrent congestion.
* **State-of-the-Art Accuracy:** Achieves an overall prediction accuracy of **91.78%**—a **15+ percentage point improvement** over the baseline ASTCL model.

### Metric Overview

| Metric | Overall Value | Performance Impact |
| :--- | :---: | :--- |
| **MAE** | **3.633 km/h** | Significant error reduction in dense urban traffic |
| **RMSE** | **8.842** | Robust against sudden variance and traffic spikes |
| **MAPE** | **8.22%** | High precision across both peak and off-peak hours |
| **Accuracy**| **91.78%** | +15% performance boost over ASTCL baseline |

---

## System Architecture & Pipeline

1. **Input Layer:** 60-minute historical window (12 time steps at 5-min intervals) combined with 6 exogenous context features.
2. **Spatio-Temporal Core:** Dynamic graph neural network with GRU-based temporal processing to capture sequential dependencies.
3. **Multi-Horizon Forecasting:** Generates real-time speed predictions for **5, 10, and 15-minute** future intervals.
4. **Production API & Dashboard:** Lightweight Flask REST API (`server.py`) serving live predictions to a browser dashboard using real-time data from the **TomTom Traffic API** and **WeatherAPI**.

---

## Tech Stack

* **Core Engine:** Python, PyTorch, Spatio-Temporal Graph Neural Networks (ST-GNNs), NumPy, Pandas
* **Backend & API:** Flask, Flask-CORS, Requests
* **External APIs:** TomTom Traffic API, WeatherAPI
* **Evaluation & Benchmarks:** Scikit-Learn, METR-LA Dataset

---

## Project Structure

```text
├── models/               # PyTorch FAV-ASTCL architecture and ST-GNN modules
├── api/                  # Flask REST API server and route handlers
├── data/                 # Data preprocessing & feature engineering scripts
├── docs/                 # Project documentation and complete research paper PDF
├── requirements.txt      # Python dependencies
└── README.md             # Project overview
