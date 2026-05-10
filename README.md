# AI-Assisted Liver Ultrasound Classification of Hepatocellular Carcinoma and Hemangioma

This project compares deep learning models for classifying liver ultrasound images as either hepatocellular carcinoma (HCC) or hemangioma using the publicly available SMC-LUD Liver Ultrasound Dataset.

## Overview

Hepatocellular carcinoma is a malignant liver tumor, while hemangioma is usually benign. Both can appear as focal liver lesions on ultrasound. In settings where access to specialist radiology review is limited, artificial intelligence may help support triage by identifying lesions that require urgent expert evaluation.

This project evaluates whether deep learning models can distinguish HCC from hemangioma on two-dimensional B-mode liver ultrasound images.

## Dataset

The dataset used in this project is the SMC-LUD Liver Ultrasound Dataset.

The dataset contains two classes:

- Hepatocellular carcinoma
- Hemangioma

Dataset split:

| Split | HCC | Hemangioma | Total |
|---|---:|---:|---:|
| Train | 1,901 | 1,868 | 3,769 |
| Validation | 543 | 533 | 1,076 |
| Test | 272 | 268 | 540 |
| Total | 2,716 | 2,669 | 5,385 |

## Models

Three deep learning models were trained and evaluated:

- EfficientNetB0
- MobileNetV2
- ViT-Tiny

The models were trained on the training set, monitored on the validation set, and evaluated on the held-out test set.

## Methods

All images were resized to 224 × 224 pixels.

The following metrics were used to evaluate model performance:

- Accuracy
- Area under the receiver operating characteristic curve
- Precision
- Sensitivity/recall
- F1-score
- Confusion matrix

Because the study is clinically framed as a triage task, HCC sensitivity was considered especially important. In suspected cancer triage, missing HCC is more clinically concerning than falsely flagging a benign lesion for further review.

## Results

| Model | Accuracy | AUC | HCC Precision | HCC Sensitivity | HCC F1-score |
|---|---:|---:|---:|---:|---:|
| EfficientNetB0 | 0.924 | 0.994 | 0.874 | 0.993 | 0.929 |
| MobileNetV2 | 0.946 | 0.992 | 0.952 | 0.941 | 0.946 |
| ViT-Tiny | 0.996 | 1.000 | 1.000 | 0.993 | 0.996 |

ViT-Tiny achieved the best overall test performance.

## Best Model: ViT-Tiny

ViT-Tiny achieved:

- Test accuracy: 99.6%
- AUC: 1.000
- HCC precision: 100.0%
- HCC sensitivity: 99.3%
- HCC F1-score: 99.6%

ViT-Tiny correctly classified 270 of 272 HCC images and 268 of 268 hemangioma images.

Confusion matrix:

|  | Predicted HCC | Predicted Hemangioma |
|---|---:|---:|
| True HCC | 270 | 2 |
| True Hemangioma | 0 | 268 |

## Error Analysis

ViT-Tiny misclassified two HCC images as hemangioma. One missed HCC case was a low-confidence error, while the other was a higher-confidence false negative. This highlights the importance of clinician oversight and further external validation before clinical use.

## Clinical Significance

This project suggests that deep learning models may support ultrasound-based triage of focal liver lesions by helping distinguish malignant HCC from benign hemangioma.

In resource-limited settings, an AI-assisted triage model could help prioritize suspicious liver lesions for specialist review. However, the model is not intended to replace radiologists or clinicians.

## Limitations

This study has several limitations:

- The dataset is from Samsung Medical Center and is not an African or Nigerian dataset.
- The study used internal validation only.
- External validation on independent datasets is required.
- Patient-level validation was not performed.
- The high performance of ViT-Tiny should be interpreted carefully.
- Prospective clinical validation is required before real-world deployment.

## Conclusion

ViT-Tiny showed the best performance for classifying HCC and hemangioma on liver ultrasound images using the SMC-LUD dataset. The findings support the feasibility of AI-assisted ultrasound triage for focal liver lesions, but external validation using African patient datasets is required before clinical implementation.

## Disclaimer

This project is for research and educational purposes only. It is not intended for clinical diagnosis, treatment decisions, or patient management.


## Citation

If you use this repository, please cite:

Wisdom, J., & Dabrilagha, F. (2026). *AI-assisted liver ultrasound classification of hepatocellular carcinoma and hemangioma* (v1.0.0). Zenodo. https://doi.org/10.5281/zenodo.20105001 

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20105001.svg)](https://doi.org/10.5281/zenodo.20105001)
