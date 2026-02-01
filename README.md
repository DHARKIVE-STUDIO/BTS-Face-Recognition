# 🛡️ BTS-Face-Recognition: One-Shot Learning Analysis
**Implementing Siamese Neural Networks for Low-Data Face Recognition**

## 📌 Project Overview
This repository explores the implementation of **Siamese Neural Networks (SNN)** to solve the challenge of face recognition in "low-data" environments. Unlike traditional CNNs that require thousands of images per class, this project utilizes **One-Shot Learning** to identify individuals (specifically members of the global phenomenon BTS) by learning a similarity function rather than a direct classification.

This project was developed as part of a formal research study at **VIT Bangalore**, focusing on the trade-offs between model depth, computational performance, and accuracy in face validation tasks.

---

## 🔬 The Siamese Architecture
The core of this project is a Siamese Network consisting of two identical sister L1-Distanced subsystems. Instead of classifying an image, the network learns to calculate the "distance" between two feature vectors (embeddings).

* **Feature Extraction:** Utilizes shared weights across twin Convolutional Neural Networks to ensure consistent embedding logic.
* **Architecture Specifics:** Each twin network consists of four convolutional layers (64 to 128 filters), Max Pooling, and a final 4096-node Dense layer.
* **Distance Layer:** Implements an L1 distance function to measure the absolute difference between the twin feature vectors.
* **Final Prediction:** A Sigmoid activation function outputs a similarity score between 0 and 1.



---

## 🧪 Technical Methodology

### 1. One-Shot Learning Strategy
The model is designed to recognize a face from a single exemplary image. This is achieved by:
* **Pairwise Training:** The dataset is structured into "Positive Pairs" (two images of the same person) and "Negative Pairs" (two images of different people).
* **Binary Cross-Entropy Loss:** The network is optimized to minimize the error in predicting whether two images are a "match" (1) or "not a match" (0).

### 2. The Data Pipeline
* **Preprocessing:** Images are resized to 100x100 pixels and normalized.
* **Real-time Face Detection:** Integrated with OpenCV for live frame capturing and facial bounding boxes.
* **Face Verification:** The model compares an "Input Image" against a "Validation Image" folder to verify identity based on a learned distance threshold.



---

## 📊 Performance Analysis & Diagnostic Insights
A key part of this research was documenting the challenges of training high-precision models on specific facial features.

* **Metric Evaluation:** The model was tested against 50 validation samples per category. 
* **The "Low Performance" Aspect:** The report identifies that while the model learns general features effectively, **Precision** and **Recall** were affected by:
    * **Intra-class Variance:** Close similarities in facial structure among group members.
    * **Orientation Sensitivity:** Performance drops when faces are not centered, highlighting the need for a Spatial Transformer Network (STN).
* **Learning Insight:** The analysis demonstrates how L1-Distance based similarity requires significant data augmentation to become invariant to lighting and background noise.

---

## 🛠 Tech Stack
* **Deep Learning:** TensorFlow / Keras
* **Computer Vision:** OpenCV (Live Tracking)
* **Languages:** Python (NumPy, Pandas, Matplotlib)
* **Environment:** Google Colab / Jupyter

---

## 🚀 Future Research Directions
To improve upon the current "Low Performance" baseline, the following enhancements are proposed:
* **Triplet Loss Implementation:** Moving from pair-based learning to anchor-positive-negative triplets to create better clusters in the embedding space.
* **Transfer Learning:** Utilizing the **VGG-Face** or **FaceNet** pre-trained weights to initialize the twin CNNs.
* **Attention Mechanisms:** Incorporating spatial attention to focus the network on key identity-defining landmarks (eyes, nose, mouth).

---
Developed by **DHARKIVE-STUDIO**
