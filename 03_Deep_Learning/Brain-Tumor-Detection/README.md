
# Brain Tumor Classification Using Deep Learning

## Project Overview

This project focuses on classifying brain MRI images into four categories using
Deep Learning and Transfer Learning.

The objective is to compare multiple pretrained Convolutional Neural Network
(CNN) architectures and identify the most effective model for brain tumor image
classification.

The following pretrained models were evaluated:

- VGG16
- VGG19
- MobileNet
- Xception
- InceptionV3

The models were enhanced with additional deep learning techniques including:

- Multi-Head Attention
- Gaussian Noise Regularization
- Batch Normalization
- Dropout
- Transfer Learning

These techniques were used to improve feature extraction, reduce overfitting,
and improve overall model robustness.



## Objective

The main objective of this project is to classify brain MRI scans into four
categories:

- Glioma
- Meningioma
- Pituitary Tumor
- No Tumor

The project also aims to:

- Perform exploratory analysis on MRI image data
- Analyze class distribution
- Handle class imbalance
- Apply transfer learning
- Compare multiple pretrained CNN architectures
- Evaluate models using multiple classification metrics
- Select the best-performing architecture

---

## Dataset

The dataset contains brain MRI images organized into separate training and test
folders.

The four image classes are:

- `glioma`
- `meningioma`
- `pituitary`
- `notumor`

The training dataset contained a total of:

**23,131 MRI images**

### Original Class Distribution

| Class | Number of Images |
|------|-----------------:|
| No Tumor | 6,380 |
| Pituitary | 5,891 |
| Meningioma | 5,556 |
| Glioma | 5,304 |

The dataset showed a moderate class imbalance.

---

## Handling Class Imbalance

To create a more balanced training dataset, Random Oversampling was applied.

`RandomOverSampler` from the `imbalanced-learn` library was used to increase
minority-class samples.

This helped ensure that the models were trained on a more balanced
representation of all four tumor classes.

---

## Image Preparation

The image paths and labels were extracted from the training directories and
stored in a Pandas DataFrame.

The categorical labels were encoded using:

`LabelEncoder`

Images were resized to:

**224 × 224 × 3**

Keras `ImageDataGenerator` was used to prepare the images for model training,
validation, and testing.

---

## Transfer Learning Approach

Transfer Learning was used to take advantage of pretrained ImageNet models.

For each architecture:

1. A pretrained CNN was loaded without its original classification head.
2. The pretrained convolutional layers were frozen.
3. Additional custom layers were added.
4. The model was trained for the four-class brain tumor classification task.

---

## Model Architecture Enhancements

The pretrained CNN backbones were combined with additional layers including:

### Multi-Head Attention

Multi-Head Attention was applied to extracted CNN feature maps to help the
model focus on important spatial features.

### Gaussian Noise

Gaussian Noise layers were introduced as a regularization technique to improve
model robustness.

### Global Average Pooling

Global Average Pooling was used to reduce feature-map dimensions before the
classification layers.

### Dense Layer

A fully connected Dense layer with ReLU activation was added for feature
learning.

### Batch Normalization

Batch Normalization was used to stabilize training.

### Dropout

Dropout was added to reduce overfitting.

### Output Layer

A Softmax output layer with four neurons was used for multiclass
classification.

---

##  Models Evaluated

### 1. VGG16

VGG16 was used as a pretrained ImageNet feature extractor and enhanced with
attention and custom classification layers.

### 2. VGG19

VGG19 was evaluated using a similar transfer-learning architecture.

### 3. MobileNet

MobileNet was tested as a lightweight CNN architecture suitable for efficient
image classification.

### 4. Xception

Xception uses depthwise separable convolutions and was evaluated with the same
attention-based classification approach.

### 5. InceptionV3

InceptionV3 was used to explore multi-scale feature extraction for MRI image
classification.

---

## Model Training

The models were compiled using:

- **Optimizer:** Adam
- **Learning Rate:** 0.0001
- **Loss Function:** Sparse Categorical Crossentropy
- **Metric:** Accuracy

Training was performed for a maximum of:

**20 epochs**

Early Stopping was used to stop training when validation performance stopped
improving.

---

## Evaluation Metrics

Each model was evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Classification Report
- Confusion Matrix

These metrics were used to compare overall performance across all four MRI
classes.

---

## Model Performance

| Model | Accuracy | Precision | Recall | F1 Score |
|------|---------:|----------:|-------:|---------:|
| VGG16 | 94.87% | 94.97% | 94.87% | 94.82% |
| VGG19 | 71.79% | 82.20% | 71.79% | 71.15% |
| **MobileNet** | **96.98%** | **97.01%** | **96.98%** | **96.99%** |
| Xception | 89.19% | 89.57% | 89.19% | 89.02% |
| InceptionV3 | 85.97% | 87.07% | 85.97% | 85.70% |

---

## Best Performing Model

### MobileNet

MobileNet achieved the best overall performance in this experiment.

Its results were approximately:

- **Accuracy:** 96.98%
- **Precision:** 97.01%
- **Recall:** 96.98%
- **F1 Score:** 96.99%

MobileNet outperformed the other tested architectures and provided the most
balanced classification performance across the four brain MRI classes.

---

## Model Comparison

The experiment demonstrated that larger or deeper architectures do not always
guarantee better results.

For this dataset:

- MobileNet produced the strongest overall performance.
- VGG16 also performed very strongly.
- Xception achieved good but lower overall results.
- InceptionV3 showed moderate performance.
- VGG19 produced the weakest results among the evaluated models.

This highlights the importance of comparing multiple architectures rather than
selecting a model based only on network complexity.

---

## Technologies Used

- Python
- TensorFlow
- Keras
- Scikit-learn
- Imbalanced-learn
- Pandas
- NumPy
- OpenCV
- Matplotlib
- Seaborn
- Kaggle
- GPU Computing

---

## Concepts Demonstrated

This project demonstrates practical implementation of:

- Deep Learning
- Image Classification
- Convolutional Neural Networks
- Transfer Learning
- Pretrained ImageNet Models
- Multi-Head Attention
- Class Imbalance Handling
- Random Oversampling
- Image Preprocessing
- Label Encoding
- Gaussian Noise Regularization
- Batch Normalization
- Dropout
- Early Stopping
- Confusion Matrix
- Precision
- Recall
- F1 Score
- Model Comparison

---
## Project Structure

```text
Brain-Tumor-Detection/
│
├── brain-tumor-detection.ipynb
└── README.md

 Disclaimer
This project was developed for educational and machine learning experimentation
purposes.
It is not intended for clinical diagnosis or medical decision-making.
Author
Shiji Govindan
AI & Machine Learning Enthusiast
Building hands-on projects across Machine Learning, Deep Learning,
Generative AI, RAG, and Agentic AI.
