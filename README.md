
# Enhanced ML-Based Network Traffic Analysis

This project explores the integration of traditional sketch data structures and machine learning techniques to improve the accuracy of flow size estimation and top-k flow detection in high-speed network environments.

---

## Project Overview

Network traffic measurement is essential for Quality of Service (QoS), security, and bandwidth management. Traditional sketch-based methods (like CU Sketch) are efficient but suffer from over-estimation due to hash collisions and limited adaptability.

In this project, we propose a hybrid approach combining **CU Sketch** with **ML models** to predict:
- **Flow Size** (regression)
- **Top-k Flows** (classification)

---

## Key Features

- Modified CU Sketch: Each bucket split into two parts for better resolution of mice vs elephant flows.
- Feature Engineering: Includes log-transformed counters, ratios, and statistical metrics.
- GPU-accelerated ML Training:
  - Flow Size → Gradient Boosting Regression (5 models based on hash groupings)
  - Top-k Flow Detection → Gradient Boosting Binary Classifier
- No Heap: Top-k detection without Min-Heap, reducing runtime memory overhead.

---

## How It Works

### 1. Flow Size Estimation
- Split sketch counters into two fields (value + hashed minimum).
- Divide flows into 5 groups via hash and train 5 separate regressors.

### 2. Top-k Flow Detection
- Use CU Sketch counters as features.
- Train a binary classifier with class imbalance handled.
- Predict if a flow is in Top-k without using Min-Heap.

---

## Reference Datasets

- CAIDA 2016 Anonymized Internet Traces  
  https://www.caida.org/data/passive/passive_2016_dataset.xml

---

## Related Works

- Elastic Sketch (SIGCOMM 2018)
- Bubble Sketch (CIKM 2024)
- Stable Sketch (WWW 2024)
- Enhanced ML Sketches (IEEE TC 2023)

---

## Authors
National Cheng Kung University
-  簡維頡  
-  黃聖民  

