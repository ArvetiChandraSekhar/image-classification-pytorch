# CIFAR-10 Classification: Comparative Study of Logistic Regression, FCNN, CNN, and ResNet

## Overview

This repository presents a comprehensive study of image classification on the CIFAR-10 dataset using four different machine learning architectures:

* Logistic Regression
* Fully Connected Neural Network (FCNN)
* Convolutional Neural Network (CNN)
* ResNet

The objective of this project is to evaluate how model architecture, data augmentation, and regularization strategies affect classification performance, generalization, and training stability.

Three experimental configurations were evaluated:

1. **Without Data Augmentation and Regularization**
2. **With Common Data Augmentation and Regularization**
3. **With Model-Specific Data Augmentation and Regularization**

---

## Dataset

### CIFAR-10

CIFAR-10 is a benchmark image classification dataset containing:

* 60,000 color images
* 10 classes
* Image size: 32×32 pixels
* 50,000 training images
* 10,000 test images

Classes:

* Airplane
* Automobile
* Bird
* Cat
* Deer
* Dog
* Frog
* Horse
* Ship
* Truck

---

## Models Evaluated

| Model               | Trainable Parameters |
| ------------------- | -------------------: |
| Logistic Regression |               30,730 |
| FCNN                |            1,578,506 |
| CNN                 |              553,514 |
| ResNet              |               73,674 |

---

## Experimental Results

### Best Test Accuracy (%)

| Model               | No Augmentation | Common Augmentation | Model-Specific Augmentation |
| ------------------- | --------------: | ------------------: | --------------------------: |
| Logistic Regression |           39.32 |               22.55 |                       32.64 |
| FCNN                |           40.65 |               34.07 |                       48.64 |
| CNN                 |           63.44 |               55.72 |                       66.41 |
| ResNet              |           74.49 |               72.27 |                   **78.84** |

---

## Key Findings

### 1. Architecture Matters More Than Parameter Count

A larger model does not necessarily achieve better performance.

* FCNN contains over **1.5 million parameters**, the largest model in this study.
* Despite its size, it consistently underperforms CNN and ResNet.
* ResNet achieves the highest accuracy while using only **73,674 parameters**.

This demonstrates that architectural design is more important than parameter count for image classification tasks.

---

### 2. Logistic Regression Serves as a Baseline

Performance remained limited across all configurations.

| Configuration               | Test Accuracy (%) |
| --------------------------- | ----------------: |
| No Augmentation             |             39.32 |
| Common Augmentation         |             22.55 |
| Model-Specific Augmentation |             32.64 |

Observations:

* Strong underfitting behavior
* Unable to learn complex visual features
* Generic augmentation reduces performance
* Useful as a baseline but unsuitable for CIFAR-10

---

### 3. FCNN Benefits from Tailored Augmentation

| Configuration               | Test Accuracy (%) |
| --------------------------- | ----------------: |
| No Augmentation             |             40.65 |
| Common Augmentation         |             34.07 |
| Model-Specific Augmentation |             48.64 |

Observations:

* Common augmentation degrades performance
* Model-specific augmentation significantly improves results
* Flattening images removes spatial information, limiting overall performance

---

### 4. CNN Learns Spatial Features Effectively

| Configuration               | Test Accuracy (%) |
| --------------------------- | ----------------: |
| No Augmentation             |             63.44 |
| Common Augmentation         |             55.72 |
| Model-Specific Augmentation |             66.41 |

Observations:

* Consistently outperforms Logistic Regression and FCNN
* Learns hierarchical visual features
* Benefits significantly from image-specific augmentations

---

### 5. ResNet Delivers the Best Performance

| Configuration               | Test Accuracy (%) |
| --------------------------- | ----------------: |
| No Augmentation             |             74.49 |
| Common Augmentation         |             72.27 |
| Model-Specific Augmentation |         **78.84** |

Advantages:

* Residual connections mitigate vanishing gradients
* Stable training dynamics
* Excellent parameter efficiency
* Best generalization performance

Improvement achieved using model-specific augmentation:

* +4.35% over no augmentation
* +6.57% over common augmentation

---

## Impact of Data Augmentation

### No Augmentation

Pros:

* Simpler training pipeline
* Faster convergence

Cons:

* Limited data diversity
* Higher risk of overfitting
* Lower generalization capability

---

### Common Augmentation

Pros:

* Increased data diversity
* Improved robustness

Cons:

* Benefits are inconsistent
* Can negatively affect simpler architectures

---

### Model-Specific Augmentation

Pros:

* Tailored to each architecture
* Consistently improves generalization
* Produces the best results for deep learning models

Performance improvement over common augmentation:

| Model               | Improvement (%) |
| ------------------- | --------------: |
| Logistic Regression |          +10.09 |
| FCNN                |          +14.57 |
| CNN                 |          +10.69 |
| ResNet              |           +6.57 |

---

## Overall Ranking

| Rank | Model                                             | Best Test Accuracy (%) |
| ---- | ------------------------------------------------- | ---------------------: |
| 🥇 1 | ResNet + Model-Specific Augmentation              |                  78.84 |
| 🥈 2 | ResNet (No Augmentation)                          |                  74.49 |
| 🥉 3 | ResNet + Common Augmentation                      |                  72.27 |
| 4    | CNN + Model-Specific Augmentation                 |                  66.41 |
| 5    | CNN (No Augmentation)                             |                  63.44 |
| 6    | CNN + Common Augmentation                         |                  55.72 |
| 7    | FCNN + Model-Specific Augmentation                |                  48.64 |
| 8    | FCNN (No Augmentation)                            |                  40.65 |
| 9    | Logistic Regression (No Augmentation)             |                  39.32 |
| 10   | FCNN + Common Augmentation                        |                  34.07 |
| 11   | Logistic Regression + Model-Specific Augmentation |                  32.64 |
| 12   | Logistic Regression + Common Augmentation         |                  22.55 |

---

## Final Conclusion

This study demonstrates that:

* Model architecture is the primary driver of performance.
* Data augmentation is effective only when aligned with the model's characteristics.
* Generic augmentation does not universally improve accuracy.
* Model-specific augmentation consistently enhances generalization and performance.
* ResNet achieves the best balance between accuracy, stability, and parameter efficiency.

### Best Overall Result

**ResNet + Model-Specific Augmentation**

* Test Accuracy: **78.84%**
* Parameters: **73,674**

This combination provides the most effective solution for CIFAR-10 image classification among all models evaluated in this project.

---

## Future Work

Potential improvements include:

* ResNet-34 / ResNet-50 architectures
* MixUp and CutMix augmentation
* Learning rate schedulers
* Transfer learning
* Vision Transformers (ViT)
* EfficientNet and ConvNeXt comparisons

---

## License

This project is provided for educational and research purposes.
