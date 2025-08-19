# Automatic License Plate Recognition (ALPR) Parking Management System

## Overview

This project presents a high-accuracy (98%) Automatic License Plate Recognition (ALPR) system designed for smart parking management. Led by the developer, the system leverages deep learning and computer vision techniques to enable real-time license plate identification from video streams. Utilizing TensorFlow for model training, OpenCV for image preprocessing, and Tesseract OCR for character recognition, the implementation achieves low-latency inference across multiple concurrent streams. The system integrates fault tolerance, performance monitoring, and configurable alerting, making it ideal for automated access control in parking facilities. Model robustness is enhanced through supervised learning, data augmentation, and hyperparameter tuning, with performance validated using cross-validation and metrics like accuracy and F1 score.

## System Architecture

For a detailed exploration of the system’s architecture, including design rationale, data flow, component interactions, extensibility, reliability, security, performance considerations, deployment guidelines, and use cases, refer to the [System Design Document](system_design.md). This document provides a comprehensive blueprint, complemented by a visual diagram, to understand the system’s modular structure and operational flow.

## Key Features

- **Real-Time Recognition**: Processes multiple video streams with low-latency inference.
- **High Accuracy**: Achieves 98% accuracy through optimized deep learning models.
- **Fault Tolerance**: Implements retry logic and monitoring for reliable operation.
- **Scalable Design**: Handles concurrent streams with efficient resource utilization.
- **Performance Monitoring**: Tracks accuracy, latency, and triggers alerts for anomalies.

## Technical Components

### Data Handling and Preprocessing

- **Data Cleaning**: Employs OpenCV (v4.1.0) to remove noise and artifacts, ensuring high-quality input data.
- **Feature Engineering**: Extracts key visual features (e.g., edges, contours) to boost model performance.
- **Data Augmentation**: Applies rotations, noise, and scaling using TensorFlow to enhance training dataset diversity and reduce overfitting.
- **Visualization**: Uses Matplotlib (v3.2.1) to analyze data distribution and preprocessing outcomes.

### Machine Learning and Deep Learning

- **Supervised Learning**: Trains models on a manually curated dataset of license plates, focusing on precise character recognition.
- **Neural Networks**: Implements a CNN-based architecture with YOLO for object detection, optimized via TensorFlow (v1.14.0) and Keras (v2.3.1).
- **Model Training and Tuning**: Utilizes grid search for hyperparameter optimization, improving model generalization and reducing latency.

### Model Evaluation and Validation

- **Metrics**: Assesses performance with accuracy and F1 score, achieving 98% accuracy.
- **Cross-Validation**: Applies k-fold cross-validation to ensure robustness across diverse plate formats and conditions.

## Technologies and Libraries

- **Python**: Core programming language (v3.8+ recommended).
- **TensorFlow**: v1.14.0 for deep learning model training and optimization.
- **Keras**: v2.3.1 for building and fine-tuning neural networks.
- **NumPy**: v1.17.4 for numerical computations.
- **Matplotlib**: v3.2.1 for data visualization.
- **OpenCV**: v4.1.0 for image preprocessing and feature extraction.
- **Scikit-learn**: v0.21.3 for machine learning utilities and validation.

## Project Breakdown

1. **License Plate Detection with Wpod-Net**
   - Utilizes Wpod-Net to locate license plates in video frames with high precision.

2. **Plate Character Segmentation with OpenCV**
   - Applies OpenCV techniques to segment individual characters from detected plates, enhancing OCR readiness.

3. **Character Recognition with Deep Learning and OCR**
   - Combines a CNN model (TensorFlow) with Tesseract OCR to extract and recognize characters in real-time.

## Getting Started

### Installation and Setup

1. **Clone the Repository**

   ```bash
   git clone https://github.com/DavidOgalo/Automatic-License-Plate-Recognition-System.git
   cd Automatic-License-Plate-Recognition-System
   ```

2. **Install Dependencies**

   ```bash
   pip install -r requirements.txt
   ```

   Alternatively, use the provided `requirements.txt` or manually install listed libraries.

3. **Prepare Dataset**

   - Collect a sample dataset of license plates specific to your country’s format.
   - Place images in a designated directory (e.g., `data/plates/`).

4. **Run Preprocessing Script**

   Preprocesses images using OpenCV for noise reduction and feature extraction.

5. **Train the Model**

   Trains the CNN model with augmentation and hyperparameter tuning.

6. **Evaluate the Model**

   Assesses model performance with cross-validation, reporting accuracy and F1 score.

7. **Run Real-Time Inference**

   Processes live video streams for plate recognition.

## Contributing

1. Fork the repository.
2. Create a feature branch: `git checkout -b feature/new-feature`.
3. Commit changes: `git commit -m 'Add new feature'`.
4. Push to the branch: `git push origin feature/new-feature`.
5. Open a Pull Request with detailed descriptions and tests.

## References

- [System Design Document](./system_design.md)
- [Error Guide Document](./error_guide.md)
- [OpenCV Documentation](https://docs.opencv.org/)
- [TensorFlow Documentation](https://www.tensorflow.org/)

## License

MIT License - see the [LICENSE](../LICENSE) file for details.
