## Automatic Licence Plate Recognition (ALPR) Parking Management System

<h3><strong>Description</strong></h3>
Led the design and implementation of an Automatic Number Plate Recognition (ANPR) system, utilizing deep learning algorithms for accurate license plate identification. Employed TensorFlow for model training and optimization, leveraging supervised learning techniques with a dataset sourced from Kaggle. Utilized OpenCV for image preprocessing and feature extraction, enhancing model performance. Applied Optical Character Recognition (OCR) techniques and advanced image processing methodologies to extract license plate characters in real-time, ensuring precise and reliable identification. Additionally, implemented model evaluation and validation techniques to assess the performance of the ANPR system, including cross-validation and metrics such as accuracy and F1 score.

<h3><strong>Key Concepts</strong></h3>

Data Handling and Pre-processing<br>
> - <strong>Data Cleaning</strong>: Utilized OpenCV for image preprocessing to address noise and artifacts, ensuring clean input data.
> - <strong>Feature Engineering</strong>: Extracted significant features from raw images to enhance model performance.
> - <strong>Data Visualization</strong>: Employed Matplotlib to visualize data distribution and preprocessing effects.

Machine Learning Algorithms<br>
> - <strong>Supervised Learning</strong>:  Implemented supervised learning techniques using a dataset sourced from Kaggle, focusing on accurate license plate identification.

Deep Learning<br>
> - <strong>Neural Networks</strong>: Designed and implemented deep learning models for license plate recognition.
> - <strong>Frameworks</strong>: Used TensorFlow and Keras for model training and optimization.
> - <strong>Model Training and Tuning</strong>: Applied advanced training techniques and hyperparameter tuning to optimize performance.

Model Evaluation and Validation<br>
> - <strong>Metrics</strong>: Evaluated model performance using accuracy and F1 score.
> - <strong>Cross-Validation</strong>: Employed cross-validation techniques to ensure robustness and reliability.

<h3><strong>Technologies (Tools and Libraries)</strong></h3>
- <strong>Python</strong>: Programming language used for the entire project. <br>
- <strong>Keras</strong>: Version 2.3.1 for building and training the neural network models. <br>
- <strong>TensorFlow</strong>: Version 1.14.0 for model training and optimization. <br>
- <strong>Numpy</strong>: Version 1.17.4 for numerical operations. <br>
- <strong>Matplotlib</strong>: Version 3.2.1 for data visualization. <br>
- <strong>OpenCV</strong>: Version 4.1.0 for image preprocessing and feature extraction. <br>
- <strong>Scikit-learn</strong>: Version 0.21.3 for various machine learning tasks. <br>

<h3><strong>Project Breakdown</strong></h3>

Part 1: Detection License Plate with Wpod-Net<br>
> - Utilized Wpod-Net for detecting license plates in images.

Part 2: Plate Character Segmentation with OpenCV<br>
> - Applied OpenCV techniques for segmenting characters from the detected license plates.

Part 3: Recognize Plate License Characters with OpenCV and Deep Learning
> - Used OCR and deep learning models to recognize and extract characters from the segmented license plates. 

<h3><strong>Getting Started</strong></h3>
<ol>
<li>Clone the Repository</li>
<li>Install Dependencies: Use the provided requirements file or manually install the required libraries.</li>
<li>Dataset: Download the dataset from Kaggle and place it in the designated directory.</li>
<li>Run the Preprocessing Script: Preprocess the images using OpenCV.</li>
<li>Train the Model: Use the training scripts to train the ANPR model.</li>
<li>Evaluate the Model: Run the evaluation scripts to assess the model</li> performance using cross-validation and metrics like accuracy and F1 score.
</ol>

<h3><strong>Maintainers and Contributors</h3></strong>
<strong>Maintainer</strong>: David Ogalo <br>
<strong>Contributors</strong>: Contributions are welcome. Please reach out for more information on contribution guidelines on this project.
