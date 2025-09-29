
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

[1]	Tong Yang, Jie Jiang, Peng Liu, Qun Huang, Junzhi Gong, Yang Zhou, Rui Miao, Xiaoming Li, and Steve Uhlig. 2018. Elastic sketch: adaptive and fast network-wide measurements. In Proceedings of the 2018 Conference of the ACM Special Interest Group on Data Communication (SIGCOMM '18). Association for Computing Machinery, New York, NY, USA, 561–575. https://doi.org/10.1145/3230543.3230544

[2]	Lu Cao, Qilong Shi, Yuxi Liu, Hanyue Zheng, Yao Xin, Wenjun Li, Tong Yang, Yangyang Wang, Yang Xu, Weizhe Zhang, and Mingwei Xu. 2024. Bubble Sketch: A High-performance and Memory-efficient Sketch for Finding Top-k Items in Data Streams. In Proceedings of the 33rd ACM International Conference on Information and Knowledge Management (CIKM '24). Association for Computing Machinery, New York, NY, USA, 3653–3657. https://doi.org/10.1145/3627673.3679882

[3]	Weihe Li and Paul Patras. 2024. Stable-Sketch: A Versatile Sketch for Accurate, Fast, Web-Scale Data Stream Processing. In Proceedings of the ACM Web Conference 2024 (WWW '24). Association for Computing Machinery, New York, NY, USA, 4227–4238. https://doi.org/10.1145/3589334.3645581

[4]	H. Wang, H. Lin, Z. Zhong, T. Yang and M. Shahzad, "Enhanced Machine Learning Sketches for Network Measurements," in IEEE Transactions on Computers, vol. 72, no. 4, pp. 957-970, 1 April 2023, doi: 10.1109/TC.2022.3185560.


---



