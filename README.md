````markdown
# AI-Assisted Liver Ultrasound Classification of Hepatocellular Carcinoma and Hemangioma

This project compares deep learning models for AI-assisted liver ultrasound classification of **hepatocellular carcinoma (HCC)** and **hemangioma** using the publicly available **SMC-LUD Liver Ultrasound Dataset**.

The goal is to evaluate whether deep learning can support ultrasound-based triage of focal liver lesions by helping distinguish malignant HCC from benign hemangioma.

## Project Title

**Comparison of Deep Learning Models for AI-Assisted Liver Ultrasound Classification of Hepatocellular Carcinoma and Hemangioma**

## Clinical Background

Hepatocellular carcinoma is a malignant liver tumor and a major cause of cancer-related mortality. Hemangioma is usually benign, but both HCC and hemangioma can appear as focal liver lesions on ultrasound.

In settings where specialist radiology access is limited, an AI-assisted triage model may help prioritize suspicious liver lesions for further specialist review. The purpose of this project is not to replace clinicians, but to explore whether deep learning models can support early triage and decision-making.

## Dataset

This project uses the **SMC-LUD Liver Ultrasound Dataset**, a publicly available dataset of anonymized two-dimensional B-mode liver ultrasound images.

Dataset classes:

- **HCC**
- **Hemangioma**

Dataset split used:

| Split | HCC | Hemangioma | Total |
|---|---:|---:|---:|
| Train | 1,901 | 1,868 | 3,769 |
| Validation | 543 | 533 | 1,076 |
| Test | 272 | 268 | 540 |
| **Total** | **2,716** | **2,669** | **5,385** |

## Models Compared

Three deep learning models were evaluated:

1. **EfficientNetB0**
2. **MobileNetV2**
3. **ViT-Tiny**

The models were trained using the training set, monitored on the validation set, and evaluated on the held-out test set.

## Methods Summary

Images were resized to **224 × 224 pixels** before model training.

The following evaluation metrics were used:

- Accuracy
- Area under the receiver operating characteristic curve (AUC)
- Precision
- Sensitivity/Recall
- F1-score
- Confusion matrix

Because this is a triage-focused task, **HCC sensitivity** was prioritized, as missing a malignant lesion is more clinically concerning than falsely flagging a benign lesion for further review.

## Results

| Model | Accuracy | AUC | HCC Precision | HCC Sensitivity/Recall | HCC F1-score |
|---|---:|---:|---:|---:|---:|
| EfficientNetB0 | 0.924 | 0.994 | 0.874 | 0.993 | 0.929 |
| MobileNetV2 | 0.946 | 0.992 | 0.952 | 0.941 | 0.946 |
| ViT-Tiny | **0.996** | **1.000** | **1.000** | **0.993** | **0.996** |

## Best Model

The best-performing model was **ViT-Tiny**.

ViT-Tiny achieved:

- **99.6% test accuracy**
- **AUC of 0.999986**
- **99.3% HCC sensitivity**
- **100.0% HCC precision**
- **99.6% HCC F1-score**

ViT-Tiny correctly classified **270 of 272 HCC images** and **268 of 268 hemangioma images** on the held-out test set.

Confusion matrix for ViT-Tiny:

|  | Predicted HCC | Predicted Hemangioma |
|---|---:|---:|
| True HCC | 270 | 2 |
| True Hemangioma | 0 | 268 |

## Error Analysis

The ViT-Tiny model missed two HCC images. One was a low-confidence error, while the other was a higher-confidence false negative. This supports the need for clinician oversight and external validation before clinical deployment.

## Saved Outputs

The following model and result files were generated:

```text
best_effnetb0_smc_lud.keras
best_mobilenetv2_smc_lud.keras
best_vit_tiny_smc_lud.pth

smc_lud_test_metrics.csv
mobilenetv2_smc_lud_test_metrics.csv
vit_tiny_smc_lud_test_metrics.csv

smc_lud_confusion_matrix.png
mobilenetv2_smc_lud_confusion_matrix.png
vit_tiny_smc_lud_confusion_matrix.png

smc_lud_roc_curve.png
mobilenetv2_smc_lud_roc_curve.png
vit_tiny_smc_lud_roc_curve.png
````

## Clinical Significance

This study suggests that deep learning models, especially ViT-Tiny, may support ultrasound-based triage of focal liver lesions by helping distinguish malignant HCC from benign hemangioma.

In resource-limited settings, such a tool could potentially help prioritize suspected HCC cases for specialist review. However, this model should not be used as a standalone diagnostic tool.

## Limitations

This project has important limitations:

* The dataset is from Samsung Medical Center and is not an African or Nigerian dataset.
* The study used internal validation only.
* External validation on independent datasets is still required.
* Patient-level validation was not performed.
* The very high ViT-Tiny performance should be interpreted carefully because public dataset splits may not fully represent real-world clinical variation.
* Clinical deployment would require prospective validation, local calibration, and regulatory review.

## Conclusion

ViT-Tiny achieved the best overall performance for liver ultrasound classification of HCC and hemangioma using the SMC-LUD dataset. The findings support the feasibility of AI-assisted ultrasound triage for focal liver lesions, but external validation using African patient datasets is required before clinical implementation.

## Disclaimer

This project is for research and educational purposes only. It is not intended for clinical diagnosis or patient management.

```

Your ViT-Tiny output confirms GPU training on a Tesla T4, a 3,769/1,076/540 train-validation-test split, and final test accuracy of 0.9963 with AUC 1.0000. :contentReference[oaicite:0]{index=0}
```
Author: Jonathan Wisdom, Niger Delta University
