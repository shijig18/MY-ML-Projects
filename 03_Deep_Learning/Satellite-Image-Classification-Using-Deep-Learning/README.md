# Satellite Image Classification Using Deep Learning

#Project Overview

This project explores the use of Deep Learning and Transfer Learning for
classifying satellite/remote-sensing images into multiple categories.

The objective of the project is to compare different pretrained Convolutional
Neural Network (CNN) architectures and evaluate their ability to classify
satellite imagery.

Four pretrained deep learning architectures were implemented and compared:

- VGG16
- VGG19
- InceptionV3
- Xception

The models were enhanced with Multi-Head Attention and custom classification
layers to improve feature learning and classification performance.

---

##  Objective

The main objectives of this project are:

- Perform exploratory analysis on satellite image data
- Examine class distribution
- Handle class imbalance
- Prepare image data for deep learning
- Apply Transfer Learning using pretrained CNN architectures
- Incorporate Multi-Head Attention
- Train and evaluate multiple deep learning models
- Compare model performance using Precision, Recall and F1-score
- Identify the best performing model

---

##  Dataset

The dataset contains satellite/remote-sensing images with corresponding
class labels.

The original labels were read from annotation files containing:

- Class label
- Bounding box center coordinates
- Width
- Height

For this classification task, only the image path and class label were used.

The project contains **14 image classes**.

### Class Balancing

Exploratory analysis showed differences in the number of images across
classes.

To address class imbalance, **Random Oversampling** was applied using
`RandomOverSampler`.

After oversampling, each of the 14 classes contained:

125 images per class

This resulted in a balanced dataset of approximately 1,750 image samples.

---

##  Data Preparation

The balanced dataset was divided into:

- 80% Training Data
- 10% Validation Data
- 10% Testing Data

Resulting dataset sizes:

| Dataset | Images |
|---------|-------:|
| Training | 1,400 |
| Validation | 175 |
| Testing | 175 |

Images were resized to:

224 × 224 × 3

Batch size:

16

Keras `ImageDataGenerator` was used to prepare the images for model training.

---

##  Deep Learning Models

Transfer Learning was used with pretrained ImageNet weights.

The convolutional base layers of the pretrained networks were frozen during
training.

The following architectures were evaluated:

### 1. VGG16

VGG16 was used as the pretrained feature extractor.

Additional layers included:

- Multi-Head Attention
- Gaussian Noise
- Global Average Pooling
- Dense Layer
- Batch Normalization
- Dropout
- Softmax Classification Layer

### 2. VGG19

The same custom classification architecture was applied using VGG19 as the
pretrained backbone.

### 3. InceptionV3

InceptionV3 was evaluated to explore a deeper architecture capable of learning
multi-scale visual features.

Multi-Head Attention was added to the extracted feature representation.

### 4. Xception

Xception was used as another transfer-learning architecture and combined with
Multi-Head Attention and custom classification layers.

---

##  Model Configuration

The models were compiled using:

Optimizer: Adam

Learning Rate: 0.0001

Loss Function: Sparse Categorical Crossentropy

Training was performed for a maximum of:

20 epochs

Early Stopping was implemented with:

Patience = 5

The best model weights were restored based on validation loss.

GPU acceleration was used during model training.

---

##  Model Evaluation

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Classification Report
- Confusion Matrix

Performance was also compared using a combined average score calculated from:

- Average Precision
- Average Recall
- Average F1-score

---

##  Model Performance

| Model | Accuracy | Avg Precision | Avg Recall | Avg F1 | Combined Score |
|------|---------:|--------------:|-----------:|-------:|---------------:|
| VGG16 | 81% | 0.8189 | 0.8031 | 0.7971 | 0.8064 |
| VGG19 | 47% | 0.4824 | 0.4744 | 0.4293 | 0.4620 |
| InceptionV3 | 67% | 0.8017 | 0.6731 | 0.6557 | 0.7102 |
| **Xception** | **81%** | **0.8316** | **0.8104** | **0.8076** | **0.8165** |

---

##  Best Performing Model

### Xception

Xception achieved the highest overall combined score:

**0.8165**

with approximately:

- Accuracy: **81%**
- Average Precision: **83.16%**
- Average Recall: **81.04%**
- Average F1-score: **80.76%**

Although VGG16 achieved a similar overall accuracy, Xception produced stronger
average Precision, Recall and F1 performance across the 14 classes.

Therefore, **Xception was selected as the best-performing model in this
experiment.**

---

##  Technologies Used

- Python
- TensorFlow
- Keras
- Scikit-learn
- Imbalanced-learn
- Pandas
- NumPy
- Matplotlib
- Seaborn
- PIL
- Google Colab
- GPU Computing

---

##  Key Concepts Demonstrated

This project demonstrates practical implementation of:

- Image Classification
- Deep Learning
- Convolutional Neural Networks
- Transfer Learning
- Pretrained ImageNet Models
- Multi-Head Attention
- Class Imbalance Handling
- Random Oversampling
- Image Preprocessing
- Regularization
- Batch Normalization
- Dropout
- Early Stopping
- Model Evaluation
- Model Comparison

---

##  Project Structure

Satellite-Image-Classification-Using-Deep-Learning/

├── satellite_image_classification_using_deep_learning.ipynb
└── README.md

---

##  Future Improvements

Possible improvements to this project include:

- Fine-tuning selected layers of the pretrained models
- Experimenting with additional data augmentation
- Hyperparameter tuning
- Testing additional transfer-learning architectures
- Mapping numeric class IDs to descriptive land-use/category names
- Deploying the best model as a web application
- Testing the model on additional unseen satellite images

---

##  Author

**Shiji Govindan**

AI & Machine Learning Enthusiast  
Exploring Machine Learning, Deep Learning, Generative AI, RAG and Agentic AI
through hands-on projects.
